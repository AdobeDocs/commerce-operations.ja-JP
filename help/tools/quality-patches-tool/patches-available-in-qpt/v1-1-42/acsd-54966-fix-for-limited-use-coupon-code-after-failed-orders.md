---
title: ACSD-54966：注文が失敗した後にクーポンコードを再利用する問題を修正しました
description: ACSD-54966 パッチを適用して、以前に失敗した注文に続いて、プロモーションやショッピングカートごとに制限されたクーポンコードの再利用を防ぐAdobe Commerceの問題を修正します。
feature: Promotions/Events, Shopping Cart, Orders
role: Admin, Developer
exl-id: e08062e5-62ff-4da6-918f-896af36edccc
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-54966：注文が失敗した後にクーポンコードを再利用する問題を修正しました

ACSD-54966 パッチは、以前に失敗した注文に続いて、顧客ごとに制限されたクーポンコードの再利用を防ぐ問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.42がインストールされている場合に利用できます。 パッチ IDはACSD-54966です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p1
* Adobe Commerce 2.4.7-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.4.5 - 2.4.5-p10、2.4.6 - 2.4.6-p8
* Adobe Commerce:2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

お客様1人につき1回のご利用に限られるクーポンコードは、前回の注文に失敗した後に再利用することはできません。

<u>複製する手順</u>:

1. *[!UICONTROL Uses per Customer]* = *1*&#x200B;のカート価格ルールを設定します。
1. 割り当てられたクーポンコードを使用して購入を進めます。
1. 管理パネルから注文をキャンセルするか、支払い失敗で注文を実行します。
1. 次のコマンドを実行します：`bin/magento queue:consumers:start sales.rule.update.coupon.usage`
1. 同じ顧客に対して、同じクーポンコードを使用して、その後の注文を試みます。

<u>期待される結果</u>:

注文をキャンセルした後、または支払い失敗が発生した場合、顧客は新しい購入のためにクーポンコードを正常に再利用できます。

<u>実際の結果</u>:

お客様はクーポンコードを再利用できません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
