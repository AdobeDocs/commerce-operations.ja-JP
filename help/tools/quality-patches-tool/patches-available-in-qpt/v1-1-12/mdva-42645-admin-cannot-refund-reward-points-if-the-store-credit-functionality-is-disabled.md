---
title: 「MDVA-42645：無効なストアクレジットの報酬ポイントを管理者が払い戻すことができない」
description: MDVA-42645 パッチは、ストアクレジット機能が無効な場合に管理者が報酬ポイントを返金できない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches） 1.1.12 がインストールされている場合に利用できます。 パッチ ID は MDVA-42645。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。
feature: Admin Workspace, Orders, Rewards, Returns
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-42645：無効な店舗クレジットの報酬ポイントを払い戻すことができません

MDVA-42645 パッチは、ストアクレジット機能が無効な場合に管理者が報酬ポイントを返金できない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)1.1.12 がインストールされている場合に使用できます。 パッチ ID は MDVA-42645。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ストアクレジット機能が無効になっている場合、管理者は報酬ポイントを返金できません。

<u> 再現手順 </u>:

1. シンプルな製品を作成します。
1. 新しい顧客アカウントを作成し、報酬ポイントをいくつか追加します。
1. **ストア**/設定/**設定**/**カスタマー**/**カスタマー設定**/**ストアクレジットオプション** に移動して、ストアクレジット機能を無効にします。
1. 報酬ポイントが割り当てられている顧客としてログインします。
1. 商品を買い物かごに追加し、チェックアウトに移動します。
1. 支払いセクションの報酬ポイントを使用して注文します。
1. 管理者で注文を開き、注文を請求します。
1. **クレジットメモ** リンクをクリックして、新しいクレジットメモを作成します。
1. 下部の「返金報酬ポイント」オプションにチェックマークを入れ、**オフラインで返金** をクリックします。

<u> 期待される結果 </u>:

* クレジット・メモが正常に作成されます。
* 報酬ポイントは正常に返金されます。

<u> 実際の結果 </u>:

次のエラーメッセージが表示されます。*注文額を超えるストアクレジットを使用することはできません。*

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。