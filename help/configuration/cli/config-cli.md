---
title: コマンドラインツール
description: Commerce コマンドラインツールを使用して、インストールタスクと設定タスクを実行します。
exl-id: 44470ce1-a5a2-4c12-962e-e42d11a6bd15
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# コマンドラインツール

Commerceには、1 つのコマンドラインインターフェイス（CLI）があります。`<magento_root>/bin/magento` – 次のようなインストール タスクおよび構成タスクを実行します。

- Commerceのインストール（およびデータベーススキーマの更新、デプロイメント設定の作成などの関連タスク）
- キャッシュのクリア
- インデックスの管理（インデックスの再作成など）
- 翻訳辞書と翻訳パッケージの作成
- ファクトリやプラグインのインターセプタなど、存在しないクラスを生成し、オブジェクトマネージャの依存関係挿入設定を生成する
- 静的ビューファイルのデプロイ
- Less からの CSS の作成

その他の利点は次のとおりです。

- 単一のコマンド（`<magento_root>/bin/magento list`）に、使用可能なすべてのインストールおよび設定コマンドを示します。
- Symfony に基づく一貫性のあるユーザーインターフェイス。
- CLI は拡張可能なため、サードパーティ開発者がプラグインすることができます。 これには、ユーザーの学習曲線を排除するという追加のメリットがあります。
- 無効なモジュールのコマンドは表示されません。

ここでは、CLI を使用したAdobe Commerce ソフトウェアの設定について説明します。 Commerceのインストールについて詳しくは、 [インストールフロー](../../installation/overview.md) が含まれる _インストールガイド_.

## 前提条件

CLI の使用を開始する前に、以下を確認します。

1. お使いのシステムはで説明されている要件を満たしています。 [必要システム構成](../../installation/system-requirements.md) が含まれる _インストールガイド_.
1. で説明したすべての前提条件タスクを完了しました [前提条件](../../installation/prerequisites/overview.md) が含まれる _インストールガイド_.
1. Commerce サーバーにログインしたら、Commerce ファイルシステムへの書き込み権限を持つユーザーに切り替えます。 参照： [ファイルシステムの所有者に切り替える](../../installation/prerequisites/file-system/overview.md) が含まれる _インストールガイド_.

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

追加 `<magento_root>/bin` お使いのシステム `PATH`.

CentOS 用の bash シェルの例：

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

オプションで、次を実行できます。

- `cd <magento_root>/bin` そしてそれらを `./magento <command name>`
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` は、web サーバーの docroot のサブディレクトリです。
