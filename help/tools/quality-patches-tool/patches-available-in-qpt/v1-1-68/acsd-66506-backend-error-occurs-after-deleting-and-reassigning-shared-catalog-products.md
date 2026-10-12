---
title: ACSD-66506：共有カタログ製品の削除と再割り当て後にバックエンドエラーが発生する
description: バックエンドがエラーをスローするAdobe Commerceの問題を修正するには、ACSD-66506 パッチを適用します。 製品を確認し、以前に割り当てられた製品を削除し、新しい製品を共有カタログに割り当てた後に、もう一度試してください*。
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: db08c58b-7e14-4bd8-af85-8f63aba9051b
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%
---
# ACSD-66506：共有カタログ製品の削除と再割り当て後にバックエンドエラーが発生する

ACSD-66506 パッチは、バックエンドがエラー&#x200B;*をスローする問題を修正します。要求された製品は存在しません。 製品を確認し、以前に割り当てられた製品を削除し、新しい製品を共有カタログに割り当てた後、もう一度試してください*。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68がインストールされている場合に利用できます。 パッチ IDはACSD-66506です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

以前に割り当てられた製品を削除し、**[!UICONTROL Shared Catalog]**&#x200B;に新しい製品を割り当てると、バックエンドで次のエラーが返されます：*要求された製品が存在しません。 製品を確認して、もう一度試してください*

<u>複製する手順</u>:

1. パフォーマンス ツールキットを使用して製品をいくつか作成します：`bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`
1. **[!UICONTROL [!DNL B2B] Features]**&#x200B;設定に移動し、**[!UICONTROL Enable Company]**&#x200B;と&#x200B;**[!UICONTROL Enable Shared Catalog]**&#x200B;を`Yes`に設定します。
1. 新しい共有カタログを作成します。
1. 生成されたすべての商品を、新しく作成した共有カタログに割り当てます。
1. 共有カタログに割り当てられた製品を削除するには、**[!UICONTROL Product Import]**&#x200B;を使用します。
   1. SKUでフィルタリングされた製品を書き出します。
   1. **[!UICONTROL Import Behavior: Delete]**&#x200B;を選択してから、同じファイルを読み込みます。
1. **[!UICONTROL Shared Catalog]**&#x200B;を開き、価格と構造を設定します。
   1. **[!UICONTROL Set Pricing and Structure]**&#x200B;を選択します。
   1. 「**[!UICONTROL Next]**」、「**[!UICONTROL Generate Catalog]**」の順にクリックします。
   1. **[!UICONTROL Save]**&#x200B;をクリックします。

<u>期待される結果</u>:

エラーが発生しても、エラーは発生せず、製品は共有カタログに残ります。

<u>実際の結果</u>:

エラーが発生しました：*要求された製品が存在しません。 製品を確認して再試行してください*。すべての製品が共有カタログから削除されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
