---
title: 'MDVA-44147: [!DNL GraphQL] request が [!UICONTROL Requisition Lists] を返さない'
description: MDVA-44147 パッチは、 [!DNL GraphQL] request が [!UICONTROL Requisition Lists] を返さない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.14 がインストールされている場合に使用できます。 パッチ ID は MDVA-44147。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。
feature: B2B, GraphQL
role: Admin
exl-id: 534c4e45-6521-45c0-ae4e-c60b754f432f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# MDVA-44147:[!DNL GraphQL] 要求が [!UICONTROL Requisition Lists] を返さない

MDVA-44147 パッチは、[!DNL GraphQL] のリクエストが [!UICONTROL Requisition Lists] を返さない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 がインストールされている場合に使用できます。 パッチ ID は MDVA-44147。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

リクエ [!DNL GraphQL] トが [!UICONTROL Requisition Lists] を返しません。

<u> 再現手順 </u>:

1. **ストア**/**設定**/**設定**/**一般**/**B2B 機能** に移動し、**[!UICONTROL Requisition List]** を有効にします。
1. 顧客としてログインし、[[!UICONTROL Requisition List]](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/requisition-lists/requisition-lists) に製品を追加します。
1. [[!UICONTROL Customer Token]](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/generate-token/) を作成します。

   <pre>
    <code class="language-graphql">
    mutation {
      generateCustomerToken(
        email: "test@gmail.com"
        password: "xxxxxxxx"
        ) {
          token
        }
      }
      </code>
      </pre>

1. 次のクエリを使用して、顧客からすべての [!UICONTROL Requisition Lists] を取得します。 値が **の** Authorization`Bearer <customer_token>` ヘッダーを使用します。 詳しくは、開発者向けドキュメントの [ 顧客クエリ ](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/customer/) 記事を参照してください。

   リクエスト :

   <pre>
    <code class="language-graphql">
    query {
      customer {
        requisition_lists(
          pageSize: 20
          ) {
            items {
              uid
              name
              description
              items(pageSize: 20) {
                items {
                  uid
                  product {
                    uid
                    name
                    sku
                    __typename
                  }
                  quantity
                }
                total_pages
              }
            }
            total_count
          }
        }
      }
      </code>
      </pre>

   応答：

   <pre>
    <code class="language-graphql">
    {
      "data": {
        "customer": {
          "requisition_lists": {
            "items": [
            {
              "uid": "MQ==",
              "name": "Name",
              "description": "Description",
              "items": {
                "items": [
                {
                  "uid": "MQ==",
                  "product": {
                    "uid": "MQ==",
                    "name": "Simple 01",
                    "sku": "s00001",
                    "__typename": "SimpleProduct"
                    },
                    "quantity": 1
                  }
                  ],
                  "total_pages": 1
                }
              }
              ],
              "total_count": 1
            }
          }
        }
      }
      </code>
      </pre>

1. 返されたリスト（MQ==）から任意の項目のUIDをコピーし、次のクエリを使用して、UIDでフィルタリングされたリストを取得します。

   <pre>
    <code class="language-graphql">
    query {
      customer {
        requisition_lists(
          pageSize: 20,
          filter: {
            uids: {
              eq: "MQ=="
            }
          }
          ) {
            items {
              uid
              name
              description
              items(pageSize: 20) {
                items {
                  uid
                  product {
                    uid
                    name
                    sku
                    __typename
                  }
                  quantity
                }
                total_pages
              }
            }
            total_count
          }
        }
      }
      </code>
      </pre>

<u> 期待される結果 </u>:

1 つの結果が返されます。

<u> 実際の結果 </u>:

ゼロの結果が返されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) ガイドのの [!DNL Quality Patches Tool] を使用して、Adobe Commerceの問題にパッチが使用可能かどうかを確認します。

[!DNL QPT] で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
