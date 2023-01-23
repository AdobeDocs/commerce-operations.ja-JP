---
title: CSS および JS リソースファイルの最適化
description: Adobe Commerceプロジェクトの CSS ファイルと JavaScript(JS) ファイルを管理者またはコマンドラインから結合および縮小する方法について説明します。
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: e6e8a2d7ef059265dbcbfcd6be117828a639f6d6
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# リソースファイルの最適化

よりレスポンシブな Commerce サイトの場合は、CSS および JavaScript(JS) リソースファイルを最適化して、レンダリングブロックリソースを排除します。

- **CSS および JS ファイルの最適化** — 個別のファイルを 1 つのファイルに結合、縮小、バンドルするようにAdobe Commerceを設定することで、CSS ファイルと JavaScript(JS) ファイルの読み込みに要する時間を短縮できます。
- **レンダリングブロックリソースの排除** — 重要な JS および CSS 機能をインラインで提供し、重要でないすべての JS/CSS スタイルについて言及することを検討します。 ガイダンスについては、 [レンダリングブロックリソースの排除](https://web.dev/render-blocking-resources/).

## 影響を受ける製品およびバージョン

[サポート対象のすべてのバージョン（2.3 以降）](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure
- Adobe Commerceオンプレミス
- Magento Open Source

## CSS ファイルの結合または縮小

個別のファイルを 1 つのファイルに結合、縮小およびバンドルすることで、CSS ファイルと JavaScript(JS) ファイルの読み込みに要する時間を短縮できます。

>[!IMPORTANT]
>
>クラウドインフラストラクチャ上のAdobe Commerceは、常に実稼動モードで動作し、それ以外の設定はできないので、コマンドラインメソッドを使用して結合、縮小、バンドルを有効にする必要があります。

### 管理者の使用

CSS の結合または縮小を有効にするには、 [!UICONTROL **管理者** > **ストア** > **設定** > **設定** > **詳細** > **開発者** > **CSS 設定**].

### コマンドラインの使用

クラウドインフラストラクチャ上のAdobe Commerceで CSS 結合を有効にするには：

1. このコマンドをローカルで実行します。

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. 変更をにコミット `app/etc/config.php` ファイルを作成し、再デプロイします。

クラウドインフラストラクチャ上のAdobe Commerceで CSS 縮小を有効にするには：

1. このコマンドをローカルで実行します。

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. 変更をにコミット `app/etc/config.php` ファイルを作成し、再デプロイします。

## JS ファイルの縮小

### 管理者の使用

の *管理者* サイドバー、移動 **ストア** > **設定** > **設定** > **詳細** > **開発者** > **JavaScript 設定**.

### コマンドラインの使用

クラウドインフラストラクチャ上のAdobe Commerceで JS の縮小を有効にするには：

1. このコマンドをローカルで実行します。

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. 変更をにコミット `app/etc/config.php` ファイルを作成し、再デプロイします。

## JS ファイルの結合とバンドル

コマース管理でのマージまたはバンドルをオンにできます（マージとバンドルを同時に有効にすることはできません）。 [!UICONTROL **ストア** > **設定** > **設定** > **詳細** > **開発者** > **JavaScript 設定**].

コマンドラインから、Adobe Commerceの組み込みバンドル（基本的なバンドル）を有効にすることもできます。

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## 追加情報

- [クライアント側の最適化設定](../../../performance/configuration.md#client-side-optimization-settings)
- [ユーザーガイド：リソースファイルの最適化](https://docs.magento.com/user-guide/system/file-optimization.html)
- [フロントエンド開発者ガイド：CSS の結合、縮小、サイトのパフォーマンス](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [高度な JavaScript のバンドル](../../../performance/advanced-js-bundling.md)

