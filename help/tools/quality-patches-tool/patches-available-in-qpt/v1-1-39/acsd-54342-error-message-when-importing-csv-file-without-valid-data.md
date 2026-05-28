---
title: ACSD-54342：有効なデータなしでCSV ファイルを読み込む際にエラーメッセージが表示される
description: 有効なデータを含まないCSV ファイルを読み込むと誤ったエラーメッセージが表示されるAdobe Commerceの問題を修正するには、ACSD-54342 パッチを適用します。
feature: Roles/Permissions
role: Admin, Developer
exl-id: 34324a18-45af-462b-a6e6-6b6a02d4d331
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-54342：有効なデータなしでCSV ファイルを読み込む際にエラーメッセージが表示される

ACSD-54342 パッチは、有効なデータを含まないCSV ファイルを読み込む際に誤ったエラーメッセージが発生する問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.39がインストールされている場合に利用できます。 パッチ IDはACSD-54342です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

有効なデータを含まないCSV ファイルを読み込むと、誤ったエラーメッセージが表示されます。

<u>複製する手順</u>:

1. 無効なデータのみを含むインポートファイルを作成します（例：[!DNL SKUs]、存在しない顧客アドレスフィールドが無効、形式が正しくない顧客メールアドレス）。
1. ファイルを読み込み、を選択して検証エラーをスキップします。

<u>期待される結果</u>:

検証は`There are no valid rows to import` メッセージで失敗します。

<u>実際の結果</u>:

検証は合格しましたが、読み込みは`Error in data structure: values are mixed` メッセージで失敗します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
