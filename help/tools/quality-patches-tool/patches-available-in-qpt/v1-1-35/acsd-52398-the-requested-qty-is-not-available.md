---
title: 'ACSD-52398: バンドルされた製品の数量を更新しようとすると、要求数量を使用できません'
description: ACSD-52398 パッチを適用すると、ストアフロントでカートにバンドルされた商品の数量を更新しようとすると、要求された数量が使用できないAdobe Commerceの問題を修正できます。
feature: Shopping Cart, Quotes, Products
role: Admin
exl-id: 75fa5f96-22e7-40a2-8b8a-f44452e5124d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-52398: バンドルされた製品の数量を更新しようとすると、要求数量を使用できません

ACSD-52398 パッチでは、ストアフロントでカートにバンドルされた製品の数量を更新しようとすると、要求された数量が使用できない問題が修正されています。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.35 がインストールされている場合に使用できます。 パッチ ID は ACSD-52398 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ストアフロントでカート内のバンドル製品の数量を更新しようとすると、リクエストされた数量は使用できません。

<u> 再現手順 </u>:

1. 数量 *1* と *10* の 2 つのシンプルな製品を作成します。
1. シンプルな製品を使用して、バンドルされた製品を作成します。
1. バンドルされた製品を買い物かごに追加します。
1. 製品を編集し、*10* 品目が使用可能なオプションの数量を *3* に更新してみてください。

<u> 期待される結果 </u>:

エラーはありません。 このオプションには *10* 個の在庫アイテムがあるので、数量は正常に更新されました。

<u> 実際の結果 </u>:

次のエラーがスローされます。*リクエストされた数量は使用できません*。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
