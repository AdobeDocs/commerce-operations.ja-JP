---
title: ACSD-63793：読み込みプロセスは、異なるブラウザータブで互いに干渉します
description: ACSD-63793 パッチを適用すると、異なるブラウザータブで読み込みプロセスが互いに干渉するAdobe Commerceの問題を修正できます。
feature: Data Import/Export
role: Admin, Developer
exl-id: f6bed4c4-5ea2-47e7-97fa-d7717470297f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-63793：読み込みプロセスは、異なるブラウザータブで互いに干渉します

ACSD-63793 パッチを使用すると、異なるブラウザータブで読み込みプロセスが互いに干渉する問題を修正できます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 がインストールされている場合に使用できます。 パッチ ID は ACSD-63793 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

管理 UI を使用したデータのインポートが別のインポートと干渉し、あるインポートからのデータが別のインポートで処理される原因となります。

<u> 再現手順 </u>:

1. **[!UICONTROL System]**/**[!UICONTROL Data Transfer]**/**[!UICONTROL Import]** に移動します。
1. **[!UICONTROL Entity Type]** を *[!UICONTROL Customers and Addresses]（単一ファイル）* に設定します。
1. **[!UICONTROL Import Behavior]** を *[!UICONTROL Add/Update]* に設定します。
1. インポートする有効なファイルを選択してください。
1. **[!UICONTROL Check Data]** ボタンをクリックします。
1. このタブは開いたままにしておきます。
1. 新しいタブを開き、無効なデータを含むファイルで手順を繰り返します（例えば、異なる顧客に対して 2 件の同一のメール）。
1. 最初のタブに戻ります。
1. 下部にある「**[!UICONTROL Import]**」ボタンをクリックします。

<u> 期待される結果 </u>:

インポートプロセスは互いに干渉してはいけません。

<u> 実際の結果 </u>:

読み込みプロセスが完了し、レポートファイルをダウンロードできるようになります。 2 行目にエラーが示され、最初の検証がエラーなしで渡された場合でも、別のインポートからのデータが処理されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
