---
title: ACSD-65127：実稼動モードでのJavaScriptの縮小により、ブラウザーで [!DNL TinyMCE] 6 エラーが発生する
description: ACSD-65127 パッチを適用して、Adobe Commerceの問題を修正します。実稼動モードでJavaScriptの縮小を有効にすると、 [!DNL TinyMCE] 6がブラウザーコンソールでエラーが発生し、機能とユーザーエクスペリエンスに影響が及ぶ場合があります。
feature: Page Builder, Page Content
role: Admin, Developer
exl-id: c878d5a4-8059-4bfc-93a8-0a9606e866fc
type: Troubleshooting
source-git-commit: d98a8f60d2bcd818ae50d754bb96a2bf0becb810
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-65127：実稼動モードでJavaScriptを縮小すると、ブラウザーで[!DNL TinyMCE] 6個のエラーが発生する

ACSD-65127 パッチでは、実稼動モードでJavaScriptの縮小を有効にすると、[!DNL TinyMCE] 6でブラウザーコンソールにエラーが発生し、機能とユーザーエクスペリエンスに影響が及ぶ問題が修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64がインストールされている場合に利用できます。 パッチ IDはACSD-65127です。 この問題は、Adobe Commerce 2.4.8で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: パッチの検索](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) ページで互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

実稼動モードでJavaScriptの縮小を有効にすると、[!DNL TinyMCE] 6でブラウザーコンソールにエラーが発生し、機能とユーザーエクスペリエンスに影響が及びます。

<u>複製する手順</u>:

1. 次のコマンドを実行して、設定を設定します。

```
bin/magento config:set --lock-config dev/js/minify_files 1
bin/magento config:set --lock-config dev/js/enable_js_bundling 1
bin/magento config:set --lock-config dev/js/merge_files 1
```

>[!NOTE]
>
>Adobeでは、**[!UICONTROL Merge JavaScript Files]**&#x200B;を有効にすることはお勧めしません。 [JS ファイルの結合（推奨されません） &#x200B;](/help/implementation-playbook/best-practices/development/optimize-css-js-files.md#merge-js-files)を参照してください。

1. 実稼動モードを有効にします。

```
bin/magento deploy:mode:set production
```

1. 管理者サイドバーで、**[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;に移動します。 リストされている製品の&#x200B;**[!UICONTROL Edit]**&#x200B;をクリックし、**[!UICONTROL Content]**&#x200B;までスクロールして、**[!UICONTROL Show Editor]**&#x200B;を選択します。

<u>期待される結果</u>:

ブラウザーコンソールにJS エラーがありません。

<u>実際の結果</u>:

js *のブラウザーコンソールで* 404`tiny_mce_6/plugins/help/js/i18n/keynav/en.js`件のエラーが発生しました。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool]  ガイドの](/help/tools/quality-patches-tool/usage.md)>使用状況[!DNL Quality Patches Tool]
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > Commerce クラウドインフラストラクチャ上のパッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」ガイド

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール
