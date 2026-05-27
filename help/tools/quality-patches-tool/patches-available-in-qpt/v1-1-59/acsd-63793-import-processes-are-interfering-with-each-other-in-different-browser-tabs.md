---
title: ACSD-63793：読み込みプロセスが異なるブラウザータブで互いに干渉する
description: 読み込みプロセスが異なるブラウザータブで互いに干渉するAdobe Commerceの問題を修正するには、ACSD-63793 パッチを適用します。
feature: Data Import/Export
role: Admin, Developer
exl-id: f6bed4c4-5ea2-47e7-97fa-d7717470297f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-63793：読み込みプロセスが異なるブラウザータブで互いに干渉する

ACSD-63793 パッチは、読み込みプロセスが異なるブラウザータブで互いに干渉する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59がインストールされている場合に利用できます。 パッチ IDはACSD-63793です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

管理UIを使用してデータを読み込むと、別の読み込みが妨げられ、ある読み込みのデータが別の読み込みで処理されます。

<u>複製する手順</u>:

1. **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]**&#x200B;に移動します。
1. **[!UICONTROL Entity Type]**&#x200B;を&#x200B;*[!UICONTROL Customers and Addresses]（単一ファイル）*&#x200B;に設定します。
1. **[!UICONTROL Import Behavior]**&#x200B;を&#x200B;*[!UICONTROL Add/Update]*&#x200B;に設定します。
1. インポートする有効なファイルを選択してください。
1. 「**[!UICONTROL Check Data]**」ボタンをクリックします。
1. このタブを開いたままにします。
1. 新しいタブを開き、無効なデータを含むファイルで手順を繰り返します（例えば、異なる顧客に対して2つの同一のメール）。
1. 最初のタブに戻ります。
1. 下部の「**[!UICONTROL Import]**」ボタンをクリックします。

<u>期待される結果</u>:

読み込みプロセスは互いに干渉しないでください。

<u>実際の結果</u>:

インポートプロセスが完了し、レポートファイルをダウンロードできます。 これは2行目のエラーを示し、最初の検証がエラーなしで渡されたとしても、別のインポートからのデータが処理されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
