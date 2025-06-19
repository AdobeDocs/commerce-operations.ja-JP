---
title: MDVA-38728：製品の表示を変更すると、メイン Web サイトの URL が書き換えられます
description: MDVA-38728 パッチを使用すると、2 番目の Web サイトの製品の表示を変更すると、メインの Web サイトの URL が書き換えられる問題が解決されます。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.10 がインストールされている場合に利用できます。 パッチ ID は MDVA-38728。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。
feature: Products
role: Admin
exl-id: c9dfa386-6327-43b6-a977-a29178c64b89
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-38728：製品の表示を変更すると、メイン Web サイトの URL が書き換えられます

MDVA-38728 パッチを使用すると、2 番目の Web サイトの製品の表示を変更すると、メインの Web サイトの URL が書き換えられる問題が解決されます。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.10 がインストールされている場合に使用できます。 パッチ ID は MDVA-38728。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.3-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.2 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

2 番目の web サイトの製品の表示を変更すると、メインの web サイトの URL が書き換えられます。

<u> 再現手順 </u>:

1. 追加の Web サイト、ストア、ストアレビューを作成します。
1. シンプルな製品を作成します。
1. 表示を **個別に表示しない** に設定します。
1. 2 番目の web サイトにのみ製品を割り当てます。
1. その他すべての必須フィールドに入力します。
1. 商品を保存します。
1. MySQL キューを開始します。

   ```mysql
   bin/magento queue:consumers:start product_action_attribute.update &
   bin/magento queue:consumers:start product_action_attribute.website.update &
   ```

1. 製品リストに移動します。
1. 作成した製品を選択し、カタログと検索への一括更新を使用して表示属性を更新します。
1. URL の書き換えを確認します。

<u> 期待される結果 </u>:

書き換えは、製品が割り当てられている 2 番目の web サイトに対して作成されます。

<u> 実際の結果 </u>:

メイン web サイトに対して書き換えが作成されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
