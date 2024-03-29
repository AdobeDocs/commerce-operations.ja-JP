---
title: モジュールと拡張機能の管理（開発者）
description: Adobe CommerceおよびMagento Open Sourceモジュールと拡張機能は、コマンドラインインターフェイスと Composer パッケージマネージャーを使用して管理します。
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: 012cba58b336b032b1c911539008c1fb961c2e07
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 2%

---

# モジュールと拡張機能の管理

Adobe CommerceまたはMagento Open Sourceでバージョンを指定して、開発者がモジュールおよび拡張機能をアップグレードする際に貢献します。 `composer.json` ファイル。 貢献している開発者でない場合は、 [アップグレードの実行](../implementation/perform-upgrade.md).

次のいずれかの方法で、 `require` セクションから `composer.json` ファイルで指定するか、 `composer require` コマンドを次のように指定します。

{{$include /help/_includes/server-login.md}}

次のオプションがあります。

## 利用可能なモジュールバージョンの取得

コマンドの使用：

```bash
composer show --all <vendor>/<name>
```

例：

```bash
composer show --all example/module
```

## 以下を使用します。 `composer require` command

コマンドの使用：

```bash
composer require <vendor>/<name>:<version>
```

例：

```bash
composer require example/module:1.0.0
```

Composer が依存関係を更新し、モジュールをインストールする間お待ちください。

## を追加します。 `require` セクションを composer.json ファイルに追加します。

1. を開きます。 `composer.json` をクリックします。

1. を追加します。 `require` 」セクションに入力します。

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. 変更を `composer.json` ファイルを開き、テキストエディタを終了します。

1. 依存関係を解決し、正確なバージョンを `composer.lock` ファイル。

   ```bash
   composer update
   ```
