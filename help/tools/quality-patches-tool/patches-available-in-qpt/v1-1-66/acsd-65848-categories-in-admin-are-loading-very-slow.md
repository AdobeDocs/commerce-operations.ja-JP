---
title: ACSD-65848：管理画面のカテゴリの読み込みが非常に遅い
description: ACSD-65848 パッチを適用して、カテゴリ内の合計製品数がサブセレクトを使用して計算され、カテゴリの読み込み時間が遅くなるAdobe Commerceの問題を修正します。
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
exl-id: 0233db9b-86b1-4320-a566-7e7e207dab84
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-65848：管理画面のカテゴリの読み込みが非常に遅い

ACSD-65848 パッチは、カテゴリ内の合計製品数がサブセレクトを使用して計算され、カテゴリの読み込み時間が遅くなる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66がインストールされている場合に利用できます。 パッチ IDはACSD-65848です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

管理者カテゴリの表示/編集ページでは、読み込み時に大幅な遅延が発生します。 遅延は、サブセレクトクエリに依存する、カテゴリ内の合計製品数の計算に使用される方法によって発生します。 代わりに結合を使用するためにこのロジックをリファクタリングすると、パフォーマンスが向上し、読み込み時間が短縮されます。

<u>複製する手順</u>:

1. バージョン 2.4.8を使用して、新しいAdobe Commerce Cloud インスタンスを作成します。
1. 2,500のカテゴリーと少なくとも10,000の商品を制作する：
   1. プロファイルを編集できるように、`setup/performance-toolkit` ディレクトリを`./var`にコピーします。
   1. `small.xml` プロファイルを開き、2,500のカテゴリと250,000の製品を含めるように更新します（加盟店の設定に合わせて）。
   1. 次のコマンドを実行して、器具を生成します。

      ```shell
      bin/magento 
      setup:performance:generate-fixtures var/setup/performance-toolkit/profiles/ce/small.xml
      ```

1. 商品とカテゴリーを作成したら、すべてのカテゴリーがアンカーとして設定されていることを確認します。 次のSQL クエリを実行します。

   ```sql
   UPDATE catalog_category_entity_int 
   SET value = 1 
   WHERE attribute_id = (
   SELECT attribute_id 
   FROM eav_attribute 
   WHERE attribute_code = 'is_anchor'
   );
   ```

1. 管理パネルで、より詳細なカテゴリ構造を作成します。
   * カテゴリー2をカテゴリー1の下に移動して、ツリーの奥深くにネストします。
1. 次のようなURLを使用して、管理パネルでカテゴリーページを開いてみます。
   `/admin/catalog/category/edit/id/xx/`

<u>期待される結果</u>:

各カテゴリーページは、数秒以内に最初に開きます。

<u>実際の結果</u>:

カテゴリーページを開くには1分以上かかります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
