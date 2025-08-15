---
title: ACSD-45754：クーポンを買い物かごに適用した後、報酬ポイントが追加されない
description: ACSD-45754 パッチを使用すると、クーポンを買い物かごに適用した後に報酬ポイントが追加されない問題を解決できます。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.18 がインストールされている場合に利用できます。 パッチ ID は ACSD-45754 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。
feature: Orders, Rewards, Shopping Cart
role: Admin
exl-id: 02f3bfc4-440b-4d77-adf5-0824d1b21073
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-45754：クーポンを買い物かごに適用した後、報酬ポイントが追加されない

ACSD-45754 パッチを使用すると、クーポンを買い物かごに適用した後に報酬ポイントが追加されない問題を解決できます。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.18 がインストールされている場合に使用できます。 パッチ ID は ACSD-45754 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.1 ～ 2.4.5

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

クーポンを買い物かごに適用した後、報酬ポイントは追加されません。

<u> 前提条件 </u>:

PayPal の支払い方法が設定されています。

<u> 再現手順 </u>:

1. **ストア**/**その他の設定**/**報酬為替レート** に移動して、報酬ポイントの為替レートを作成します。
1. ログインした顧客に 100 の報酬ポイントを適用するクーポンコードを使用して、買い物かご価格ルールを作成します。
1. PayPal とクーポンコードを使用して、ログインした顧客として製品をチェックアウトします。
1. 管理者の顧客アカウントで報酬ポイント履歴を確認します。

<u> 期待される結果 </u>:

報酬ポイントは、価格ルールに従って顧客に追加されます。

<u> 実際の結果 </u>:

報酬ポイントは顧客に追加されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
