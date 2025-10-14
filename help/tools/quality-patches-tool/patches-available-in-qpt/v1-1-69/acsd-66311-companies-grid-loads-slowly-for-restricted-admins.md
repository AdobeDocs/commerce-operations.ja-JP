---
title: ACSD-66311：制限付き管理者ユーザーの会社グリッドの読み込みに時間がかかる
description: ACSD-66311 パッチを適用すると、web サイトへのアクセスが制限された管理者ユーザーのAdobe Commerceで、会社のグリッドの読み込みに時間がかかる問題を修正できます。
role: Admin, Developer
feature: B2B
type: Troubleshooting
exl-id: e470078b-dd10-4b0b-a489-bc88f025fded
source-git-commit: 3337907b1893260d6cb18b1c4fbf45dfa1f3d6d5
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 2%

---

# ACSD-66311：制限付き管理者ユーザーの会社グリッドの読み込みに時間がかかる

ACSD-66311 パッチは、web サイトへのアクセスが制限された管理者ユーザーの場合、会社のグリッドの読み込みに時間がかかる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 がインストールされている場合に使用できます。 パッチ ID は ACSD-66311 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p4 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

Web サイトへのアクセスが制限された管理者ユーザーの場合、会社のグリッドの読み込みに時間がかかる。

<u> 再現手順 </u>:

1. **[!UICONTROL B2B features]** と共にAdobe Commerceをインストールします。
1. ストア/ビューを使用して、（メイン web サイトに加えて） 2 つの追加の web サイトを作成します。
   * メイン Web サイト （インストール時に作成）
   * Website 2 → Store 2 → StoreView 2
   * Website 3 → Store 3 → StoreView 3
1. **[!UICONTROL Admins in Scope]** のユーザーロールを作成します。
   * 範囲：2 つのストアのみ：*メイン web サイト* + *web サイト 3/ストア 3*。
   * リソース：*ダッシュボード* + *会社* のみ。
1. **[!UICONTROL Admins in Scope]** の役割を持つ管理者ユーザー（例：**adminscope** を作成します。
1. 特定の分散顧客および会社データを生成します。
   1. **Web サイトに割り当てられている顧客**

      | Web サイト ID | 顧客の数 |
      |------------|---------------------|
      | 1 | 600,000 |
      | 2 | 1,500 |
      | 3 | 500 |

   1. 次のクエリを実行して、配布を検証します。

      ```
           SELECT website_id, COUNT(*) 
           FROM customer_entity 
           GROUP BY website_id; 
      ```

   1. **事業者に係る顧客**

      | 顧客の数 | 企業数 |
      |---------------------|---------------------|
      | 1 | 4,500 |
      | 2 | ～1,000 |
      | ～595k | 1 |

   1. 次のクエリを実行して、配布を検証します。

      ```
            SELECT customer_count, COUNT(*) AS number_of_companies
            FROM (
              SELECT company_id, COUNT(customer_id) AS customer_count
              FROM company_advanced_customer_entity
              GROUP BY company_id
            ) AS subquery
            GROUP BY customer_count
            ORDER BY customer_count; 
      ```

1. すべてのデータのインデックスを再作成して、**customer_grid_flat** にエントリを生成します。
1. **adminscope** としてログインします。
1. **[!UICONTROL Customers]**/**[!UICONTROL Companies]** に移動します。

<u> 期待される結果 </u>:

ページは 1 秒未満で読み込まれます。

<u> 実際の結果 </u>:

ページの読み込みに 14 分以上かかります。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
