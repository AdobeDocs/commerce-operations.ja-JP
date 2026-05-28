---
title: 'MDVA-42326: セッションのタイムアウト後にチェックアウト時にエラーが発生する'
description: MDVA-42326 パッチは、永続的なショッピングカートが有効になっている場合でも、セッションのタイムアウト後にチェックアウト時に顧客がエラーを受け取る問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.8がインストールされている場合に利用できます。 パッチ IDはMDVA-42326です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: Checkout, Orders
role: Admin
exl-id: f9ef6778-298b-4ff9-9c4b-b3f47bb04b67
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 0%

---

# MDVA-42326: セッションのタイムアウト後にチェックアウト時にエラーが発生する

MDVA-42326 パッチは、永続的なショッピングカートが有効になっている場合でも、セッションのタイムアウト後にチェックアウト時に顧客がエラーを受け取る問題を解決します。 このパッチは、[品質パッチツール （QPT） ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8がインストールされている場合に使用できます。 パッチ IDはMDVA-42326です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.3.6 - 2.3.7-p2、2.4.1 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

永続的なショッピングカートが有効になっている場合でも、セッションのタイムアウト後にチェックアウト時にエラーが発生します。

<u>前提条件</u>:

1. **Config** > **General** > **Web** > **Default Cookie Settings** > **Cookie Lifetime**&#x200B;に移動し、**120**&#x200B;に設定します。
1. **Config** > **Customers** > **Customer Configuration** > **Online Customers Options**&#x200B;に移動し、両方の値を&#x200B;**2**&#x200B;に設定します。
1. **Config** > **顧客** > **永続的なショッピングカート**&#x200B;に移動し、**有効**&#x200B;に設定します。
1. **Config** > **Sales** > **Payment Methods**&#x200B;に移動し、**Check/Money Order**&#x200B;を除くすべての支払い方法をオフにします（有効にする必要があります）。

<u>複製する手順</u>:

1. 顧客としてログインし、商品をカートに追加します。
1. 買い物かごをチェック。
1. 2分間待ちます（前提条件で設定）。セッションはタイムアウトします。
1. 「**チェックアウトに移動**」をクリックし、ページを更新しないでください。
1. ゲストとしてチェックアウトし、配送先住所を入力し、配送方法を選択します。
1. 「**次へ**」をクリックします。
1. **レビューと支払い** ページで、**注文を完了**&#x200B;をクリックします。 1つの支払い方法のみが許可されているため、顧客は支払い方法を選択せずに注文できるはずです。

<u>期待される結果</u>:

顧客が注文できる必要があります。

<u>実際の結果</u>:

お客様は次のエラーを受け取ります。*アドレス検証に失敗しました：メールの形式が間違っています*。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
