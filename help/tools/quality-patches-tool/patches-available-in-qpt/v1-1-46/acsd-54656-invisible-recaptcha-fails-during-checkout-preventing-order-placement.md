---
title: チェックアウト中に非表示の[!DNL reCAPTCHA]が失敗し、注文の配置ができなくなります
description: ACSD-54656 パッチを適用して、チェックアウト中に見えない[!DNL reCAPTCHA]が正しく機能しないAdobe Commerceの問題を修正します。これにより、注文の配置が妨げられます。
feature: Checkout, Gift
role: Admin, Developer
exl-id: 08850189-2e1b-4132-8d63-ce447b1f1211
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4fc0a729-4349-5307-bd06-1b4bfbaf5d0c
    internal-label: Gift
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%
---
# ACSD-54656: チェックアウト中に非表示の[!DNL reCAPTCHA]が正しく機能しないため、注文の配置が妨げられています。

ACSD-54656 パッチは、チェックアウト中に見えない[!DNL reCAPTCHA]が正しく機能しない問題を修正します。これにより、注文の配置が妨げられます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.46がインストールされている場合に利用できます。 パッチ IDはACSD-54656です。 この問題は、Adobe Commerce 2.4.6で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

チェックアウト中に非表示の[!DNL reCAPTCHA]が正しく機能しないため、注文の配置が妨げられています。

<u>複製する手順</u>:

1. [!UICONTROL Checkout] ページのギフトカードに任意の種類の[!DNL reCAPTCHA]を有効にします。
1. 商品をカートに追加し、**[!UICONTROL Checkout]** ページに移動します。
1. ギフトカードフォームを展開し、有効なギフトカードクーポンを入力します。
1. 「**[!UICONTROL See balance and apply]**」ボタンをクリックします。

<u>期待される結果</u>:

ギフトカードが正常に適用されました。

<u>実際の結果</u>:

エラーメッセージが表示されます：*[!DNL reCAPTCHA]検証に失敗しました。もう一度やり直してください*。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
