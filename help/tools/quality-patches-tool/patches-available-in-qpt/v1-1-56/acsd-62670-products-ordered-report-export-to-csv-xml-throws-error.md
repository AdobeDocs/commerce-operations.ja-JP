---
title: ACSD-62670:CSV および XML への [!UICONTROL Ordered Products Report] エクスポートで 404 エラーが返される
description: ACSD-62670 パッチを適用すると、[!UICONTROL Ordered Products Report] を CSV および XML に書き出すとエラーがスローされるAdobe Commerceの問題を修正できます。
feature: Reporting, Admin Workspace, Data Import/Export
role: Admin, Developer
exl-id: 99d77ddd-4fb3-4eda-8771-62c0e25f49d1
type: Troubleshooting
source-git-commit: 3469da56c15499de4ceb5313c3cc2dfde0f0771c
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# ACSD-62670:CSV および XML への *[!UICONTROL Ordered Products Report]* エクスポートでエラーがスローされる

ACSD-62670 パッチでは、*[!UICONTROL Ordered Products Report]* を CSV および XML に書き出すとエラーがスローされる問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ja) 1.1.56 がインストールされている場合に使用できます。 パッチ ID は ACSD-62670 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p11、2.4.5-p10、2.4.6-p8、2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

*[!UICONTROL Ordered Products Report]* を CSV および XML に書き出すと、エラーがスローされる。

<u> 再現手順 </u>:

1. *管理者* パネルに移動し、**[!UICONTROL Reports]**/**[!UICONTROL Products]**/**[!UICONTROL Ordered]** に移動します。
1. CSV または Excel ファイルを書き出そうとします。

<u> 期待される結果 </u>:

レポートはエラーなしで書き出されます。

<u> 実際の結果 </u>:

*[!UICONTROL Ordered Products Report]* のエクスポートの結果、エラー 404 が発生する。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
