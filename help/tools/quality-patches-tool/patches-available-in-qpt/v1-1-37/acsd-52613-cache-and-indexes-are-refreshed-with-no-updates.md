---
title: 'ACSD-52613: キャッシュとインデックスが更新されずに更新される'
description: ACSD-52613 パッチを適用して、 [!DNL REST API]までに「Inventory_source」項目に更新が行われない場合にキャッシュとインデックスが更新されるAdobe Commerceの問題を修正します。
feature: REST
role: Admin
exl-id: 18878161-da4e-4d6e-9f58-706519f837f8
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# ACSD-52613：更新なしでキャッシュとインデックスが更新される

ACSD-52613 パッチは、[!DNL REST API]によって`Inventory_source`個の項目に更新が行われない場合にキャッシュとインデックスが更新されるAdobe Commerceの問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.37がインストールされている場合に利用できます。 パッチ IDはACSD-52613です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

キャッシュとインデックスは、[!DNL REST API]によって`Inventory_source` アイテムに更新が行われない場合に更新されます。

<u>前提条件</u>:

インストール済みの在庫モジュール

<u>複製する手順</u>:

1. 開発者モードを`debug.log`に切り替えます。
1. 100個の製品を含むインポートファイルを準備 – import.csv:

   ```text
   sku    name    product_type    attribute_set_code    price
   test_sku_1    test_sku_1    simple    Default    10
   test_sku_2    test_sku_2    simple    Default    10
   ...
   test_sku_100    test_sku_100    simple    Default    10
   ```

1. `import.csv`から製品をインポート
1. **test_stock**&#x200B;および&#x200B;**test_source**&#x200B;という新しい在庫とソースを作成します。
1. Web サイトに新しい在庫を割り当て、在庫にソースを割り当てます。
1. すべてのアクセス権を持つ新しい統合を作成し、それをアクティブ化してアクセストークンをコピー&amp;ペーストします。
1. **ストア** > **構成** > **サービス** > **Oauth** > **消費者設定**&#x200B;に移動し、**OAuth アクセストークンをスタンドアロンのベアラートークンとして使用することを許可する**&#x200B;を有効にします。
1. キャッシュをフラッシュします。
1. インデックスを&#x200B;**スケジュール別に更新**&#x200B;として設定
1. API リクエストの実行

   `POST ../rest/V1/inventory/source-items`

   これを体として使う

   ```json
   {
    "sourceItems": [
        {
            "sku": "test_sku_1",
            "source_code": "test_source",
            "quantity": 24,
            "status": 1
        },
        {
            "sku": "test_sku_2",
            "source_code": "test_source",
            "quantity": 50,
            "status": 1
        },
        {
            "sku": "test_sku_3",
            "source_code": "test_source",
            "quantity": 50,
            "status": 1
        },
        {
            "sku": "test_sku_4",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_5",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_6",
            "source_code": "test_source",
            "quantity": 19,
            "status": 1
        },
        {
            "sku": "test_sku_7",
            "source_code": "test_source",
            "quantity": 50,
            "status": 1
        },
        {
            "sku": "test_sku_8",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_9",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_10",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_11",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_12",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_13",
            "source_code": "test_source",
            "quantity": 50,
            "status": 1
        },
        {
            "sku": "test_sku_14",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_15",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_16",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_17",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_18",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_19",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_20",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_21",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_22",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_23",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_24",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_25",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_26",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_27",
            "source_code": "test_source",
            "quantity": 13,
            "status": 1
        },
        {
            "sku": "test_sku_28",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_29",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_30",
            "source_code": "test_source",
            "quantity": 1,
            "status": 1
        },
        {
            "sku": "test_sku_31",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_32",
            "source_code": "test_source",
            "quantity": 1,
            "status": 1
        },
        {
            "sku": "test_sku_33",
            "source_code": "test_source",
            "quantity": 49,
            "status": 1
        },
        {
            "sku": "test_sku_34",
            "source_code": "test_source",
            "quantity": 12,
            "status": 1
        },
        {
            "sku": "test_sku_35",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_36",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_37",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_38",
            "source_code": "test_source",
            "quantity": 10,
            "status": 1
        },
        {
            "sku": "test_sku_39",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_40",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_41",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_42",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_43",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_44",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_45",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_46",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_47",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_48",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_49",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_50",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_51",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_52",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_53",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_54",
            "source_code": "test_source",
            "quantity": 1,
            "status": 1
        },
        {
            "sku": "test_sku_55",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_56",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_57",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_58",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_59",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_60",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_61",
            "source_code": "test_source",
            "quantity": 16,
            "status": 1
        },
        {
            "sku": "test_sku_62",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_63",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_64",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_65",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_66",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_67",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_68",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_69",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_70",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_71",
            "source_code": "test_source",
            "quantity": 16,
            "status": 1
        },
        {
            "sku": "test_sku_72",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_73",
            "source_code": "test_source",
            "quantity": 3,
            "status": 1
        },
        {
            "sku": "test_sku_74",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_75",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_76",
            "source_code": "test_source",
            "quantity": 50,
            "status": 1
        },
        {
            "sku": "test_sku_77",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_78",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_79",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_80",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_81",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_82",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_83",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_84",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_85",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_86",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_87",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_88",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_89",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_90",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_91",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_92",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_93",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_94",
            "source_code": "test_source",
            "quantity": 3,
            "status": 1
        },
        {
            "sku": "test_sku_95",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_96",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_97",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_98",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_99",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_100",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        }
    ]
   }
   ```

1. `var/log`からすべてのログを削除
1. [!DNL REST API] リクエストを再度実行します。
1. `var/log/debug.log`を確認してください。

<u>期待される結果</u>:

キャッシュをクリーニングしないでください。また、インデックスは何も変更されていないため、2回目の実行後に実行しないでください。

<u>実際の結果</u>:

`var/log/debug.log`には、キャッシュ クリアに関連するエントリが含まれています。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
