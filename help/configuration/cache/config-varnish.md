---
title: Vanish の設定と使用
description: Vanish がファイルを保存し、HTTP トラフィックを改善する方法を理解します。
feature: Configuration, Cache
exl-id: 57614878-e349-43bb-b22b-1aa321907be1
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 0%

---

# ワニスを設定

[ワニスキャッシュ] は、オープンソース Web アプリケーションアクセラレーター ( _HTTP アクセラレーター_ または _HTTP リバースプロキシのキャッシュ_) をクリックします。 Vanish は、ファイルまたはファイルの断片をメモリに保存（またはキャッシュ）し、Vanish は、今後の同等の要求に対する応答時間とネットワーク帯域幅の消費を削減できます。 Apache や nginx などの Web サーバーとは異なり、Vanrish は HTTP プロトコルでのみ使用するように設計されています。

Commerce 2.4.2 は Vanrish 6.4 でテストされています。Commerce 2.4.x は Vanrish 6.x と互換性があります。

>[!WARNING]
>
>水 _強く勧める_ 制作時にはワニスを使用します。 組み込みのフルページ・キャッシュ：ファイル・システムまたは [データベース] — は Vanrish よりもはるかに遅く、Vanrish は HTTP トラフィックを高速化するように設計されています。

Vanish の詳細については、次を参照してください。

- [ザビッグワニスの絵]
- [ワニス起動オプション]
- [ニスとウェブサイトのパフォーマンス]

## ワニストポロジ図

次の図は、コマーストポロジの Vanish の基本的なビューを示しています。

![基本ワニス図](../../assets/configuration/varnish-basic.png)

上の図では、ユーザーのインターネット経由での HTTP リクエストによって、CSS、HTML、JavaScript、画像 ( 総称して _アセット_) をクリックします。 Wanis は、Web サーバーの前に配置され、これらの要求を Web サーバーにプロキシします。

Web サーバーがアセットを返すと、キャッシュ可能なアセットは Varnish に保存されます。 これらのアセットに対する以降の要求は、Vanish で処理されます（つまり、要求は Web サーバーに到達しません）。 Vanrish はキャッシュされたコンテンツを非常に迅速に返します。 結果は、応答時間が短くなり、コンテンツがユーザーに返されるのに要する時間が短くなり、コマースで満たす必要のある要求の数が少なくなります。

Vanish でキャッシュされたアセットは、設定可能な間隔で有効期限が切れるか、同じアセットの新しいバージョンに置き換えられます。 キャッシュは、管理者または [`magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types) コマンドを使用します。

## プロセスの概要

このトピックでは、最小限のパラメータセットで Vanrish を最初にインストールし、動作するテストを行う方法について説明します。 次に、コマース管理から Vanish 設定を書き出し、再度テストします。

このプロセスは、次のように要約できます。

1. Vanish をインストールし、任意のコマースページにアクセスしてテストし、Vanrish が機能していることを示す HTTP 応答ヘッダーが表示されているかどうかを確認します。
1. Commerce ソフトウェアをインストールし、管理者を使用して Vanish 設定ファイルを作成します。
1. 既存の Vanrish 設定ファイルを、管理者が生成したファイルに置き換えます。
1. すべてを再度テストします。

   もしあなたの `<magento_root>/var/page_cache` ディレクトリ、Commerce で Vanish を正常に設定しました！

>[!NOTE]
- 特に記載のない限り、このトピックで説明するすべてのコマンドは、を使用するユーザーとして入力する必要があります。 `root` 権限。
- このトピックは、CentOS と Apache 2.4 で Vanish 用に記述されています。Vanish を別の環境で設定する場合は、一部のコマンドが異なる場合があります。 詳細は、Vanish のドキュメントを参照してください。


## 既知の問題

Vanish に関する次の問題がわかっています。

- [Vanish は SSL をサポートしていません]

   別の方法として、SSL 終了または SSL 終了プロキシを使用します。

- 手動で `<magento_root>/var/cache` ディレクトリに入る場合は、Vanish を再起動する必要があります。

- コマースのインストール中にエラーが発生した可能性があります：

   ```terminal
   Error 503 Service Unavailable
   Service Unavailable
   XID: 303394517
   Varnish cache server
   ```

   このエラーが発生した場合は、 `default.vcl` タイムアウトを `backend` stanza は次のようになります。

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "8080";
       .first_byte_timeout = 600s;
   }
   ```

## Vanish キャッシュの概要

Vanish キャッシュは、次を使用して Commerce で機能します。

- [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) Magento2 GitHub リポジトリから
- `.htaccess` Commerce で提供される Apache 用の分散設定ファイル
- `default.vcl` 次を使用して生成される Vanrish の設定 [管理者](../cache/configure-varnish-commerce.md)

>[!INFO]
このトピックでは、前の一覧の既定のオプションのみを扱います。 複雑なシナリオでキャッシュを設定する方法は他にも多数あります（例えば、コンテンツ配信ネットワークを使用）。これらの方法は、このガイドの範囲外です。

最初のブラウザー要求時に、キャッシュ可能なアセットが Varnish からクライアントブラウザーに配信され、ブラウザーにキャッシュされます。

また、Vanish は静的アセットにエンティティタグ (ETag) を使用します。 ETag は、サーバ上で静的ファイルが変更されるタイミングを判断する手段を提供します。 その結果、静的アセットは、サーバー上で変更がおこなわれるとき（ブラウザーからの新しいリクエスト時またはクライアントがブラウザーキャッシュを更新したとき）に、クライアントに送信されます。通常は、F5 キーまたは Ctrl + F5 キーを押します。

詳しくは、以降の節で説明します。

## ブラウザーリクエストによるキャッシュ

このセクションでは、ブラウザーインスペクターを使用して、最初のリクエストでアセットがブラウザーに配信され、その後ローカルブラウザーキャッシュから読み込まれる方法を示します。

### 最初のブラウザーリクエスト

`nginx.conf.sample` および `.htaccess` クライアントキャッシュのオプションを提供します。 最初の要求がブラウザからキャッシュ可能なオブジェクトに対して行われると、Vanish はそのオブジェクトをクライアントに配信します。

次の図は、ブラウザインスペクターを使用する例を示しています。

![キャッシュ可能なオブジェクトに対して初めて要求を行う場合、Vanrish はそれをブラウザーに配信します](../../assets/configuration/varnish-apache-first-visit.png)

前述の例は、ストアフロントのメインページ (`m2_ce_my`) をクリックします。 CSS および JavaScript アセットは、クライアントブラウザーでキャッシュされます。

>[!NOTE]
ほとんどの静的アセットには、アセットがサーバーから取得されたことを示す HTTP 200(OK) ステータスコードが含まれています。

### 2 番目のブラウザーリクエスト

同じブラウザーが同じページを再度リクエストした場合、これらのアセットはローカルブラウザーのキャッシュから配信されます。次の図を参照してください。

![次回同じオブジェクトがリクエストされたときに、アセットがローカルブラウザーのキャッシュから読み込まれます](../../assets/configuration/varnish-apache-second-visit.png)

最初のリクエストと 2 番目のリクエストの応答時間の違いに注意してください。 静的アセットには 200(OK) の応答コードがあります。静的アセットは、初めてローカルキャッシュから配信されるからです。

## Commerce での Etag の使用方法

次の例は、特定の静的アセットの応答ヘッダーを示しています。

![ETag を使用すると、静的アセットが変更されたかどうかを簡単に判断できます](../../assets/configuration/varnish-etag.png)

`calendar.css` には ETag 応答ヘッダーがあり、これは、クライアントブラウザー上の CSS ファイルをサーバー上の CSS ファイルと比較できることを意味します。

さらに、静的アセットは、次の図に示すように、304（未変更）HTTP ステータスコードで返されます。

![HTTP 304（未変更）応答コードは、ローカルキャッシュ内の静的アセットがサーバー上と同じであることを示します](../../assets/configuration/varnish-304.png)

304 ステータスコードが発生するのは、ユーザーがローカルキャッシュを無効にし、サーバー上のコンテンツが変更されなかったためです。 ステータスコード 304 により、静的アセット _コンテンツ_ は転送されません。ブラウザーには、HTTP ヘッダーのみがダウンロードされます。

コンテンツがサーバー上で変更された場合、クライアントは HTTP 200(OK) ステータスコードと新しい ETag を使用して静的アセットをダウンロードします。

<!-- Link Definitions -->

[データベース]: https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/
[ザビッグワニスの絵]: https://www.varnish-cache.org/docs/trunk/users-guide/intro.html
[ワニスキャッシュ]: https://varnish-cache.org
[ワニス起動オプション]: https://www.varnish-cache.org/docs/trunk/reference/varnishd.html#ref-varnishd-options
[ニスとウェブサイトのパフォーマンス]: https://www.varnish-cache.org/docs/trunk/users-guide/performance.html#users-performance
[Vanish は SSL をサポートしていません]: https://www.varnish-cache.org/docs/3.0/phk/ssl.html
