---
title: 'ACSD-53176: ''次の 1 つ''条件を含む製品ルールが一致しません'
description: ACSD-53176 パッチを適用すると、関連する商品ルールの「is one of」条件が「Products to Match」で正しく機能しないAdobe Commerceの問題を修正できます。
feature: Marketing Tools
role: Admin
exl-id: 8260c6ac-3ca2-4361-9e36-a8a58468fa95
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-53176:`is one of` 条件を含む製品ルールが一致しません

ACSD-53176 パッチを使用すると、関連する製品ルール `is one of` 条件が **Products to Match** に対して正しく機能しない問題を修正できます。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.36 がインストールされている場合に使用できます。 パッチ ID は ACSD-53176 です。 この問題はAdobe Commerce 2.4.7 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 ～ 2.4.5-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

関連する製品ルール `is one of` 条件が **一致する製品** で正しく機能しません。

<u> 再現手順 </u>:

1. 3 ～ 4 個の製品を作成します。
1. 新しい関連製品ルールを作成します。

   複数の製品に一致するルールを設定します。
   * `SKU is one of "S1,S2".`

   2 つ以上の項目を表示するようにルールを設定します。
   * `Product SKU is one of constant value "S2,S3".`

1. ストアフロントで S1 製品を開きます。

<u> 期待される結果 </u>:

関連製品「S2」、「S3」を製品ページ「S1」、「S2」の両方に表示する。

<u> 実際の結果 </u>:

関連製品が製品ページに表示されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
