---
title: コマンドラインツール
description: Adobe Commerce コマンドラインツールを使用して、インストールタスクと設定タスクを実行する方法を説明します。 CLI のコマンドと管理機能を確認します。
exl-id: 44470ce1-a5a2-4c12-962e-e42d11a6bd15
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# コマンドラインツール

Commerceには、インストールおよび設定タスクを実行する次のような 1 つのコマンドラインインターフェイス（`<magento_root>/bin/magento`）があります。

- Commerceのインストール（およびデータベーススキーマの更新、デプロイメント設定の作成などの関連タスク）
- キャッシュのクリア
- インデックスの管理（インデックスの再作成など）
- 翻訳辞書と翻訳パッケージの作成
- ファクトリやプラグインのインターセプタなど、存在しないクラスを生成し、オブジェクトマネージャの依存関係挿入設定を生成する
- 静的ビューファイルのデプロイ
- Less からの CSS の作成

その他の利点は次のとおりです。

- 1 つのコマンド（`<magento_root>/bin/magento list`）に、使用可能なすべてのインストールコマンドと設定コマンドが一覧表示されます。
- Symfony に基づく一貫性のあるユーザーインターフェイス。
- CLI は拡張可能なため、サードパーティ開発者がプラグインすることができます。 これには、ユーザーの学習曲線を排除するという追加のメリットがあります。
- 無効なモジュールのコマンドは表示されません。

ここでは、CLI を使用したAdobe Commerce ソフトウェアの設定について説明します。 Commerceのインストールについて詳しくは、[&#x200B; インストールガイド &#x200B;](../../installation/overview.md) の _インストールフロー_ を参照してください。

## 前提条件

CLI の使用を開始する前に、以下を確認します。

1. お使いのシステムは、『インストール ガイド [&#x200B; の &#x200B;](../../installation/system-requirements.md) システム要件 _に記載されている要件を満たしてい_ す。
1. [&#x200B; インストール ガイド &#x200B;](../../installation/prerequisites/overview.md) の _前提条件_ で説明されているすべての前提条件タスクを完了しました。
1. Commerce サーバーにログインしたら、Commerce ファイルシステムへの書き込み権限を持つユーザーに切り替えます。 [&#x200B; インストール ガイド &#x200B;](../../installation/prerequisites/file-system/overview.md) の _ファイル システム所有者に切り替える_ を参照してください。

## コマンドの実行

bash シェルの場合は、次の構文を使用してファイルシステム所有者に切り替え、コマンドを同時に入力します。

```bash
su <file system owner> -s /bin/bash -c <command>
```

ファイルシステムの所有者がログインを許可しない場合は、次を使用できます。

```bash
sudo -u <file system owner> <command>
```

**任意のディレクトリから CLI コマンドを実行するには**:

`<magento_root>/bin` をシステム `PATH` に追加します。

CentOS 用の bash シェルの例：

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

オプションで、次を実行できます。

- `cd <magento_root>/bin` として `./magento <command name>` び出して実行
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` は、web サーバーの docroot のサブディレクトリです。
