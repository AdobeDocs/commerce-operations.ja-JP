---
title: ACSD-51240：会社登録フォーム経由での登録中に、アップロードしたファイルが見つからない
description: ACSD-51240 パッチを適用すると、会社登録フォーム経由での登録時に、アップロードしたファイルが見つからないAdobe Commerceの問題を修正できます。
exl-id: 78e339d6-435e-4856-9f57-98bb955d093c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-51240：会社登録フォーム経由での登録中に、アップロードしたファイルが見つからない

>[!NOTE]
>
>このパッチは [ACSD-55628](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-42/acsd-55628-upload-file-company-registration-form-replace-file-customer-attribute-storefront.md) に置き換えられます。

ACSD-51240 パッチは、会社登録フォーム経由で登録する際に、アップロードしたファイルが見つからない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33 がインストールされている場合に使用できます。 パッチ ID は ACSD-51240 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 &lt; 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) で互換性を確認します。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 問題

アップロード済みファイルが、会社登録フォーム経由での登録中に見つかりません。

<u> 再現手順 </u>:

1. **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B >Company]** > **[!UICONTROL Enable]** = *はい* を設定します。
1. **[!UICONTROL File]** タイプの新しい顧客属性を作成し、**[!UICONTROL Show in StoreFront]** = *はい* を設定して、**[!UICONTROL all forms]** を選択します。
1. ストアフロントで新しい会社を作成し、新しい属性の画像をアップロードします。
ストアフロントで会社と管理者ユーザーを開きます。

<u> 期待される結果 </u>:

アップロードされたファイルが表示されます。

<u> 実際の結果 </u>:

アップロードされたファイルは、会社ページにも、[!UICONTROL Commerce Admin] の管理者の顧客ページにも表示されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
