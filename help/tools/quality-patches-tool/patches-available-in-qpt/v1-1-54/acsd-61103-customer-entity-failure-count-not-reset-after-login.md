---
title: 'ACSD-61103: APIを介して顧客が正常にログインした後、エラー数が0にリセットされない'
description: お客様がAPI エンドポイントを介して正常にログインした後、「customer_entity」テーブルのエラー数が0にリセットされないAdobe Commerceの問題を修正するには、ACSD-61103 パッチを適用します。
feature: GraphQL, REST, Customers
role: Admin, Developer
exl-id: 9f5aac1f-c8a3-4255-8ebc-2268283b3384
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# ACSD-61103: APIを介して顧客が正常にログインした後、エラー数が0にリセットされない

ACSD-61103 パッチは、顧客がAPI エンドポイントを介して正常にログインした後、`customer_entity` テーブルの失敗数が0にリセットされない問題を解決します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54がインストールされている場合に利用できます。 パッチ IDはACSD-61103です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

顧客がAPI エンドポイントを介して正常にログインした後でも、`customer_entity` テーブルのエラー数は0にリセットされません。

<u>複製する手順</u>:

1. 顧客アカウントの作成。
1. 誤った詳細を使用して、APIを介して顧客トークンを生成します。
1. 上記のお客様については、`customer_entity` DB テーブルの`failures_num`列を確認してください。
1. 正しい詳細を使用して、APIを介して顧客トークンを生成します。
1. 上記のお客様については、`customer_entity` DB テーブルの`failures_num`列を確認してください。

<u>期待される結果</u>:

正しい資格情報を使用してAPI経由で顧客トークンを生成した後、`failures_num`列を0にリセットする必要があります。

<u>実際の結果</u>:

正しい資格情報を使用してAPIを介して顧客トークンを生成した後、`failures_num`列が0にリセットされません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
