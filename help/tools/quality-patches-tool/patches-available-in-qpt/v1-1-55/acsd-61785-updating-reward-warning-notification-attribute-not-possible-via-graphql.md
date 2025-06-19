---
title: ACSD-61785:GraphQL mutation および REST API 呼び出しを使用して reward_warning_notification 属性を更新することはできません
description: ACSD-61785 パッチを適用すると、Adobe Commerceの問題が修正されます。この問題では、GraphQL ミューテーションおよび REST API 呼び出しを使用して「reward_warning_notification」属性を更新することはできません。
feature: REST, GraphQL, Rewards
role: Admin, Developer
exl-id: 41f40452-4240-4b4a-b1bc-0da23139f19f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61785:GraphQL mutation および REST API 呼び出しを使用して reward_warning_notification 属性を更新することはできません

ACSD-61785 パッチでは、GraphQL mutation および REST API 呼び出しを使用して `reward_warning_notification` 属性を更新することができない問題を修正しています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 がインストールされている場合に使用できます。 パッチ ID は ACSD-61785 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

GraphQL mutation および REST API 呼び出しを使用して `reward_warning_notification` 属性を更新することはできません。

<u> 再現手順 </u>:

1. *バランスの更新を登録* および *ポイントの有効期限に関する通知を登録* については、GraphQLおよび REST API スキーマ/ドキュメントを参照してください。

<u> 期待される結果 </u>:

GraphQLと REST API を介して、*報酬バランスの更新* および *ポイントの有効期限の通知* を購入することができます。

<u> 実際の結果 </u>:

GraphQLと REST API には、この機能はありません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
