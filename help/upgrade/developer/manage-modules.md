---
title: モジュールと拡張機能の管理（開発者）
description: コマンドラインインターフェイスとComposer パッケージマネージャーを使用して、Adobe Commerce モジュールと拡張機能を管理します。
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
last-update: 2026-04-28
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: f08fa0de-a550-4acd-b570-f81cf1d03aaf
    internal-label: Commerce ecosystem
subfeature_v2:
  - id: dad884f1-e840-49a1-970e-2f965bdbc410
    internal-label: Extensions
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: a3c0eba7bdcd8017e88bdb4df1f45d77fe4bb351
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

<!-- Last updated from includes: 2026-04-17 13:49:36 -->
