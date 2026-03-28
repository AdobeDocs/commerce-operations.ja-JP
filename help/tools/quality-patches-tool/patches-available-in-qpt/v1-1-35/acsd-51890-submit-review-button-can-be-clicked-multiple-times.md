---
title: 'ACSD-51890: [!UICONTROL Submit review] ボタンを複数回クリックできます'
description: ACSD-51890 パッチを適用して、[!UICONTROL Submit Review]検証なしで [!DNL Google reCAPTCHA v3]  ボタンを複数回クリックできるAdobe Commerceの問題を修正します。
feature: Products
role: Admin
exl-id: db69ccdc-c66e-4bdb-9783-772f2af0d33f
type: Troubleshooting
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-51890: **[!UICONTROL Submit Review]**&#x200B;検証なしで&#x200B;**[!DNL Google reCAPTCHA v3]** ボタンを複数回クリックできます

>[!NOTE]
>
>このパッチは[ACSD-55112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-42/acsd-55112-submit-review-button-can-be-clicked-multiple-times.md)に置き換えられます。

ACSD-51890 パッチは、**[!UICONTROL Submit Review]**&#x200B;検証なしで&#x200B;**[!DNL Google reCAPTCHA v3]** ボタンを複数回クリックできる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.35がインストールされている場合に利用できます。 パッチ IDはACSD-51890です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

**[!UICONTROL Submit Review]** ボタンは、**[!DNL Google reCAPTCHA v3]**&#x200B;検証なしで複数回クリックできます。

<u>複製する手順</u>:

1. 製品レビュー用に&#x200B;**[!DNL Google reCAPTCHA v3]**&#x200B;を有効にします。
1. 製品ページを開き、**[!UICONTROL Review]** セクションに移動し、[!DNL reCAPTCHA]が表示されていることを確認します。
1. レビューフォームに入力し、**[!UICONTROL Submit Review]** ボタンをできるだけ早く複数回クリックします。
1. 管理者から&#x200B;**[!UICONTROL Review]** セクションを開きます。

<u>期待される結果</u>

重複したレビューは作成されません。

<u>実際の結果</u>

重複したレビューが作成されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool]  ガイドの](/help/tools/quality-patches-tool/usage.md)>使用状況[!DNL Quality Patches Tool]。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [&#x200B; [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) ガイドの[!UICONTROL Quality Patches Tool]を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) ガイドの「[!DNL Quality Patches Tool] パッチを検索する」を参照してください。
