---
title: 'ACSD-60441: V1/customers [!DNL REST] API エンドポイントを使用して顧客を更新すると、エラーがスローされる'
description: バックエンドから生成された統合アクセストークンを使用する場合にV1/customers [!DNL REST] APIを介してお客様を更新するとエラーが発生するAdobe Commerceの問題を修正するには、ACSD-60441 パッチを適用します。
feature: REST, Customers
role: Admin, Developer
exl-id: 3936c065-41a6-4860-8313-e054f9b23ac7
type: Troubleshooting
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-60441: `V1/customers` [!DNL REST] API エンドポイントを使用して顧客を更新すると、エラーがスローされる

ACSD-60441 パッチは、バックエンドから生成された統合アクセストークンを使用する際に`V1/customers` [!DNL REST] APIを介して顧客を更新するとエラーが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50がインストールされている場合に利用できます。 パッチ IDはACSD-60441です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p8

**Adobe Commerce バージョンとの互換性**

* Adobe Commerce（すべてのデプロイメント方式） 2.4.4-p9、2.4.5-p8、2.4.6-p6、2.4.7-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

バックエンドから生成された統合アクセストークンを使用する場合、`V1/customers` [!DNL REST] API エンドポイントを介して顧客を更新すると、エラーがスローされます。

<u>複製する手順</u>:

1. 管理者から統合を作成します。
1. 統合トークンを使用して、[!DNL POST] リクエストを`rest/default/V1/customers/<customer_id>`に送信します。

   ```json
   {
     "customer": {
       "email": "roni_cost@example.com",
       "firstname": "Veronica",
       "lastname": "Costello"
     }
   }
   ```

<u>期待される結果</u>:

顧客データが更新されます。

<u>実際の結果</u>:

次のエラーが表示されます。

```json
{
    "message": "A customer with the same email address already exists in an associated website.",
    "trace": ...
}
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool]  ガイドの](/help/tools/quality-patches-tool/usage.md)>使用状況[!DNL Quality Patches Tool]。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [&#x200B; [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) ガイドの[!UICONTROL Quality Patches Tool]を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) ガイドの「[!DNL Quality Patches Tool] パッチを検索する」を参照してください。
