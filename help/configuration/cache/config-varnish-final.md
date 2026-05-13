---
title: Varnish設定の確認
description: Adobe Commerceを使用してVarnish設定を最終的に検証する方法について説明します。 テスト手順とトラブルシューティング手法について説明します。
feature: Configuration, Cache
exl-id: 01f28c93-75cd-4969-9142-b8dac0aa2adb
source-git-commit: d20f9d38a06fcd0eed872fe6f7ef1f3ee015a00f
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# Varnish設定の確認 {#final-verification}

これで、Commerceによって生成された`default.vcl`を使用できたので、最終的な検証を行って、Varnishが機能していることを確認できます。

## HTTP応答ヘッダーの検証

Web ブラウザーでCommerce ページにアクセスすると、`curl`または別のユーティリティを使用して、HTTP応答ヘッダーを表示します。

まず、[開発者モード &#x200B;](../cli/set-mode.md#change-to-developer-mode)を使用していることを確認してください。使用しない場合は、ヘッダーが表示されません。

以下に例を挙げます。

```shell
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

重要なヘッダー：

```text
X-Magento-Cache-Control: max-age=86400, public, s-maxage=86400
Age: 0
X-Magento-Cache-Debug: MISS
```

>[!INFO]
>
>この値も使用できます：`X-Magento-Cache-Debug: HIT`。

## ページ読み込み時間の確認

Varnishが動作している場合、キャッシュ可能なブロックを持つCommerce ページは150 ミリ秒未満で読み込まれる必要があります。 そのようなページの例として、フロントドアとストアフロントのカテゴリーページがあります。

ブラウザーインスペクターを使用して、ページの読み込み時間を測定します。

例えば、Chrome インスペクターを使用するには、次の手順を実行します。

1. Chromeのキャッシュ可能なCommerce ページにアクセスします。
1. ページの任意の場所を右クリックします。
1. ポップアップメニューから、**[!UICONTROL Inspect Element]**&#x200B;をクリックします
1. インスペクターパネルで、「**[!UICONTROL Network]**」タブをクリックします。
1. ページを更新します。
1. インスペクターパネルの上部までスクロールして、表示しているページのURLを確認します。

   次の図は、`magento2` インデックスページの読み込みの例を示しています。

   ![表示しているページをクリックします](../../assets/configuration/varnish-inspector.png)

   ページの読み込み時間は、ページ URLの横に表示されます。 この場合、読み込み時間は5 ミリ秒です。 これにより、Varnishがページをキャッシュしたことを確認できます。

1. HTTP応答ヘッダーを表示するには、（名前の列の）ページ URLをクリックします。

   詳しくは、「HTTP応答ヘッダーの検証」の節を参照してください。

## Commerce キャッシュの検証

`<magento_root>/var/page_cache` ディレクトリが空であることを確認してください：

1. Commerce サーバーにログインするか、ファイルシステム所有者に切り替えます。
1. 次のコマンドを入力します。

   ```shell
   rm -rf <magento_root>/var/page_cache/*
   ```

1. キャッシュ可能な1つ以上のCommerce ページにアクセスします。
1. `var/page_cache/` ディレクトリを確認してください。

   ディレクトリが空の場合、おめでとうございます。 VarnishとCommerceの連携が正常に設定されました。

1. `var/page_cache/` ディレクトリをクリアした場合は、Varnishを再起動します。

>[!TIP]
>
>503 （バックエンドの取得に失敗しました）エラーが発生した場合は、_Adobe Commerce ヘルプセンター_&#x200B;の[503 （サービスが利用できません）エラーのトラブルシューティング &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshooting-503-errors.html)を参照してください。
