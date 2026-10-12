---
title: 'ACSD-47937: アプリケーションレベルのキャッシュが原因で値下げ通知が送信されない'
description: アプリケーションレベルのキャッシュにより、値下げ通知が必ずしも送信されないAdobe Commerceの問題を修正するには、ACSD-47937 パッチを適用します。
feature: Admin Workspace, Cache, Orders
role: Admin
exl-id: 91d8e677-c2bb-4230-bbe3-a2c5f9b82e16
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%
---
# ACSD-47937: アプリケーションレベルのキャッシュが原因で値下げ通知が送信されない

ACSD-47937 パッチは、アプリケーションレベルのキャッシュにより、値下げ通知が常に送信されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.26がインストールされている場合に利用できます。 パッチ IDはACSD-47937です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4および2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4、2.4.5、および2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

顧客には、その後の製品価格変更に関する製品価格低下メールは配信されていません。

<u>複製する手順</u>:

1. **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]**&#x200B;の&#x200B;*[!UICONTROL Price Changes]*&#x200B;と&#x200B;*[!UICONTROL Back in Stock]*&#x200B;の両方で&#x200B;**[!UICONTROL Product Alert]**&#x200B;を有効にします。
1. **[!UICONTROL Display Out of Stock Products]**&#x200B;を有効にします。
1. 数量= 0の簡易製品（ABC）を作成します。
1. ストアフロントで顧客を作成し、上記の商品に登録すると、値下げ時に商品アラートが届きます。
1. 顧客に対する製品アラートを開始します。

   ```PHP
   bin/magento queue:consumers:start product_alert
   ```

1. ABC製品の価格を下げます。
1. 商品アラートのcronをトリガーします。

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. ABC商品の価格を再度下げます。
1. 商品アラートのcronをトリガーします。

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

>[!NOTE]
>
>[!DNL n98] ツールに慣れていない場合は、通常どおり`bin/magento cron:run command`を実行し、`cron_schedule` テーブルを監視して、`catalog_product_alert` ジョブが成功ステータスを取得することを確認できます。

<u>期待される結果</u>:

2回目の値下げメールを送信します。

<u>実際の結果</u>:

2回目の値下げメールは送信されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > Commerce クラウドインフラストラクチャ上のパッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」ガイド

## 関連トピックス

* [[!DNL Quality Patches Tool]  リリース：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを確認します
* [Commerce実装プレイブックのデータベーステーブルを修正するためのベストプラクティス &#x200B;](/help/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables.md#why-adobe-recommends-avoiding-modifications)


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
