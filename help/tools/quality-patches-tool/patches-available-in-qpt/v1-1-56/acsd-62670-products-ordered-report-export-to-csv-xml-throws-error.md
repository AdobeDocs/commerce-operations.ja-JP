---
title: 'ACSD-62670: [!UICONTROL Ordered Products Report]をCSVに書き出すと、XMLが404 エラーを返す'
description: ACSD-62670 パッチを適用して、[!UICONTROL Ordered Products Report]をCSVおよびXMLに書き出すとエラーが発生するAdobe Commerceの問題を修正します。
feature: Reporting, Admin Workspace, Data Import/Export
role: Admin, Developer
exl-id: 99d77ddd-4fb3-4eda-8771-62c0e25f49d1
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# ACSD-62670: *[!UICONTROL Ordered Products Report]* CSVへの書き出しおよびXML スローのエラー

ACSD-62670 パッチは、*[!UICONTROL Ordered Products Report]*&#x200B;をCSVおよびXMLに書き出すとエラーが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ja) 1.1.56がインストールされている場合に利用できます。 パッチ IDはACSD-62670です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.4.4-p11、2.4.5-p10、2.4.6-p8、2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

*[!UICONTROL Ordered Products Report]*&#x200B;をCSVおよびXMLに書き出すと、エラーがスローされます。

<u>複製する手順</u>:

1. *管理者* パネルに移動し、**[!UICONTROL Reports]** > **[!UICONTROL Products]** > **[!UICONTROL Ordered]**&#x200B;に移動します。
1. CSVまたはExcel ファイルを書き出してみます。

<u>期待される結果</u>:

レポートはエラーなく書き出されます。

<u>実際の結果</u>:

*[!UICONTROL Ordered Products Report]*&#x200B;の書き出しでは、エラー404が発生します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
