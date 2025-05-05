---
title: チェックアウト中に非表示  [!DNL reCAPTCHA]  失敗し、注文を行えなくなる
description: ACSD-54656 パッチを適用して、チェックアウト時に非表示のが正しく機能せず  [!DNL reCAPTCHA]  注文の発注が妨げられるAdobe Commerceの問題を修正してください。
feature: Checkout, Gift
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-54656：チェックアウト時に非表示の [!DNL reCAPTCHA] が正しく機能せず、注文の配置が妨げられている。

ACSD-54656 パッチは、チェックアウト時に非表示の [!DNL reCAPTCHA] が正しく機能せず、注文の配置が妨げられる問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.46 がインストールされている場合に使用できます。 パッチ ID は ACSD-54656 です。 この問題はAdobe Commerce 2.4.6 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.5-p5

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

チェックアウト中に非表示の [!DNL reCAPTCHA] が正しく機能せず、注文の配置が妨げられます。

<u> 再現手順 </u>:

1. [!UICONTROL Checkout] ページでギフトカードに対して任意のタイプの [!DNL reCAPTCHA] を有効にします。
1. 買い物かごに製品を追加して、**[!UICONTROL Checkout]** のページに移動します。
1. ギフトカードフォームを展開し、有効なギフトカードクーポンを入力します。
1. ボタンをクリ **[!UICONTROL See balance and apply]** クします。

<u> 期待される結果 </u>:

ギフト カードが正常に適用されました。

<u> 実際の結果 </u>:

エラーメッセージ「*[!DNL reCAPTCHA]検証に失敗しました。もう一度試してください*」が表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
