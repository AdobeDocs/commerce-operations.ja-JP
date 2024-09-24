---
title: 「MDVA-39384：会社ユーザーのカスタム顧客属性を保存できない」
description: MDVA-39384 パッチを使用すると、会社ユーザーのカスタム顧客属性が保存されない問題を解決できます。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches） 1.1.2 がインストールされている場合に利用できます。 パッチ ID は MDVA-39384。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。
feature: Attributes, B2B, Companies
role: Developer
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-39384：会社ユーザーのカスタム顧客属性を保存できません

MDVA-39384 パッチを使用すると、会社ユーザーのカスタム顧客属性が保存されない問題を解決できます。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)1.1.2 がインストールされている場合に使用できます。 パッチ ID は MDVA-39384。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.1 ～ 2.3.6、2.4.1 ～ 2.4.3

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

会社ユーザーのカスタム顧客属性が保存されません。

<u> 前提条件 </u>:

B2B モジュールがインストールされている。

<u> 再現手順 </u>:

1. **ストア**/設定/**設定**/**B2B 機能** に移動し、**会社を有効にする** を「はい」に設定します。
1. カスタム顧客属性を作成します。
   * 値必須：Yes （オプション。検証エラーが表示されるように有効化します）。
   * ストアフロントに表示：はい。
   * 使用するForms：すべての機能がリストに表示されます。
1. 会社を作成し、会社管理者としてログインします。
1. アカウントで会社構造に移動します。
1. **ユーザーを追加** リンクをクリックします。
1. カスタム属性を含むフォームに入力します。
1. **保存** をクリックします。

<u> 期待される結果 </u>:

カスタム属性値は、新しい会社ユーザーと共に保存されます。

<u> 実際の結果 </u>:

カスタム属性値は、新しい会社ユーザーと共に保存されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
