---
title: 'ACSD-66889: CLI でインベントリの再インデックス中にエラーが発生しました'
description: ACSD-66889 パッチを適用して、インベントリインデクサーの実行中にエラーをトリガーするAdobe Commerceの問題を修正してください。
feature: Inventory
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9631e0864b2ad8fc09734aedd476e96852cd70fb
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---


# ACSD-66889: CLI でインベントリの再インデックス中にエラーが発生しました

ACSD-66889 パッチは、インベントリインデクサーの実行時に発生するエラーを修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 がインストールされている場合に使用できます。 パッチ ID は ACSD-66889 です。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p8

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.5-p13

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

インベントリインデクサーを実行すると、プロセスで非推奨の警告がスローされ、文字列構文が古くなっているために完了できません。

<u> 再現手順 </u>:

1. CLI コマンドを使用してインベントリの再インデックスを実行します。

   ```
   php bin/magento indexer:reindex inventory
   ```

<u> 期待される結果 </u>:

CLI でインベントリインデクサーが正常に再構築されます。

<u> 実際の結果 </u>:

CLI が非推奨（廃止予定）の機能エラーをスローし、インベントリインデックスが *インデックス再作成が必要* 状態のままになる：

```
Deprecated Functionality: Using ${var} in strings is deprecated, use {$var} instead in /home/vendor/magento/module-elasticsearch-catalog-permissions/Model/Adapter/FieldMapper/Product/FieldProvider/FieldName/Resolver/CategoryPermission.php on line 24
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
