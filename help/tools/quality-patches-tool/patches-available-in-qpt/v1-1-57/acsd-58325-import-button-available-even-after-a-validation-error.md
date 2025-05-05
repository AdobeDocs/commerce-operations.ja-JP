---
title: ACSD-58325：検証エラーの後も使用できる [!UICONTROL Import] ボタン
description: ACSD-58325 パッチを適用して、検証エラーの後も「[!UICONTROL Import]」ボタンが使用可能なAdobe Commerceの問題を修正してください。
feature: Data Import/Export
role: Admin, Developer
exl-id: 551a9ac7-9b7f-49b5-9255-2014c330fb07
source-git-commit: c50fa066d02c04a08c28730afffe4508019a93aa
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# ACSD-58325：検証エラーの後も使用できる [!UICONTROL Import] ボタン

ACSD-58325 パッチは、検証エラーの後も **[!UICONTROL Import]** ボタンが使用可能な問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 がインストールされている場合に使用できます。 パッチ ID は ACSD-58325 です。 この問題はAdobe Commerce 2.4.7 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerce バージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

検証エラーの後も「[!UICONTROL Import]」ボタンを使用できます。

<u> 再現手順 </u>:

1. 製品読み込み用の CSV ファイルを作成する際に、ファイル内の画像名が正しくありません。
1. 作成した CSV ファイルを使用して、スケジュールされた製品読み込みを作成します。
1. スケジュールされた読み込みが実行されるまで待ちます。
1. グリッドで [!UICONTROL Last outcome] をチェッ **[!UICONTROL Scheduled Imports/Exports]** します。

<u> 期待される結果 </u>:

[!UICONTROL Last outcome] は [!UICONTROL Failed] であるべきです。

<u> 実際の結果 </u>:

[!UICONTROL Last outcome] は [!UICONTROL Successful] です。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
