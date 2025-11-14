---
title: CSS および JS リソースファイルの最適化
description: 管理またはコマンドラインからAdobe Commerce プロジェクトの CSS ファイルとJavaScript（JS）ファイルを結合して縮小する方法を説明します。
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: 19f874130645fcabe3178a37ec6dedcf75b93afa
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# リソースファイルの最適化

Commerce サイトの応答性を高めるには、CSS およびJavaScript（JS）リソースファイルを最適化し、レンダリングをブロックするリソースを排除します。

- **CSS ファイルと JS ファイルの最適化** - Adobe Commerceで個別のファイルを 1 つのファイルに結合、縮小、バンドルするように設定することで、CSS およびJavaScript（JS）ファイルの読み込みに要する時間を短縮します。
- **レンダリングを妨げるリソースを排除** – 重要な JS および CSS 機能をインラインで配信し、重要でないすべての JS/CSS スタイルを延期することを検討します。 ガイダンスについては、[ レンダリングをブロックするリソースを排除する ](https://web.dev/render-blocking-resources/) を参照してください。

## 影響を受ける製品とバージョン

[ サポートされているすべてのバージョン、2.3 以降 ](../../../release/versions.md):

- クラウドインフラストラクチャー上のAdobe Commerce
- Adobe Commerce オンプレミス

## CSS ファイルの結合または縮小

CSS およびJavaScript（JS）ファイルの読み込みに要する時間は、個別のファイルを結合、縮小および 1 つのファイルにバンドルすることで、短縮できます。

>[!IMPORTANT]
>
>クラウドインフラストラクチャー上のAdobe Commerceは、常に実稼動モードで実行され、それ以外の場合は設定できないので、結合、縮小およびバンドルを有効にするにはコマンドライン方式を使用する必要があります。

デプロイメントで HTTP/2 を使用している場合は、ファイルを結合またはバンドルしないでください。 HTTP/2 では、静的ファイルが非同期でダウンロードされます。 ブラウザーは、ファイルのコンテンツを処理する前に、結合ファイル全体をダウンロードする必要があります。

### Admin の使用

CSS の結合または縮小を有効にするには、[!UICONTROL **管理**/**ストア**/**設定**/**設定**/**詳細**/**開発者**/**CSS 設定**] に移動します。

### コマンドラインの使用

クラウドインフラストラクチャー上のAdobe Commerceで CSS 結合を有効にする手順は次のとおりです。

1. 次のコマンドをローカルで実行します。

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. 変更を `app/etc/config.php` ファイルにコミットし、再デプロイします。

クラウドインフラストラクチャー上のAdobe Commerceで CSS の縮小を有効にする手順は次のとおりです。

1. 次のコマンドをローカルで実行します。

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. 変更を `app/etc/config.php` ファイルにコミットし、再デプロイします。

## JS ファイルの縮小

### Admin の使用

*管理者* サイドバーで、**ストア**/**設定**/**設定**/**詳細**/**開発者**/12}JavaScript設定 **に移動します。**

### コマンドラインの使用

クラウドインフラストラクチャー上のAdobe Commerceで JS の縮小を有効にする手順は次のとおりです。

1. 次のコマンドをローカルで実行します。

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. 変更を `app/etc/config.php` ファイルにコミットし、再デプロイします。

## JS ファイルの結合とバンドル

Commerce管理で結合またはバンドルをオンにできます（結合とバンドルを同時に有効にすることはできません）。[!UICONTROL **ストア**/**設定**/**設定**/**詳細**/**開発者**/10}JavaScript設定 **。**]

コマンドラインからAdobe Commerceの組み込みバンドル（基本バンドル）を有効にすることもできます。

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## 重要でないヘッドスクリプトの遅延

次の設定を有効にして、head セクションに読み込まれた重要でない JavaScript を自動的に遅延させます。[!UICONTROL **ストア**/**設定**/**設定**/**詳細**/**開発者**/10}JavaScript設定 **。**]

このフラグはコマンドラインからも有効にできます。

```bash
php -f bin/magento config:set dev/js/defer_non_critical 1
```

## 追加情報

- [クライアントサイドの最適化設定](../../../performance/configuration.md#client-side-optimization-settings)
- [ ユーザーガイド：リソースファイルの最適化 ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#optimizing-resource-files)
- [ フロントエンド開発者ガイド：CSS マージ、縮小、サイトのパフォーマンス ](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [高度なJavaScriptのバンドル](../../../performance/advanced-js-bundling.md)
