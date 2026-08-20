---
title: ACSD-50512：ダウンロード可能な製品ステージング更新プログラムの開始日を更新する際にエラーが発生する
description: ACSD-51892 パッチを適用して、エラー*ダウンロード可能なリンクが製品に関連しないAdobe Commerceのパフォーマンス問題を修正します。ダウンロード可能な製品ステージング更新プログラムの開始日を更新する際に、リンクを確認して、もう一度試してください*。
feature: Products, Staging
role: Admin
exl-id: 9c3b4d45-c500-46a7-8679-a8aa9e0a66d6
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-50512：ダウンロード可能な製品ステージング更新の開始日を更新する際にエラーが発生する

ACSD-50512 パッチは、エラー&#x200B;*ダウンロード可能なリンクが製品に関連しない問題を修正します。 ダウンロード可能な製品ステージング更新プログラムの開始日を更新する際に、リンクを確認して再試行してください*。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.33がインストールされている場合に利用できます。 パッチ IDはACSD-51502です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

エラー&#x200B;*ダウンロード可能なリンクが製品と関連していません。 ダウンロード可能な製品ステージング更新プログラムの開始日を更新する際に、リンクを確認して再試行してください*。

<u>複製する手順</u>:

1. *ダウンロード可能なリンク*&#x200B;と&#x200B;*サンプルリンク*&#x200B;を含むダウンロード可能な製品を作成します。
1. 同じ製品に対してスケジュールされた更新を作成し、製品を保存します。
1. 事前設定済みのスケジュールされた更新（手順2から）を編集し、開始日を変更します。
1. スケジュールされた更新を保存します。

<u>期待される結果</u>:

スケジュールされた更新への変更が正常に保存されます。

<u>実際の結果</u>:

次のエラーが発生します：*ダウンロード可能なリンクが製品と関連しません。 リンクを確認して、もう一度やり直してください*。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
