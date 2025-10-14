---
title: モジュールと拡張機能の管理（開発者）
description: コマンドラインインターフェイスと Composer パッケージマネージャーを使用して、Adobe Commerce モジュールと拡張機能を管理します。
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 3%

---

# モジュールと拡張機能の管理

投稿する開発者は、Adobe Commerce `composer.json` ファイルでバージョンを指定することで、モジュールと拡張機能をアップグレードします。 コントリビューションを行う開発者でない場合は、[&#x200B; アップグレードの実行 &#x200B;](../implementation/perform-upgrade.md) を参照してください。

`require` ファイルに `composer.json` セクションを追加するか、`composer require` コマンドを次のように使用できます。

{{$include /help/_includes/server-login.md}}

以下のオプションがあります。

## 使用可能なモジュールバージョンの取得

コマンドの使用法：

```bash
composer show --all <vendor>/<name>
```

例：

```bash
composer show --all example/module
```

## `composer require` コマンドの使用

コマンドの使用法：

```bash
composer require <vendor>/<name>:<version>
```

例：

```bash
composer require example/module:1.0.0
```

Composer が依存関係を更新してモジュールをインストールしています。しばらくお待ちください。

## composer.json ファイルに `require` セクションを追加します。

1. `composer.json` をテキストエディターで開きます。

1. `require` セクションを追加します。

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. 変更内容を `composer.json` ファイルに保存し、テキストエディターを終了します。

1. 依存関係を解決し、正確なバージョンを `composer.lock` ファイルに書き込みます。

   ```bash
   composer update
   ```

<!-- Last updated from includes: 2022-09-08 16:00:49 -->
