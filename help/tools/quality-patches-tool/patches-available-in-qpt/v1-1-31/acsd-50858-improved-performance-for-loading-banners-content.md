---
title: 'ACSD-50858: バナーのコンテンツを読み込む際のパフォーマンスが向上しました'
description: ACSD-50858 パッチを適用して、過剰なDB クエリとページ読み込み時間の増加により、カート/チェックアウトページでバナーのパフォーマンスが影響を受けるAdobe Commerceの問題を修正します。
feature: Page Content
role: Admin
exl-id: 1b46e51f-70ad-4450-b3a8-173c2e4b7925
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# ACSD-50858: バナーのコンテンツを読み込む際のパフォーマンスが向上しました

ACSD-50858 パッチは、買い物かご/チェックアウトページのバナーパフォーマンスの問題を修正します。*過度のDB クエリとページ読み込み時間の増加*。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.31がインストールされている場合に利用できます。 パッチ IDはACSD-50858です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

バナーのパフォーマンスは、*過度のDB クエリとページ読み込み時間の増加*&#x200B;により、カート/チェックアウトページで影響を受けます。

これは、バナーのコンテンツの読み込み方法をリファクタリングすることで修正され、DB クエリの数が99.99%、ページの読み込み時間が約99%短縮されました。

<u>複製する手順</u>:

1. Adminにログインして、シンプルな製品を作成します。
1. 管理者またはフロントエンドから顧客を作成し、その顧客の配送先住所を追加します。
1. banners.phpを`magento_root/pub/` フォルダーに移動します。
1. `php pub/banners.php` コマンドを使用してバナーを生成します。 シンプルなバナーを1万個、販売ルールを使ってバナーを1千個生成します。
1. フロントエンドで以前に作成した顧客にログインします。
1. 前に作成した商品をカートに追加します。
1. チェックアウトページ（チェックアウト/カート）に移動します。
1. `banner/ajax/load` リクエストの読み込み時間を監視します：

   * `bin/magento dev:query-log:enable`なし
   * `bin/magento dev:query-log:enable`様と

     ```shell
     grep 'magento_banner_content' var/debug/db.log  | wc -l
     ```

<u>期待される結果</u>:

`magento_banner_content`とカート/チェックアウトページの読み込み時間のDB クエリ数が減少しました。

<u>実際の結果</u>:

`magento_banner_content`およびカート/チェックアウトページの読み込み時間のDB クエリ数が増加しました。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 追加情報

<u>banners.php コンテンツ </u>:

```php
\Banner::class);
    $banner->setIsEnabled(
        \Magento\Banner\Model\Banner::STATUS_ENABLED
    )->setName(
        'Test Dynamic Block '.$i
    )->setTypes(
        ''
    )->setStoreContents(
        [0 => 'Dynamic Block Content '.$i]
    )->save();
}

$objectManager = \Magento\Framework\App\ObjectManager::getInstance();

/** @var \Magento\SalesRule\Model\Rule $salesRule */
$salesRule = $objectManager->create(\Magento\SalesRule\Model\Rule::class);
$salesRule->setData(
    [
        'name' => '50% Off ',
        'is_active' => 1,
        'customer_group_ids' => [\Magento\Customer\Model\GroupManagement::NOT_LOGGED_IN_ID],
        'coupon_type' => \Magento\SalesRule\Model\Rule::COUPON_TYPE_NO_COUPON,
        'conditions' => [
            [
                'type' => \Magento\SalesRule\Model\Rule\Condition\Address::class,
                'attribute' => 'base_subtotal',
                'operator' => '>',
                'value' => 0
            ]
        ],
        'simple_action' => 'by_percent',
        'discount_amount' => 50,
        'discount_step' => 0,
        'stop_rules_processing' => 1,
        'website_ids' => [
           1
        ]
    ]
);
$salesRule->save();

for ($i = 0; $i < 1000; $i++) {

    $banner = $objectManager->create(\Magento\Banner\Model\Banner::class);
    $banner->setData(
        [
            'name' => 'Get 50% Off ',
            'is_enabled' => \Magento\Banner\Model\Banner::STATUS_ENABLED,
            'types' => [], /*Any Banner Type*/
            'store_contents' => ['<img src="http://example.com/banner_40_percent_off.png" />'],
            'banner_sales_rules' => [$salesRule->getId()],
        ]
    );
    $banner->save();
}
```

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
