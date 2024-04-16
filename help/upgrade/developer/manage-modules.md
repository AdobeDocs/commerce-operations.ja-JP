---
title: モジュールと拡張機能の管理（開発者）
description: コマンドラインインターフェイスと Composer パッケージマネージャーを使用して、Adobe Commerce モジュールと拡張機能を管理します。
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 2%

---

# モジュールと拡張機能の管理

投稿する開発者は、Adobe CommerceまたはMagento Open Sourceでバージョンを指定することで、モジュールおよび拡張機能をアップグレードします `composer.json` ファイル。 コントリビューション機能を持つ開発者でない場合は、を参照してください。 [アップグレードの実行](../implementation/perform-upgrade.md).

を追加できます `require` セクションから `composer.json` ファイルを開くか、 `composer require` コマンドは次のようになります。

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

## の使用 `composer require` コマンド

コマンドの使用法：

```bash
composer require <vendor>/<name>:<version>
```

例：

```bash
composer require example/module:1.0.0
```

Composer が依存関係を更新してモジュールをインストールしています。しばらくお待ちください。

## を追加 `require` composer.json ファイルのセクション

1. を開きます `composer.json` テキストエディター。

1. を追加 `require` セクション。

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. 変更をに保存します。 `composer.json` ファイルを開き、テキストエディターを終了します。

1. 依存関係を解決し、正確なバージョンをに書き込む `composer.lock` ファイル。

   ```bash
   composer update
   ```
