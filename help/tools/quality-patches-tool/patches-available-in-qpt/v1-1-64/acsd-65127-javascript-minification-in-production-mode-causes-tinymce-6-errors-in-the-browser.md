---
title: ACSD-65127：実稼動モードでJavaScriptを縮小すると、ブラウザーで  [!DNL TinyMCE] 6 エラーが発生する
description: ACSD-65127 パッチを適用すると、実稼動モードでAdobe Commerceの縮小を有効にすると  [!DNL TinyMCE] 6 でブラウザーコンソールにエラーが発生し、機能とユーザーエクスペリエンスに影響を与えるJavaScriptの問題が修正されます。
feature: Page Builder, Page Content
role: Admin, Developer
exl-id: c878d5a4-8059-4bfc-93a8-0a9606e866fc
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-65127：実稼動モードでJavaScriptを縮小すると、ブラウザーで [!DNL TinyMCE]6 個のエラーが発生する

ACSD-65127 パッチでは、実稼動モードでJavaScriptの縮小を有効にすると、[!DNL TinyMCE] 6 でブラウザーコンソールでエラーが発生し、機能とユーザーエクスペリエンスに影響を与える問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 がインストールされている場合に使用できます。 パッチ ID は ACSD-65127 です。 この問題はAdobe Commerce 2.4.8 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがお使いのAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: パッチを検索 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) ページで互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

実稼動モードでJavaScriptの縮小を有効にすると、[!DNL TinyMCE] 6 でブラウザーコンソールでエラーが発生し、機能とユーザーエクスペリエンスに影響を与えました。

<u> 再現手順 </u>:

1. 次のコマンドを実行して、設定を指定します。

```
bin/magento config:set --lock-config dev/js/minify_files 1
bin/magento config:set --lock-config dev/js/enable_js_bundling 1
bin/magento config:set --lock-config dev/js/merge_files 1
```

1. 実稼動モードを有効にします。

```
bin/magento deploy:mode:set production
```

1. 管理者サイドバーで、**[!UICONTROL Catalog]**/**[!UICONTROL Products]** に移動します。 リストに表示されている製品の **[!UICONTROL Edit]** をクリックし、**[!UICONTROL Content]** までスクロールダウンして **[!UICONTROL Show Editor]** を選択します。

<u> 期待される結果 </u>:

ブラウザーコンソールに JS エラーはありません。

<u> 実際の結果 </u>:

*404* js `tiny_mce_6/plugins/help/js/i18n/keynav/en.js` のブラウザーコンソールのエラー。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
