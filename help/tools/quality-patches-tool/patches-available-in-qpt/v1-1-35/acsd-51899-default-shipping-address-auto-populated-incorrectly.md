---
title: 'ACSD-51899: デフォルトの配送先住所が誤って自動入力される'
description: ACSD-51899 パッチを適用して、デフォルトの配送先住所に間違った住所が自動入力されるAdobe Commerceの問題を修正します。
feature: Checkout
role: Admin
exl-id: 14e48613-6af8-476c-978d-87c27a0b0d15
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# ACSD-51899: デフォルトの配送先住所が誤って自動入力される

ACSD-51899 パッチは、デフォルトの配送先住所に間違った住所が自動入力される問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.35がインストールされている場合に利用できます。 パッチ IDはACSD-51899です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

デフォルトの配送先住所に間違った住所が自動入力される

<u>複製する手順</u>:

1. 発送方法で&#x200B;**実店舗での受け取り**&#x200B;を有効にします。
1. *stock*&#x200B;と&#x200B;*source*&#x200B;を作成します。
1. 製品を作成し、製品をソースに割り当てます。
1. 商品をカートに追加。
1. **ミニカートからチェックアウト**&#x200B;に進むをクリックします。
1. テスト用メールアドレスを入力し、**ストアで選択**&#x200B;を選択します。
1. 「**ストアを選択**」ボタンをクリックし、選択するストアの場所を選択します。
1. 「**次へ**」ボタンをクリックします。
1. ストアのロゴをクリックして、**ホームページ**&#x200B;に移動します。
1. **ミニカート**&#x200B;を開きます。
1. **カートの表示と編集**&#x200B;という名前の下のハイパーリンクをクリックします。
1. 「**チェックアウトに進む**」をクリックします。
1. 配送ページの「配送」ボタンをクリックします。

<u>期待される結果</u>

*国、地域、郵便番号*&#x200B;を除き、配送先住所フィールドは空のままです。

<u>実際の結果</u>

デフォルトの配送先住所は、ページを更新した後、*実店舗での受け取り*&#x200B;の住所が自動入力されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
