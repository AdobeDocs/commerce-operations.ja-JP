---
title: 'MDVA-42326: セッションのタイムアウト後にチェックアウト時にエラーが発生する'
description: MDVA-42326 パッチは、永続的なショッピングカートが有効になっている場合でも、セッションのタイムアウト後にチェックアウト時に顧客がエラーを受け取る問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.8がインストールされている場合に利用できます。 パッチ IDはMDVA-42326です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: Checkout, Orders
role: Admin
exl-id: f9ef6778-298b-4ff9-9c4b-b3f47bb04b67
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%
---
# MDVA-42326: セッションのタイムアウト後にチェックアウト時にエラーが発生する

MDVA-42326 パッチは、永続的なショッピングカートが有効になっている場合でも、セッションのタイムアウト後にチェックアウト時に顧客がエラーを受け取る問題を解決します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.8がインストールされている場合に使用できます。 パッチ IDはMDVA-42326です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.3.6 - 2.3.7-p2、2.4.1 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

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
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
