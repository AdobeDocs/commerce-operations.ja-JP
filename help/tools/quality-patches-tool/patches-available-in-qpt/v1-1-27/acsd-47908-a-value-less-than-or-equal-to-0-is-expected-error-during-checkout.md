---
title: 'ACSD-47908: *0以下の値がチェックアウト時に予期される* エラーです'
description: ACSD-47908 パッチを適用して、チェックアウト時に発送手順で発送元と数量を選択する際のAdobe Commerce エラー*0以下の値が想定される*を修正します。
feature: Admin Workspace, Checkout, Orders
role: Admin
exl-id: f1429bd9-652d-43c0-af52-b2258e2a7643
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%
---
# ACSD-47908: *0以下の値は、チェックアウト時に* エラーが発生すると予想されます

ACSD-47908 パッチは、チェックアウト時に出荷手順でソースと数量を選択する際に&#x200B;*0以下の値が予想される*&#x200B;というエラーを修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.27がインストールされている場合に利用できます。 パッチ IDはACSD-47908です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

チェックアウト時に出荷ステップでソースと数量を選択すると、次のエラーがスローされます。*0以下の値が予想されます*。

<u>前提条件</u>:

Adobe Commerce Inventory management（MSI）モジュールをインストールします。

<u>複製する手順</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Sources]**&#x200B;に移動し、複数のソースを設定します。
1. **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]**&#x200B;に移動し、新しいストックを作成します。
   * 次に、ソースを新しい在庫に割り当てます。
1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;に移動し、少なくとも1つの製品を編集します。
   * 製品が新しいソースに割り当てられていることを確認し、使用可能な数量を指定します。
1. **[!UICONTROL Sales]** > **[!UICONTROL Orders]**&#x200B;に移動し、新しい注文を作成します。
1. これらの商品を注文に追加して配置します。
1. **[!UICONTROL Ship]**&#x200B;をクリックします。
1. 発送するソースを選択します。
1. 発送する各商品の数量を指定します。
1. ページをリロードします。
1. **[!UICONTROL Proceed to Shipment]**&#x200B;をクリックします。

<u>期待される結果</u>:

新しい配送ページがエラーなく開きます。

<u>実際の結果</u>:

* 入力した数量は検証できません。
* 次のエラーがスローされます：*0*&#x200B;以下の値を入力してください。

  ただし、エラーは一貫性がなく、常に表示されるわけではありません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
