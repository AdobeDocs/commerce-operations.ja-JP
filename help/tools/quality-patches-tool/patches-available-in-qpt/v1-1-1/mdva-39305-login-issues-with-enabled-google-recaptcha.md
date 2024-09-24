---
title: 「MDVA-39305：有効なGoogle reCAPTCHA でのログインの問題」
description: MDVA-39305 パッチにより、登録されたお客様が有効なGoogle reCAPTCHA でログインできない問題が修正されました。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches） 1.1.1 がインストールされている場合に利用できます。 パッチ ID は MDVA-39305。 この問題は、Adobe Commerce バージョン 2.4.4 および 2.4.7 で修正される予定であることに注意してください。
feature: Console
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# MDVA-39305：有効なGoogle reCAPTCHA でのログインの問題

MDVA-39305 パッチにより、登録されたお客様が有効なGoogle reCAPTCHA でログインできない問題が修正されました。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)1.1.1 がインストールされている場合に使用できます。 パッチ ID は MDVA-39305。 この問題は、Adobe Commerce バージョン 2.4.4 および 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* クラウドインフラストラクチャー上のAdobe Commerce 2.4.2-p1、2.4.3-p3、2.4.5-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1-p1 ～ 2.4.3-p3、2.4.4-p1 ～ 2.4.4-p5、2.4.5 ～ 2.4.6-p2

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

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

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
