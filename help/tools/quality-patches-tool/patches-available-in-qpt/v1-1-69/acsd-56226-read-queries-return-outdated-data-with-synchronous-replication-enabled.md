---
title: 'ACSD-56226: READ クエリで「synchronous_replication」が有効になっている古いデータが返される'
description: ACSD-56226 パッチを適用して、Cloud上のスレーブ接続に「synchronous_replication」フラグが有効になっている場合にREAD クエリが古いデータを返すAdobe Commerceの問題を修正します。
feature: System
role: Admin, Developer
type: Troubleshooting
exl-id: 5ad0e884-decb-4e09-b5b3-b38a9953a4b8
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-56226: READ クエリで、`synchronous_replication`が有効になっている古いデータが返される

ACSD-56226 パッチは、クラウド上のスレーブ接続に`synchronous_replication` フラグが有効になっている場合にREAD クエリが古いデータを返す問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69がインストールされている場合に利用できます。 パッチ IDはACSD-56226です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

読み取りクエリは、`synchronous_replication` フラグが有効になっている場合に古いデータを返します。 これにより、スレーブ接続が無効になり、データベースの過負荷が発生します。

<u>複製する手順</u>:

1. クラウドインフラストラクチャ上のAdobe Commerceの環境変数で、`MYSQL_USE_SLAVE_CONNECTION`を&#x200B;*true*&#x200B;に設定します。
1. 次の設定を`.magento.env.yaml`に追加して、`synchronous_replication`を&#x200B;*false*&#x200B;に設定します。

   ```text
   DATABASE_CONFIGURATION:
     _merge: true
     slave_connection:
       default:
         synchronous_replication: false
   ```

1. ログイン、カートへの追加、注文など、フロントエンドのアクションを再デプロイして実行します。

<u>期待される結果</u>:

`synchronous_replication`が&#x200B;*false*&#x200B;に設定されている場合、スレーブ接続は引き続き有効です。

<u>実際の結果</u>:

`synchronous_replication`が&#x200B;*false*&#x200B;に設定されている場合、スレーブ接続は無効になり、データベースのオーバーロードが発生します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
