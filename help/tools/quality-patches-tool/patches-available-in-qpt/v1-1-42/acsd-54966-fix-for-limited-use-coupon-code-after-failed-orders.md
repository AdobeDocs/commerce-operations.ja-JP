---
title: ACSD-54966：注文が失敗した後のクーポンコードの再利用を修正
description: 以前に失敗した注文に続いて、プロモーションや買い物かごごとに制限されているクーポンコードの再利用を防ぐAdobe Commerceの問題を修正するために ACSD-54966 パッチを適用してください。
feature: Promotions/Events, Shopping Cart, Orders
role: Admin, Developer
exl-id: e08062e5-62ff-4da6-918f-896af36edccc
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-54966：注文が失敗した後のクーポンコードの再利用を修正

ACSD-54966 パッチは、以前に失敗した注文の後、顧客ごとに制限されているクーポンコードの再利用を妨げる問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42 がインストールされている場合に使用できます。 パッチ ID は ACSD-54966 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p1
* Adobe Commerce 2.4.7-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.5-p10、2.4.6 ～ 2.4.6-p8
* Adobe Commerce:2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

クーポンコードは、お客様ごとの 1 回の使用に制限されており、以前の注文が失敗した後で再利用することはできません。

<u> 再現手順 </u>:

1. *[!UICONTROL Uses per Customer]* = *1* の買い物かご価格ルールを設定します。
1. 割り当てられたクーポンコードを使用して購入を行います。
1. 管理パネルから注文をキャンセルするか、支払いに失敗して注文を実行します。
1. 次のコマンドを実行します。`bin/magento queue:consumers:start sales.rule.update.coupon.usage`
1. 同じ顧客に同じクーポンコードを使用して、後続の注文を試みます。

<u> 期待される結果 </u>:

注文をキャンセルした後、または支払いエラーが発生した後、顧客は新しい購入のためにクーポンコードを正常に再利用できます。

<u> 実際の結果 </u>:

お客様はクーポンコードを再利用できません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
