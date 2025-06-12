---
title: ACSD-51899：デフォルトの配送先住所が正しく自動入力されない
description: ACSD-51899 パッチを適用すると、デフォルトの配送先住所に間違った住所が自動入力されるAdobe Commerceの問題を修正できます。
feature: Checkout
role: Admin
exl-id: 14e48613-6af8-476c-978d-87c27a0b0d15
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-51899：デフォルトの配送先住所が正しく自動入力されない

ACSD-51899 パッチは、デフォルトの配送先住所が間違った住所で自動入力される問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.35 がインストールされている場合に使用できます。 パッチ ID は ACSD-51899 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

デフォルトの配送先住所は、間違った住所で自動入力されます

<u> 再現手順 </u>:

1. 発送方法で **店舗での受け取り** を有効にします。
1. *stock* および *source* を作成します。
1. 製品を作成し、製品をソースに割り当てます。
1. 商品を買い物かごに追加します。
1. ミニ買い物かごから「**チェックアウトに進む**」をクリックします。
1. テストメールアドレスを入力し、「**店舗で選択** を選択します。
1. **ストアを選択** ボタンをクリックし、選択するストアの場所を選択します。
1. 「**次へ**」ボタンをクリックします。
1. ストアのロゴをクリックして **ホームページ** に移動します。
1. **ミニカート** を開きます。
1. 下部にある「**買い物かごを表示して編集** というハイパーリンクをクリックします。
1. **チェックアウトに進む** をクリックします。
1. [ 配送 ] ページの [ 配送 ] ボタンをクリックします。

<u> 期待される結果 </u>

*国、地域、郵便番号* を除き、発送先住所フィールドは空のままです。

<u> 実績 </u>

デフォルトの配送先住所には、ページを更新すると *店舗での受け取り* 住所が自動入力されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
