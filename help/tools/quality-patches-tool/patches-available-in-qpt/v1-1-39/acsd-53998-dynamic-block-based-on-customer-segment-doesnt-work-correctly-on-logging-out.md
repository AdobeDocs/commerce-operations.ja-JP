---
title: 「ACSD-53998：顧客セグメントに基づく動的ブロックがログアウト後に正しく機能しない」
description: ACSD-53998 パッチを適用すると、カスタマーアカウントからログアウトした後、カスタマーセグメントに基づく動的ブロックが正しく機能しないAdobe Commerceの問題を修正できます。
feature: Customers, Page Builder, Personalization
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-53998：顧客セグメントに基づく動的ブロックがログアウト後に正しく機能しない

ACSD-53998 パッチは、顧客アカウントからログアウトした後、顧客セグメントに基づく動的ブロックが正しく機能しない問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.39 がインストールされている場合に使用できます。 パッチ ID は ACSD-53998 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p2 - 2.4.4-p6、2.4.5-p1 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

顧客セグメントに基づく動的ブロックは、顧客アカウントからログアウトした後、正しく機能しません。

<u> 前提条件 </u>:

[!DNL Page Builder] モジュールをインストールして有効にします。

<u> 再現手順 </u>:

1. 条件なしで 2 つの顧客セグメントを作成します。
1. 各セグメントに 2 つのダイナミック ブロックを作成します。
1. 2 つのダイナミック ブロックを [!DNL Page Builder] つのダイナミック ブロックとして含むブロックを作成します。
1. 上記のブロックを含んだウィジェットを作成し、すべてのページのフッターセクションの下にブロックを表示します。
1. キャッシュをクリアします。
1. ホームページを開きます。
1. 顧客としてログインします。
1. ログアウトします。

<u> 期待される結果 </u>:

ログインした顧客用に作成されたバナーは、ゲストユーザーには表示されません。

<u> 実際の結果 </u>:

ログインした顧客セグメント用に作成されたバナーは、顧客アカウントからログアウトした後も表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
