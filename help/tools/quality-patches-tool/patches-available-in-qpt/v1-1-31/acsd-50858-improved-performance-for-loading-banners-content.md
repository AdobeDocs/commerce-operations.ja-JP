---
title: ACSD-50858：バナーのコンテンツを読み込むパフォーマンスの向上
description: ACSD-50858 パッチを適用すると、DB クエリが過剰になり、ページの読み込み時間が長くなることで、買い物かごやチェックアウトページでバナーのパフォーマンスが影響を受けるAdobe Commerceの問題を修正できます。
feature: Page Content
role: Admin
exl-id: 1b46e51f-70ad-4450-b3a8-173c2e4b7925
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# ACSD-50858：バナーのコンテンツを読み込むパフォーマンスの向上

ACSD-50858 パッチは、買い物かごと/チェックアウトページのバナーのパフォーマンスの問題（*DB クエリが多すぎて、ページの読み込み時間が長い* を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.31 がインストールされている場合に使用できます。 パッチ ID は ACSD-50858 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

バナーのパフォーマンスは、（DB クエリが過剰で、ページの読み込み時間が長い *ことが原因で、買い物かご/チェックアウトページに影響を与え* す。

これは、バナーのコンテンツの読み込み方法をリファクタリングすることで修正されました。これにより、DB クエリの数が 99.99% 削減され、ページの読み込み時間が約 99% 短縮されました。

<u> 再現手順 </u>:

1. 管理者にログインし、シンプルな製品を作成します。
1. 管理者またはフロントエンドから顧客を作成し、その配送先住所を追加します。
1. banners.php を `magento_root/pub/` フォルダーに移動します。
1. `php pub/banners.php` コマンドを使用してバナーを生成します。 1 万枚の簡易バナーと、販売ルール付きの 1,000 枚のバナーを生成します。
1. フロントエンドで以前に作成した顧客にログインします。
1. 前に作成した商品を買い物かごに追加します。
1. チェックアウトページ（チェックアウト/カート）に移動します。
1. `banner/ajax/load` リクエストの読み込み時間を監視します。

   * `bin/magento dev:query-log:enable` なし
   * （`bin/magento dev:query-log:enable` を使用）

     ```
     grep 'magento_banner_content' var/debug/db.log  | wc -l
     ```

<u> 期待される結果 </u>:

買い物かごやチェックアウトページの読み込み時間に対する DB クエリ数 `magento_banner_content` 減少。

<u> 実際の結果 </u>:

買い物かごやチェックアウトページの読み込み時間に対する DB クエリ数の増加 `magento_banner_content`。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

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

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
