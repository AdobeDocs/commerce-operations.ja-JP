---
title: ACSD-66311：制限付きの管理者ユーザーに対してグリッドの読み込みが遅い
description: ACSD-66311 パッチを適用して、web サイトへのアクセスが制限されている管理者ユーザーに対して、企業がグリッドの読み込みが遅くなるAdobe Commerceの問題を修正します。
role: Admin, Developer
feature: B2B
type: Troubleshooting
exl-id: e470078b-dd10-4b0b-a489-bc88f025fded
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 2%

---

# ACSD-66311：制限付きの管理者ユーザーに対してグリッドの読み込みが遅い

ACSD-66311 パッチは、web サイトへのアクセスが制限されている管理者ユーザーに対して、会社のグリッドの読み込みが遅くなる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69がインストールされている場合に利用できます。 パッチ IDはACSD-66311です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p4 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

企業は、web サイトへのアクセスが制限されている管理者ユーザーに対して、グリッドの読み込みが遅い。

<u>複製する手順</u>:

1. **[!UICONTROL B2B features]**&#x200B;でAdobe Commerceをインストールします。
1. ストア/ビューを含む2つの追加のweb サイト（メイン web サイトに加えて）を作成します。
   * メインサイト（インストール時に作成）
   * Web サイト 2 → Store 2 → StoreView 2
   * Web サイト 3 → Store 3 → StoreView 3
1. **[!UICONTROL Admins in Scope]** ユーザーの役割を作成：
   * スコープ：2つのストア：*メイン Web サイト* + *Web サイト 3/ストア 3*。
   * リソース：*ダッシュボード* + *企業*&#x200B;のみです。
1. 役割&#x200B;**[!UICONTROL Admins in Scope]**&#x200B;を持つ管理者ユーザー（例：**adminscope**）を作成します。
1. 特定の分散顧客および企業データを生成します。
   1. **web サイトに割り当てられた顧客**

      | Web サイト ID | 顧客数 |
      |------------|---------------------|
      | 1 | 600,000 |
      | 2 | 1,500 |
      | 3 | 500 |

   1. 次のクエリを実行して、配布を検証します。

      ```sql
           SELECT website_id, COUNT(*) 
           FROM customer_entity 
           GROUP BY website_id; 
      ```

   1. **企業に割り当てられた顧客**

      | 顧客数 | 企業数 |
      |---------------------|---------------------|
      | 1 | 4,500 |
      | 2 | ~1,000 |
      | ～595k | 1 |

   1. 次のクエリを実行して、配布を検証します。

      ```sql
            SELECT customer_count, COUNT(*) AS number_of_companies
            FROM (
              SELECT company_id, COUNT(customer_id) AS customer_count
              FROM company_advanced_customer_entity
              GROUP BY company_id
            ) AS subquery
            GROUP BY customer_count
            ORDER BY customer_count; 
      ```

1. すべてのデータを再インデックス化して、**customer_grid_flat**&#x200B;にエントリを生成します。
1. **adminscope**&#x200B;としてログインします。
1. **[!UICONTROL Customers]** > **[!UICONTROL Companies]**&#x200B;に移動します。

<u>期待される結果</u>:

ページの読み込み時間は1秒以下です。

<u>実際の結果</u>:

ページの読み込みに14分以上かかります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
