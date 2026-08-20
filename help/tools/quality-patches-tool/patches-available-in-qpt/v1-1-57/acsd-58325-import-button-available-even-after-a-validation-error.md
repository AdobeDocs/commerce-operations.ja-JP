---
title: 'ACSD-58325: [!UICONTROL Import] ボタンは、検証エラーの後でも使用できます'
description: ACSD-58325 パッチを適用して、検証エラーの後でも[!UICONTROL Import] ボタンが使用可能なAdobe Commerceの問題を修正します。
feature: Data Import/Export
role: Admin, Developer
exl-id: 551a9ac7-9b7f-49b5-9255-2014c330fb07
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# ACSD-58325: [!UICONTROL Import] ボタンは、検証エラーの後でも使用できます

ACSD-58325 パッチは、検証エラーの後でも&#x200B;**[!UICONTROL Import]** ボタンが使用できる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57がインストールされている場合に利用できます。 パッチ IDはACSD-58325です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました
* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerceのバージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

検証エラーの後でも、[!UICONTROL Import] ボタンを使用できます。

<u>複製する手順</u>:

1. 製品の読み込み用のCSV ファイルを、ファイル内の不正な画像名で作成します。
1. 作成したCSV ファイルを使用して、スケジュールされた製品インポートを作成します。
1. スケジュールされた読み込みが実行されるまで待ちます。
1. **[!UICONTROL Scheduled Imports/Exports]** グリッドの[!UICONTROL Last outcome]を確認してください。

<u>期待される結果</u>:

[!UICONTROL Last outcome]は[!UICONTROL Failed]である必要があります。

<u>実際の結果</u>:

[!UICONTROL Last outcome]は[!UICONTROL Successful]です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
