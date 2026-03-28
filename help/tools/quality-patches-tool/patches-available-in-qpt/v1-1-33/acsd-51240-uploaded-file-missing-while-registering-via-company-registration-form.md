---
title: ACSD-51240：会社登録フォームによる登録中にアップロードされたファイルが見つからない
description: ACSD-51240 パッチを適用して、会社登録フォームを介して登録中にアップロードされたファイルが見つからないAdobe Commerceの問題を修正します。
exl-id: 78e339d6-435e-4856-9f57-98bb955d093c
type: Troubleshooting
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-51240：会社登録フォームによる登録中にアップロードされたファイルが見つからない

>[!NOTE]
>
>このパッチは[ACSD-55628](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-42/acsd-55628-upload-file-company-registration-form-replace-file-customer-attribute-storefront.md)に置き換えられます。

ACSD-51240 パッチは、会社登録フォームを介した登録中にアップロードされたファイルが見つからない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33がインストールされている場合に利用できます。 パッチ IDはACSD-51240です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 &lt; 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## イシュー

会社登録フォームで登録中にアップロードされたファイルが見つかりません。

<u>複製する手順</u>:

1. **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B >Company]** > **[!UICONTROL Enable]** = *はい*&#x200B;を設定します。
1. タイプ **[!UICONTROL File]**&#x200B;の新しい顧客属性を作成し、**[!UICONTROL Show in StoreFront]** = *Yes*&#x200B;と設定して、**[!UICONTROL all forms]**&#x200B;を選択します。
1. ストアフロントで新しい会社を作成し、新しい属性の画像をアップロードします。
ストアフロントで会社と管理者ユーザーを開きます。

<u>期待される結果</u>:

アップロードしたファイルが表示されます。

<u>実際の結果</u>:

アップロードされたファイルは、会社ページにも[!UICONTROL Commerce Admin]の管理者のお客様ページにも表示されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool]  ガイドの](/help/tools/quality-patches-tool/usage.md)>使用状況[!DNL Quality Patches Tool]。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [&#x200B; [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) ガイドの[!UICONTROL Quality Patches Tool]を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) ガイドの「[!DNL Quality Patches Tool] パッチを検索する」を参照してください。
