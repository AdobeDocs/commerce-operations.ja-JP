---
title: 最終検証
description: Adobe Commerce アプリケーションで動作するように Varnish 設定が適切に設定されていることを確認します。
feature: Configuration, Cache
exl-id: 01f28c93-75cd-4969-9142-b8dac0aa2adb
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ワニスの形状の最終検証

Commerceで生成された `default.vcl` を使用しているので、最終的な検証を行って、Varnish が機能していることを確認できます。

## HTTP 応答ヘッダーの検証

Web ブラウザーでCommerce ページにアクセスした場合は、`curl` などのユーティリティを使用して HTTP レスポンスヘッダーを表示します。

最初に、[ 開発者モード ](../cli/set-mode.md#change-to-developer-mode) を使用していることを確認します。使用していない場合、ヘッダーは表示されません。

以下に例を挙げます。

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

重要なヘッダー：

```
X-Magento-Cache-Control: max-age=86400, public, s-maxage=86400
Age: 0
X-Magento-Cache-Debug: MISS
```

>[!INFO]
>
>この値も使用できます（`X-Magento-Cache-Debug: HIT`）。

## ページの読み込み時間を確認

ワニスが機能している場合、キャッシュ可能なブロックを持つCommerceページは 150 ms 未満で読み込まれます。 このようなページの例としては、前面のドアページとストアフロントのカテゴリページがあります。

ブラウザーインスペクターを使用すると、ページの読み込み時間を測定できます。

例えば、Chrome インスペクターを使用するには、次のようにします。

1. Chromeのキャッシュ可能なCommerceページにアクセスします。
1. ページ上の任意の場所を右クリックします。
1. ポップアップメニューから、「**[!UICONTROL Inspect Element]**」をクリックします
1. インスペクターパネルで、「**[!UICONTROL Network]**」タブをクリックします。
1. ページを更新します。
1. インスペクターパネルの上部までスクロールして、表示しているページの URL を確認します。

   次の図は、`magento2` インデックスページを読み込む例を示しています。

   ![ 表示しているページをクリックします ](../../assets/configuration/varnish-inspector.png)。

   ページの読み込み時間は、ページ URL の横に表示されます。 この場合、ロード時間は 5 ミリ秒です。 これは、Varnish がページをキャッシュしたことを確認するのに役立ちます。

1. HTTP 応答ヘッダーを表示するには、（名前列の）ページの URL をクリックします。

   HTTP ヘッダーを表示できます。詳しくは、HTTP 応答ヘッダーの検証の節で説明されています。

## Commerce キャッシュの検証

`<magento_root>/var/page_cache` ディレクトリが空であることを確認します。

1. Commerce サーバーにログインするか、ファイルシステムのオーナーに切り替えます。
1. 次のコマンドを入力します。

   ```bash
   rm -rf <magento_root>/var/page_cache/*
   ```

1. 1 つ以上のキャッシュ可能なCommerce ページにアクセスします。
1. `var/page_cache/` ディレクトリを確認します。

   ディレクトリが空の場合は、これで完了です。 ワニスとCommerceが連携するように正常に設定されました。

1. `var/page_cache/` ディレクトリをクリアした場合は、Varnish を再起動します。

>[!TIP]
>
>503 （バックエンド取得に失敗しました）エラーが発生した場合は、_Adobe Commerce ヘルプセンター [503 （サービスを利用できない）エラーのトラブルシューティング ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshooting-503-errors.html?lang=ja) を参照してください_。
