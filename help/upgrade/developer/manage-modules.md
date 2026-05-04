---
title: モジュールと拡張機能の管理（開発者）
description: コマンドラインインターフェイスとComposer パッケージマネージャーを使用して、Adobe Commerce モジュールと拡張機能を管理します。
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 3%

---

# モジュールと拡張機能の管理

共同制作者は、Adobe Commerce `composer.json` ファイルでバージョンを指定して、モジュールと拡張機能をアップグレードします。 提供元の開発者でない場合は、[ アップグレードを実行する](../implementation/perform-upgrade.md)を参照してください。

`require` セクションを`composer.json` ファイルに追加するか、`composer require` コマンドを次のように使用できます。

{{$include /help/_includes/server-login.md}}

次のオプションがあります。

## 利用可能なモジュールバージョンを取得する

コマンドの使用状況：

```shell
composer show --all <vendor>/<name>
```

例：

```shell
composer show --all example/module
```

## `composer require` コマンドの使用

コマンドの使用状況：

```shell
composer require <vendor>/<name>:<version>
```

例：

```shell
composer require example/module:1.0.0
```

Composerが依存関係を更新し、モジュールをインストールする間、待ちます。

## composer.json ファイルに`require` セクションを追加します

1. テキストエディターで`composer.json`を開きます。

1. `require` セクションを追加します。

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. `composer.json` ファイルに変更を保存し、テキストエディターを終了します。

1. 依存関係を解決し、正確なバージョンを`composer.lock` ファイルに書き込みます。

   ```shell
   composer update
   ```

<!-- Last updated from includes: 2022-09-08 16:00:49 -->
