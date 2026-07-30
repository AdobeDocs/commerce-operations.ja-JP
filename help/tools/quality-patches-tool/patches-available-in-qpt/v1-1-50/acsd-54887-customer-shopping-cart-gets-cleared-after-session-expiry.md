---
title: ACSD-54887：顧客セッションの有効期限が切れた後、顧客ショッピングカートがクリアされる
description: ACSD-54887 パッチを適用して、[!UICONTROL Persistent Shopping Cart]が有効になっているお客様のセッションの有効期限が切れた後、お客様のショッピングカートがクリアされるAdobe Commerceの問題を修正します。
feature: Shopping Cart
role: Admin, Developer
exl-id: de2a96b2-48ce-4b9b-93bc-f7b64c37463a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# ACSD-54887：顧客セッションの有効期限が切れた後、顧客ショッピングカートがクリアされる

ACSD-54887 パッチは、顧客セッションの有効期限が切れ、[!UICONTROL Persistent Shopping Cart]が有効になった後、顧客のショッピングカートがクリアされる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50がインストールされている場合に利用できます。 パッチ IDはACSD-54887です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.4.4 - 2.4.4-p8、2.4.5-p3 - 2.4.5-p7、および2.4.6-p1 - 2.4.6-p5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

顧客セッションの有効期限が切れ、[!UICONTROL Persistent Shopping Cart]が有効になった後、顧客ショッピングカートがクリアされます。

<u>複製する手順</u>:

1. [!UICONTROL Persistent Shopping Cart]を有効にします。 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** = *はい*&#x200B;に移動します。

   永続性を有効にしてログインします（注：ポップアップ認証では使用できず、直接[!UICONTROL Sign in] ページでのみ使用できます）。

1. 商品をカートに追加する。
1. チェックアウトに進み、支払い方法を選択します。
1. セッションを期限切れにします（`PHPSESSID`を削除）。
1. ページを更新します。 支払い方法が既に選択されており、[!UICONTROL Persistent Cart] Cookieが削除されているため、見積もりはすぐにゲスト見積もりに変換されます。
1. セッションを期限切れにします（`PHPSESSID`を削除）。
1. ページを更新します。 カートが空であることを確認します。
1. もう一度ログインしてください。

<u>期待される結果</u>:

再度ログインすると、カートに商品が表示されます。

<u>実際の結果</u>:

再度ログインすると、カートは空になります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
