---
title: MDVA-41061：管理者から製品を保存すると、Stock ステータスが販売可能にリセットされる
description: MDVA-41061 パッチは、製品が管理者から保存されたときに在庫状況が販売可能にリセットされる問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.5がインストールされている場合に利用できます。 パッチ IDはMDVA-41061です。 最新のパッチバージョンは、MDVA-41061-V3 パッチ IDを含むQPT 1.1.15で利用できます。 この問題は、Adobe Commerce 2.4.4で修正されています。
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: ddbc30ef-bc88-4878-8bd8-6880823819a2
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
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
source-wordcount: '518'
ht-degree: 0%
---
# MDVA-41061：管理者から製品を保存すると、Stock ステータスが販売可能にリセットされる

MDVA-41061 パッチは、製品が管理者から保存されたときに在庫状況が販売可能にリセットされる問題を修正します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.5がインストールされている場合に使用できます。 パッチ IDはMDVA-41061です。 最新のパッチバージョンは、MDVA-41061-V3 パッチ IDを含むQPT 1.1.15で利用できます。 この問題は、Adobe Commerce 2.4.4で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方式） 2.4.2 - 2.4.2-p2、2.4.3 - 2.4.3-p2

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

製品が管理者から保存されると、Stock ステータスが販売可能にリセットされます。

<u>前提条件</u>:

在庫モジュールが取り付けられています。

<u>複製する手順</u>:

1. Qty = 1のシンプルな商品を作成します。
1. 手順1で作成した商品を使用して注文します。
1. cronの実行 – `cataloginventory_stock_status` テーブルで`inventory.reservations.updateSalabilityStatus` キューが実行され、製品在庫ステータスが0に変更されていることを確認します。
1. フロントエンドで製品を確認します。 **在庫切れ**&#x200B;としてマークする必要があります。
1. 変更を加えることなく、製品を管理者に保存します。

<u>期待される結果</u>:

* 在庫状況は更新しないでください。
* 製品は、フロントエンドで&#x200B;**在庫切れ**&#x200B;である必要があります。

<u>実際の結果</u>:

* シンプルな商品は、フロントエンドで&#x200B;**In Stock**&#x200B;としてマークされます。
* ユーザーは、カートに追加しようとすると、*要求された数量は利用できません* メッセージを受け取ります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
