---
title: ワニスの設定と使用
description: Varnish がファイルを保存し、HTTP トラフィックを改善する方法を理解します。
feature: Configuration, Cache
exl-id: 57614878-e349-43bb-b22b-1aa321907be1
source-git-commit: ec3ab7e3c6c3835e73653b0d4f74aadc861016d3
workflow-type: tm+mt
source-wordcount: '1049'
ht-degree: 0%

---

# ワニスを設定する

[Varnish Cache] は、オープンソースの web アプリケーションアクセラレーター（_HTTP アクセラレーター_ または _キャッシュ HTTP リバースプロキシ_ とも呼ばれます）です。 Varnish は、メモリ内のファイルまたはファイルのフラグメントを保存（またはキャッシュ）します。これにより、Varnish は、将来の同等のリクエストに対する応答時間とネットワーク帯域幅の消費を削減できます。 Apache や nginx などの web サーバーとは異なり、Varnish は HTTP プロトコルでのみ使用するように設計されています。

[ 必要システム構成 ](../../installation/system-requirements.md) に、Varnish のサポート対象バージョンを示します。

>[!WARNING]
>
>私たちは _強くお勧めします_ あなたは生産でワニスを使います。 組み込みのフルページキャッシュ（ファイルシステムまたは [ データベース ](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)）は、Varnish よりもはるかに遅く、Varnish は HTTP トラフィックを高速化するように設計されています。

Varnish の詳細については、次を参照してください。

- [ 大きなワニスの絵 ]
- [Varnish スタートアップ オプション ]
- [ ワニスとウェブサイトのパフォーマンス ]

## ワニスのトポロジ図

次の図は、Commerce トポロジでの Varnish の基本的なビューを示しています。

![ ワニスの基本図 ](../../assets/configuration/varnish-basic.png)

上の図では、インターネット経由でのユーザーの HTTP リクエストによって、CSS、HTML、JavaScriptおよび画像（総称して _assets_）に対する多数のリクエストが発生しています。 Varnish は web サーバーの前に配置され、これらのリクエストを web サーバーにプロキシします。

Web サーバーがアセットを返すと、キャッシュ可能なアセットは Varnish に保存されます。 これらのアセットに対する後続のリクエストは、Varnish によって処理されます（つまり、リクエストは web サーバーに到達しません）。 Varnish は、キャッシュされたコンテンツを非常に迅速に返します。 その結果、コンテンツをユーザーに返す応答時間が短縮され、Commerceで処理する必要があるリクエストの数が減少します。

Varnish によってキャッシュされたAssetsは、設定可能な間隔で期限切れになるか、同じアセットの新しいバージョンに置き換えられます。 また、Admin または [`magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types) コマンドを使用して、手動でキャッシュをクリアすることもできます。

## プロセスの概要

このトピックでは、最初に最小限のパラメータのセットでワニスをインストールし、それが機能することをテストする方法について説明します。 次に、Commerce Admin から Varnish 設定をエクスポートし、再度テストします。

プロセスの概要は次のとおりです。

1. Varnish をインストールし、Commerceページにアクセスしてテストし、Varnish が機能していることを示す HTTP 応答ヘッダーが取得されているかどうかを確認します。
1. Commerce ソフトウェアをインストールし、管理者を使用して Varnish 設定ファイルを作成します。
1. 既存の Varnish 設定ファイルを、管理者が生成した設定ファイルに置き換えます。
1. もう一度すべてをテストします。

   `<magento_root>/var/page_cache` ディレクトリに何もない場合は、Commerceで Varnish を正常に設定しました。

>[!NOTE]
>
>- 特に明記されている場合を除き、このトピックで説明されているすべてのコマンドを、`root` 権限を持つユーザーとして入力する必要があります。
>
>- このトピックは、CentOS および Apache 2.4 の Varnish 用に記述されています。別の環境で Varnish を設定している場合は、一部のコマンドが異なる場合があります。 詳しくは、Varnish のドキュメントを参照してください。

## 既知の問題

Varnish に関する次の問題を把握しています。

- [ ワニスは SSL をサポートしていません ]

  別の方法として、SSL ターミネーションまたは SSL ターミネーションプロキシを使用してください。

- `<magento_root>/var/cache` ディレクトリの内容を手動で削除する場合は、Varnish を再起動する必要があります。

- Commerceのインストール中にエラーが発生した可能性があります：

  ```terminal
  Error 503 Service Unavailable
  Service Unavailable
  XID: 303394517
  Varnish cache server
  ```

  このエラーが発生した場合は、`default.vcl` を編集して、`backend` のスタンザに次のようにタイムアウトを追加します。

  ```conf
  backend default {
      .host = "127.0.0.1";
      .port = "8080";
      .first_byte_timeout = 600s;
  }
  ```

## ワニスのキャッシュの概要

ワニスのキャッシュは、次を使用してCommerceで機能します。

- Magento 2 GitHub リポジトリから [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample)
- Commerce`.htaccess` 提供される Apache 用の分散設定ファイル
- [Admin](../cache/configure-varnish-commerce.md) を使用して生成された Varnish の `default.vcl` 設定

>[!INFO]
>
>ここでは、上記のリストのデフォルトオプションのみを取り上げます。 複雑なシナリオでキャッシュを設定する方法は他にも多数あります（コンテンツ配信ネットワークの使用など）。これらの方法については、このガイドの範囲外です。

最初のブラウザーリクエストで、キャッシュ可能なアセットが Varnish からクライアントブラウザーに配信され、ブラウザー上にキャッシュされます。

さらに、Varnish は静的アセットにエンティティタグ（ETag）を使用します。 ETag は、サーバー上で静的ファイルが変更された場合に判断する手段を提供します。 その結果、静的アセットは、サーバー上で変更が発生すると、クライアントに送信されます。ブラウザーからの新しいリクエストに対して、またはクライアントがブラウザーキャッシュを更新したときに（通常、F5 キーまたは Control + F5 キーを押して）。

詳細については、以降のセクションで説明します。

## ブラウザーリクエストによるキャッシュ

このセクションでは、ブラウザーインスペクターを使用して、最初のリクエストでアセットがブラウザーに配信され、その後ローカルブラウザーキャッシュから読み込まれる方法を表示します。

### 最初のブラウザーリクエスト

`nginx.conf.sample` および `.htaccess` は、クライアントキャッシュのオプションを提供します。 キャッシュ可能なオブジェクトに対してブラウザーから最初のリクエストが行われると、Varnish はそのリクエストをクライアントに配信します。

次の図は、ブラウザーインスペクターを使用した例を示しています。

![ キャッシュ可能なオブジェクトに対して初めてリクエストが行われると、Varnish はそのリクエストをブラウザーに配信します ](../../assets/configuration/varnish-apache-first-visit.png)

前述の例は、ストアフロントのメインページ（`m2_ce_my`）に対するリクエストを示しています。 CSS とJavaScriptのアセットは、クライアントブラウザーにキャッシュされます。

>[!NOTE]
>
>ほとんどの静的アセットには HTTP 200 （OK）ステータスコードが含まれており、アセットがサーバーから取得されたことを示します。

### 2 番目のブラウザーリクエスト

同じブラウザーが同じページを再度リクエストする場合、次の図に示すように、これらのアセットはローカルブラウザーのキャッシュから配信されます。

![ 次回、同じオブジェクトがリクエストされると、アセットはローカルブラウザーのキャッシュから読み込まれます ](../../assets/configuration/varnish-apache-second-visit.png)

1 番目のリクエストと 2 番目のリクエストの応答時間の違いに注意してください。 ここでも、静的アセットには 200 （OK）の応答コードが含まれています。これは、静的アセットが初めてローカルキャッシュから配信されるためです。

## Commerceでの Etag の使用方法

次の例は、特定の静的アセットの応答ヘッダーを示しています。

![ETag を使用すると、静的アセットが変更されたかどうかを簡単に判断できます ](../../assets/configuration/varnish-etag.png)

`calendar.css` には ETag 応答ヘッダーがあります。これは、クライアントブラウザー上の CSS ファイルをサーバー上の CSS ファイルと比較できることを意味します。

さらに、次の図に示すように、静的アセットは 304 （変更なし） HTTP ステータスコードで返されます。

![HTTP 304 （変更なし）応答コードは、ローカルキャッシュの静的アセットがサーバー上のものと同じであることを示します ](../../assets/configuration/varnish-304.png)

304 ステータスコードが発生するのは、ユーザーがローカルキャッシュを無効にし、サーバー上のコンテンツが変更されなかったためです。 ステータスコードが 304 なので、静的アセット _コンテンツ_ は転送されません。HTTP ヘッダーのみがブラウザーにダウンロードされます。

サーバー上でコンテンツが変更された場合、クライアントは HTTP 200 （OK）ステータスコードと新しい ETag を持つ静的アセットをダウンロードします。

<!-- Link Definitions -->

[大きなニスの絵]: https://www.varnish-cache.org/docs/trunk/users-guide/intro.html
[Varnish キャッシュ]: https://varnish-cache.org
[Varnish スタートアップ オプション]: https://www.varnish-cache.org/docs/trunk/reference/varnishd.html#ref-varnishd-options
[ワニスと Web サイトのパフォーマンス]: https://www.varnish-cache.org/docs/trunk/users-guide/performance.html#users-performance
[ワニスは SSL をサポートしていません]: https://www.varnish-cache.org/docs/3.0/phk/ssl.html
