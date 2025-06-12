---
title: ACSD-54972：正規カテゴリ URL が更新されない
description: カテゴリ URL を変更した後、正規カテゴリ URL が更新されないAdobe Commerceの問題を修正するために、ACSD-54972 パッチを適用してください。
feature: Catalog Management, Products, Categories
role: Admin, Developer
exl-id: c4b17c08-9a2b-44a2-925e-f4c5cce7b760
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# ACSD-54972：正規カテゴリ URL が、カテゴリ URL の変更後に更新されない

ACSD-54972 パッチは、カテゴリ URL を変更した後、正規カテゴリ URL が更新されない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43 がインストールされている場合に使用できます。 パッチ ID は ACSD-54972 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

カテゴリ URL を変更した後、正規カテゴリ URL が更新されない。

<u> 再現手順 </u>:

1. **[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Catalog]**/**[!UICONTROL Catalog]**/**[!UICONTROL Search Engine Optimization]** に移動します。

   * Set *[!UICONTROL Use Canonical Link Meta Tag for Categories]*: *はい*

2. カテゴリを作成します（例：*名前*:*カテゴリ 01*、*URL キー*:*category-01*）。
3. 「**[!UICONTROL Create Permanent Redirect for old URL]**」チェックボックスをオンにしたまま、*URL キー* を元の値とは異なる値に更新します。
4. キャッシュをクリーンアップします。
5. フロントエンドの *[!UICONTROL Category Page]* に移動します。
6. ページソースを確認し、*canonical* タグを検索します。

<u> 期待される結果 </u>:

`<link rel="canonical" href="http://127.0.0.1/pub/category-01-new.html" />`

<u> 実際の結果 </u>:

`<link rel="canonical" href="http://127.0.0.1/pub/category-01.html" />`

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
