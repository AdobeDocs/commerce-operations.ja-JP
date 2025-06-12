---
title: MDVA-44703：注文レポートの注文合計が正しく計算されない
description: MDVA-44703 パッチは、制限された管理者ユーザーに対して、注文レポート内の注文合計が誤って計算される問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.16 がインストールされている場合に利用できます。 パッチ ID は MDVA-44703。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。
feature: Orders
role: Admin
exl-id: bdd38ba6-f282-4026-8f65-b76543859123
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-44703：注文レポートの注文合計が正しく計算されない

MDVA-44703 パッチは、制限された管理者ユーザーに対して、注文レポート内の注文合計が誤って計算される問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.16 がインストールされている場合に使用できます。 パッチ ID は MDVA-44703。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 ～ 2.4.4

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

注文レポートの注文合計が、制限された管理者ユーザーに対して誤って計算されます。

<u> 再現手順 </u>:

1. 2 つのストアを持つ追加の web サイトを作成します。
1. 新しい web サイトへのアクセス権のみを持つ、制限付きの管理者ユーザーを作成します。
1. 制限付きの管理者ユーザーとしてログインします。
1. 合計が異なる 2 つの注文を作成し、新規店舗ごとに 1 つずつ作成します。
1. 注文の請求書を作成します。
1. **レポート**/**売上** に移動し、**注文レポート** を開きます。
1. 統計を更新します。
1. 各ストアのレポートを参照してください。

<u> 期待される結果 </u>:

売上合計は、各店舗の注文金額に対応しています。

<u> 実際の結果 </u>:

サイト全体の集計売上高は、店舗ごとに表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
