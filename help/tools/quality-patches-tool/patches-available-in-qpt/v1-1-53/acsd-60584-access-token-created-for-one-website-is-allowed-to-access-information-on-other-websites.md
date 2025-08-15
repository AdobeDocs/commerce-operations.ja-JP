---
title: ACSD-60584：ある web サイト用に作成されたアクセストークンが、他の web サイトの情報にアクセスできます
description: ACSD-60584 パッチを適用すると、ある web サイトのユーザー用に作成されたアクセストークンが、他の web サイトの顧客情報にアクセスしたり変更したりできる問題を修正できます。
feature: Customers, GraphQL
role: Admin, Developer
exl-id: ea30ba92-4b7b-44f9-a1b1-97946061d9e6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-60584：ある web サイト用に作成されたアクセストークンが、他の web サイトの情報にアクセスできます

ACSD-60584 パッチは、ある web サイト上のユーザー用に作成されたアクセストークンが、他の web サイト上の顧客情報にアクセスしたり、変更したりできる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.53 がインストールされている場合に使用できます。 パッチ ID は ACSD-60584 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ある web サイトでユーザー用に作成された API トークンを使用すると、顧客情報へのアクセス、買い物かごの作成、他の web サイト表示での買い物かごへの製品の追加が可能になります。

<u> 再現手順 </u>:

1. **[!DNL Share Customer Accounts configuration]** が **[!UICONTROL Per Website]** に設定されていることを確認します。
1. 追加の *web サイト*、*ストア* および *ストレビュー* を作成します。
1. 前の手順で、メインの *web サイト* と *web サイト* に同じメールを持つ 2 つの顧客を作成します。
1. メイン web サイトの [!DNL GraphQL] を使用して顧客トークンを生成します。
1. 生成されたトークンを使用して、顧客情報を取得する 2 番目の web サイトをヘッダーに含む顧客 **[!DNL GraphQL]** クエリを送信します。
1. 返された結果を確認します。

<u> 期待される結果 </u>:

メインの *web サイト* からのトークンがクエリで使用されているので、メインの *web サイト* からの顧客情報 [!DNL GraphQL] 返されます。

<u> 実際の結果 </u>:

2 番目の Web サイトからの顧客情報が返されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
