---
title: 'ACSD-66889: CLIでインベントリの再インデックス中にエラーが発生する'
description: ACSD-66889 パッチを適用して、インベントリインデクサーの実行中にエラーがトリガーするAdobe Commerceの問題を修正します。
feature: Inventory
role: Admin, Developer
type: Troubleshooting
exl-id: 289bd211-99f5-489e-9005-58c711ef128e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%
---
# ACSD-66889: CLIでインベントリの再インデックス中にエラーが発生する

ACSD-66889 パッチは、インベントリインデクサーの実行時に発生するエラーを修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68がインストールされている場合に利用できます。 パッチ IDはACSD-66889です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p8

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.5-p13

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

インベントリインデクサーを実行すると、古い文字列構文が原因で非推奨警告がスローされ、処理を完了できません。

<u>複製する手順</u>:

1. CLI コマンドを使用してインベントリのインデックス再作成を実行します。

   ```shell
   php bin/magento indexer:reindex inventory
   ```

<u>期待される結果</u>:

CLIは、インベントリインデクサーを正常に再構築します。

<u>実際の結果</u>:

CLIで非推奨の機能エラーがスローされ、インベントリ インデックスは&#x200B;*インデックスが必須*&#x200B;状態のままになります。

```shell
Deprecated Functionality: Using ${var} in strings is deprecated, use {$var} instead in /home/vendor/magento/module-elasticsearch-catalog-permissions/Model/Adapter/FieldMapper/Product/FieldProvider/FieldName/Resolver/CategoryPermission.php on line 24
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
