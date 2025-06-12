---
title: ACSD-55566：応答内の内部サーバーエラーで [!UICONTROL mergeCart] mutation が失敗  [!DNL GraphQL]  る
description: ACSD-55566 パッチを適用すると、同じバンドルアイテムを持つソースと宛先の買い物かごを結合する際に、「mergeCart」ミューテーションが内部サーバーエラー in [!DNL GraphQL] response で失敗するAdobe Commerceの問題を修正できます。
feature: GraphQL, Shopping Cart
role: Admin, Developer
exl-id: 84c6fbb9-73b3-4197-aff3-49743f0ebb2c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-55566：応答で内部サーバーエラーが発生し、`mergeCart` mutation が失敗 [!DNL GraphQL] る

ACSD-55566 パッチは、応答で内部サーバーエラーが発生して `mergeCart` ミューテーションのミューテーションが失敗する問題 [!DNL GraphQL] 修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48 がインストールされている場合に使用できます。 パッチ ID は ACSD-55566 です。 この問題はAdobe Commerce 2.5.0 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 ～ 2.4.6-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

同じバ `mergeCart` ドル項目を持つソースと宛先の買い物かご [!DNL GraphQL] 結合する際、ミューテーションは失敗し、応答で内部サーバーエラーが発生します。

<u> 再現手順 </u>:

1. カスタムソースとカスタム在庫を作成します。
1. 作成した在庫をメインの web サイトに割り当てます。
1. 単純な製品を作成し、それに作成したソース（qty=2）を割り当てます。
1. 1 つのオプションと 1 つの子製品（手順 3 で作成した製品）を持つバンドル製品を作成します。
1. [!DNL GraphQL] を使用してゲスト用の買い物かごを作成します。
1. 両方のオプションが選択された状態でバンドル製品を追加します。
1. *cartID* を保存します。
1. 顧客を作成し、顧客トークンを生成します。
1. 顧客カートを作成します。
1. 同じ設定の同じバンドル製品を買い物かごに追加します。
1. ゲストの買い物かごを顧客の買い物かごに結合してみます。

<u> 期待される結果 </u>:

顧客の買い物かごには、両方の買い物かごからの製品が含まれています。

<u> 実際の結果 </u>:

内部エラーが発生します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
