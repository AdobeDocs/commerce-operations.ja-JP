---
title: 'ACSD-56226: READ クエリは、''synchronous_replication''が有効な古いデータを返します'
description: ACSD-56226 パッチを適用すると、Cloud 上のスレーブ接続で「synchronous_replication」フラグが有効になっている場合に、READ クエリが古いデータを返すAdobe Commerceの問題が修正されます。
feature: System
role: Admin, Developer
type: Troubleshooting
source-git-commit: a45cef14b7b37f1112d2ef82adf29b09d63b8e2b
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---


# ACSD-56226：読み取りクエリで、`synchronous_replication` が有効な古いデータが返される

ACSD-56226 パッチは、クラウド上のスレーブ接続で `synchronous_replication` フラグが有効になっている場合に、READ クエリが古いデータを返す問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 がインストールされている場合に使用できます。 パッチ ID は ACSD-56226 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

`synchronous_replication` フラグが有効な場合、READ クエリは古いデータを返します。 これにより、スレーブ接続が無効になり、データベースが過負荷になります。

<u> 再現手順 </u>:

1. クラウドインフラストラクチャー上のAdobe Commerceの環境変数で `MYSQL_USE_SLAVE_CONNECTION` を *true* に設定します。
1. `.magento.env.yaml` に次の設定を追加して、`synchronous_replication` を *false* に設定します。

   ```
   DATABASE_CONFIGURATION:
     _merge: true
     slave_connection:
       default:
         synchronous_replication: false
   ```

1. 再デプロイして、ログイン、買い物かごに追加、注文などのフロントエンドアクションを実行します。

<u> 期待される結果 </u>:

`synchronous_replication` が *false* に設定されている場合、スレーブ接続は有効のままです。

<u> 実際の結果 </u>:

`synchronous_replication` が *false* に設定されている場合、スレーブ接続が無効になり、データベースが過負荷になります。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
