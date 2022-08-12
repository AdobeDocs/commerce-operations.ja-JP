---
title: 最終検証
description: Vanrish の設定が、Adobe Commerceアプリケーションで動作するように正しく設定されていることを確認します。
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---


# ワニス構成の最終検証

これで、 `default.vcl` コマースで生成された Vanrish を確実に機能させるために、最終的な検証を行うことができます。

## HTTP 応答ヘッダーの検証

用途 `curl` Web ブラウザーで任意のコマースページにアクセスしたときに HTTP 応答ヘッダーを表示する別のユーティリティ。

まず、 [開発者モード](../cli/set-mode.md#change-to-developer-mode);そうしないと、ヘッダーは表示されません。

以下に例を挙げます。

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

重要なヘッダー：

```terminal
X-Magento-Cache-Control: max-age=86400, public, s-maxage=86400
Age: 0
X-Magento-Cache-Debug: MISS
```

>[!INFO]
>
>この値も使用できます。 `X-Magento-Cache-Debug: HIT`.

## ページ読み込み時間の確認

Vanish が機能している場合、キャッシュ可能なブロックを含む Commerce ページは 150 ms 未満で読み込まれます。 そのようなページの例として、正面ドアや [店頭](https://glossary.magento.com/storefront) [カテゴリ](https://glossary.magento.com/category) ページ。

ブラウザーインスペクターを使用して、ページ読み込み時間を測定します。

例えば、Chrome インスペクターを使用するには、次のようにします。

1. Chrome でキャッシュ可能な Commerce ページにアクセスします。
1. ページ上の任意の場所を右クリックします。
1. ポップアップメニューで、 **[!UICONTROL Inspect Element]**
1. インスペクタウィンドウで、 **[!UICONTROL Network]** タブをクリックします。
1. ページを更新します。
1. 表示中のページの URL が表示されるように、インスペクターペインの上部にスクロールします。

   次の図は、 `magento2` インデックスページ。

   ![表示しているページをクリックします](../../assets/configuration/varnish-inspector.png)

   ページの読み込み時間は、ページ URL の横に表示されます。 この場合、読み込み時間は 5 ms です。 これは、Vanish がページをキャッシュしたことを確認するのに役立ちます。

1. HTTP 応答ヘッダーを表示するには、ページ URL（名前列内）をクリックします。

   HTTP ヘッダーを表示できます。詳しくは、 HTTP 応答ヘッダーの検証の節で説明しています。

## コマースキャッシュを確認します

次を確認します。 `<magento_root>/var/page_cache` ディレクトリが空です：

1. Commerce サーバーにログインするか、 [ファイルシステム所有者](https://glossary.magento.com/magento-file-system-owner).
1. 次のコマンドを入力します。

   ```bash
   rm -rf <magento_root>/var/page_cache/*
   ```

1. 1 つ以上のキャッシュ可能なコマースページにアクセスします。
1. 次を確認します。 `var/page_cache/` ディレクトリ。

   ディレクトリが空の場合は、おめでとうございます。 Vanish と Commerce が連携するように設定されました。

1. もし `var/page_cache/` ディレクトリ、Vanish を再起動します。

>[!TIP]
>
>503（バックエンドの取得に失敗）エラーが発生した場合は、 [503（サービスを利用できない）エラーのトラブルシューティング](https://support.magento.com/hc/en-us/articles/360034631211) 内 _Adobe Commerce Help Center_.