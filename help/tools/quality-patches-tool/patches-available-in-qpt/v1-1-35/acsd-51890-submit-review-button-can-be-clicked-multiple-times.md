---
title: ACSD-51890:[!UICONTROL Submit review] のボタンは複数回クリックできます
description: ACSD-51890 パッチを適用すると、検証を行わずに「[!UICONTROL Submit Review]」ボタンを複数回クリックできるAdobe Commerceの問題  [!DNL Google reCAPTCHA v3]  修正できます。
feature: Products
role: Admin
exl-id: db69ccdc-c66e-4bdb-9783-772f2af0d33f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-51890：検証 **[!UICONTROL Submit Review]** なくてもボタンを複数回クリック **[!DNL Google reCAPTCHA v3]** きます

>[!NOTE]
>
>このパッチは [ACSD-55112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-42/acsd-55112-submit-review-button-can-be-clicked-multiple-times.md) に置き換えられます。

ACSD-51890 パッチは、検証を行わずに **[!UICONTROL Submit Review]** ボタンを複数回クリックできる問題 **[!DNL Google reCAPTCHA v3]** 修正しています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.35 がインストールされている場合に使用できます。 パッチ ID は ACSD-51890 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

「**[!UICONTROL Submit Review]**」ボタンは、**[!DNL Google reCAPTCHA v3]** の検証を行わずに複数回クリックできます。

<u> 再現手順 </u>:

1. 製品レビュー用に **[!DNL Google reCAPTCHA v3]** を有効にします。
1. 製品ページを開き、「**[!UICONTROL Review]**」セクションに移動し、[!DNL reCAPTCHA] が表示されていることを確認します。
1. レビューフォームに入力し、「**[!UICONTROL Submit Review]**」ボタンをできるだけ早く複数回クリックします。
1. 管理者から「**[!UICONTROL Review]**」セクションを開きます。

<u> 期待される結果 </u>

重複するレビューは作成されません。

<u> 実績 </u>

重複するレビューが作成されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>): Search for patches[!DNL Quality Patches Tool]」を参照してください。
