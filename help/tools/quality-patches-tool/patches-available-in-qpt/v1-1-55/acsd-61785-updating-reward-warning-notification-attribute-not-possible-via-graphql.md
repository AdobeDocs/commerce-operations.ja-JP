---
title: 'ACSD-61785: GraphQLの突然変異およびREST API呼び出しを介してreward_warning_notification属性を更新できない'
description: ACSD-61785 パッチを適用して、「reward_warning_notification」属性を更新できないAdobe Commerceの問題を修正します。この問題は、GraphQLの突然変異とREST API呼び出しによって解決されます。
feature: REST, GraphQL, Rewards
role: Admin, Developer
exl-id: 41f40452-4240-4b4a-b1bc-0da23139f19f
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-61785: GraphQLの突然変異およびREST API呼び出しを介してreward_warning_notification属性を更新できない

ACSD-61785 パッチは、GraphQLの突然変異とREST API呼び出しによって`reward_warning_notification`属性を更新できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55がインストールされている場合に利用できます。 パッチ IDはACSD-61785です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`reward_warning_notification`属性の更新は、GraphQLの突然変異およびREST API呼び出しでは実行できません。

<u>複製する手順</u>:

1. *残高の更新を購読*&#x200B;および&#x200B;*ポイントの有効期限に関する通知*&#x200B;について、GraphQLおよびREST API スキーマ/ドキュメントを確認します。

<u>期待される結果</u>:

GraphQLおよびREST APIを使用して、*報酬残高の更新*&#x200B;および&#x200B;*ポイント有効期限のお知らせ*&#x200B;を購読できます。

<u>実際の結果</u>:

GraphQLとREST APIには、この機能がありません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
