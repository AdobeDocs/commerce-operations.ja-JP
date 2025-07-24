---
title: ACSD-65848：管理画面のカテゴリの読み込みに時間がかかる
description: ACSD-65848 パッチを適用すると、カテゴリ内の合計製品数がサブセレクトを使用して計算され、カテゴリの読み込み時間が遅延するAdobe Commerceの問題が修正されます。
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8a614c40a1c0134a0528b74cbd434e7ca96c933a
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---


# ACSD-65848：管理画面のカテゴリの読み込みに時間がかかる

ACSD-65848 パッチでは、カテゴリの合計製品数がサブ選択を使用して計算され、カテゴリの読み込み時間が遅延する問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 がインストールされている場合に使用できます。 パッチ ID は ACSD-65848 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

管理者カテゴリのページの表示/編集で、読み込み時に大幅な遅延が発生する。 遅延は、カテゴリ内の合計製品数の計算に使用されるメソッドによって発生します。これはサブ選択クエリに依存します。 このロジックをリファクタリングして結合を使用すると、パフォーマンスが向上し、読み込み時間が短縮されます。

<u> 再現手順 </u>:

1. バージョン 2.4.8 を使用して新しい Adobe Commerce Cloud インスタンスを作成します。
1. 2,500 のカテゴリと 10,000 以上の製品を作成します。
   1. `setup/performance-toolkit` ディレクトリを `./var` にコピーして、プロファイルを編集できるようにします。
   1. `small.xml` プロファイルを開き、2,500 個のカテゴリと 250,000 個の製品（マーチャントの設定に一致）を含めるように更新します。
   1. 次のコマンドを実行して、器具を生成します。

      ```bash
      bin/magento 
      setup:performance:generate-fixtures var/setup/performance-toolkit/profiles/ce/small.xml
      ```

1. 製品とカテゴリを作成したら、すべてのカテゴリがアンカーとして設定されていることを確認します。 次の SQL クエリを実行します。

   ```sql
   UPDATE catalog_category_entity_int 
   SET value = 1 
   WHERE attribute_id = (
   SELECT attribute_id 
   FROM eav_attribute 
   WHERE attribute_code = 'is_anchor'
   );
   ```

1. 管理パネルで、より深いカテゴリ構造を作成します。
   * カテゴリ 2 をカテゴリ 1 の下に移動し、ツリーの深い方にネストします。
1. 次のような URL を使用して、管理パネルでカテゴリページを開いてみます。
   ```/admin/catalog/category/edit/id/xx/```

<u> 期待される結果 </u>:

各カテゴリページは、数秒以内に最初の試行で開きます。

<u> 実際の結果 </u>:

カテゴリページが開くまで 1 分以上かかります。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
