---
title: 'ACSD-65540: company_structureの更新でREGEXP_LIKE関数が見つからなかったためにSQL エラーが発生する'
description: company_structureの更新でREGEXP_LIKE関数が見つからなかったためにSQL エラーが発生するAdobe Commerceの問題を修正するには、ACSD-65540 パッチを適用します。
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: a3e60742-60d4-41e3-93c3-506cc5a1c4a3
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# ACSD-65540: `company_structure`件の更新で`REGEXP_LIKE`関数が見つからなかったため、SQL エラーが発生しました

ACSD-65540 パッチは、`company_structure`個の更新で`REGEXP_LIKE`機能が欠落しているため、SQL エラーが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64がインストールされている場合に利用できます。 パッチ IDはACSD-65540です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce B2B （すべてのデプロイメント方法） 1.5.2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce B2B （すべてのデプロイメント方法） 1.5.2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`company_structure`件の更新で`REGEXP_LIKE`関数が見つからないため、SQL構文エラーが発生します。

<u>複製する手順</u>:

1. [!DNL B2B]をバージョン 1.5.2に更新します。
1. 次のコマンドを実行します。

```shell
bin/magento setup:upgrade
```

<u>期待される結果</u>:

アップグレードが正常に完了しました。

<u>実際の結果</u>:

```text
Unable to apply data patch Magento\Company\Setup\Patch\Data\SetCompanyForStructure for module Magento_Company. Original exception message: SQLSTATE[42000]: Syntax error or access violation: 1305 FUNCTION REGEXP_LIKE does not exist, query was: UPDATE `company_structure` SET `company_id` = ? WHERE (REGEXP_LIKE(path, '^331(/.+)?$'))
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
