---
title: ACSD-45781：ストアのフロント検索フィールドがモバイルに表示されない
description: MDVA-45781 パッチを適用すると、ストア フロント検索フィールドがモバイルに表示されない問題が解決されます。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.19 がインストールされている場合に利用できます。 パッチ ID は MDVA-45781。 この問題はAdobe Commerce 2.4.3 で修正されました。
feature: Cache, Native Luma Frontend Development, Search
role: Admin
exl-id: f761461b-2dd0-45d2-b80d-57793f6f0924
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-45781：ストアのフロント検索フィールドがモバイルに表示されない

MDVA-45781 パッチを適用すると、ストア フロント検索フィールドがモバイルに表示されない問題が解決されます。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.19 がインストールされている場合に使用できます。 パッチ ID は MDVA-45781。 この問題はAdobe Commerce 2.4.3 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1 ～ 2.4.1-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ストアフロント検索フィールドがモバイルに表示されない

<u> 再現手順 </u>:

1. Commerce管理者/**ストア**/**設定**/**カタログ**/**カタログ検索** に移動して、次のように設定します。
   * 「レコメンデーションを検索」を有効にして *いいえ*
   * 検索候補を有効にして *いいえ*
1. 「**設定を保存**」ボタンをクリックします。
1. キャッシュをクリーンアップします。
1. 標準の Luma テーマを使用して、モバイルで参照します。
1. 「**検索** ボタンをクリックします。

<u> 期待される結果 </u>:

入力検索フォームが表示されます。

<u> 実際の結果 </u>:

何も起こらない。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
