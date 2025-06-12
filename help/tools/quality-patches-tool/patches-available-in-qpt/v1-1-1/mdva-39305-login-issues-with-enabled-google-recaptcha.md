---
title: MDVA-39305：有効なGoogle reCAPTCHA でのログインの問題
description: MDVA-39305 パッチを適用すると、Adobe Commerceの reCAPTCHA が有効になっているときに、登録されたお客様がログインできないGoogleの問題を修正できます。
feature: Console
role: Admin
exl-id: c40fd84a-73dc-42bd-8cda-58738615fbba
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# MDVA-39305：有効なGoogle reCAPTCHA でのログインの問題

>[!NOTE]
>
>このパッチは更新されており、最新のパッチ ID は MDVA-39305-V3 です。 Adobe Commerce バージョン 2.4.4、2.4.5-p2 および 2.4.7 用の新しいパッチが作成されます。詳細については、「[MDVA-39305-V3](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-58/mdva-39305-v3-login-issue-with-enabled-google-recaptcha) パッチの記事」を参照してください。

MDVA-39305 パッチにより、Google reCAPTCHA が有効な場合に、登録されたお客様がログインできない問題が修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1 がインストールされている場合に使用できます。 パッチ ID は MDVA-39305。 この問題は、Adobe Commerce バージョン 2.4.4 および 2.4.7 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* クラウドインフラストラクチャー上のAdobe Commerce 2.4.2-p1、2.4.3-p3、2.4.5-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1-p1 ～ 2.4.3-p3、2.4.4-p1 ～ 2.4.4-p5、2.4.5 ～ 2.4.6-p2

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

登録されたお客様は、有効なGoogle reCAPTCHA を使用してログインすることはできません。

<u> 再現手順 </u>:

1. **Store** / **Configuration** / **Security** / **Google reCAPTCHA ストアフロント** に移動し、**Google reCAPTCHA** を有効にします。
1. **フロントエンド** に移動します。
1. ブラウザーで **開発者ツールコンソール** を開きます。

<u> 期待される結果 </u>:

コンソールに CSP 警告はありません。

<u> 実際の結果 </u>:

コンソールでの CSP 警告。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
