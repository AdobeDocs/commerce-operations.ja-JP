---
title: コマンドラインツール
description: Commerce コマンドラインツールを使用して、インストールタスクと設定タスクを実行します。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# コマンドラインツール

Commerce には 1 つのコマンドラインインターフェイス (CLI) があります。`<magento_root>/bin/magento` — インストールタスクと設定タスクを実行します。以下が含まれます。

- コマースのインストール（およびデータベーススキーマの更新、デプロイメント設定の作成などの関連タスク）
- キャッシュのクリア
- インデックスの管理（インデックスの再作成を含む）
- 翻訳辞書と翻訳パッケージの作成
- プラグインのファクトリやインターセプタなどの存在しないクラスを生成し、オブジェクトマネージャの依存関係インジェクション設定を生成する
- 静的ビューファイルのデプロイ
- LESS からの CSS の作成

その他の利点は次のとおりです。

- 1 つのコマンド (`<magento_root>/bin/magento list`) に、使用可能なすべてのインストールおよび設定コマンドを示します。
- Symfony に基づく一貫したユーザ・インタフェース
- CLI は拡張可能なため、サード・パーティの開発者は CLI に「プラグイン」できます。 これにより、ユーザーの学習曲線をなくすこともできます。
- 無効なモジュールのコマンドは表示されません。

このトピックでは、CLI を使用したAdobe CommerceおよびMagento Open Sourceソフトウェアの設定について説明します。 コマースのインストールについて詳しくは、 [インストールフロー](../../installation/overview.md) 内 _インストールガイド_.

## 前提条件

CLI を使用する前に、次の点を確認します。

1. システムが、 [必要システム構成](../../installation/system-requirements.md) 内 _インストールガイド_.
1. 前提条件のタスクをすべて完了しました ( [前提条件](../../installation/prerequisites/overview.md) 内 _インストールガイド_.
1. Commerce サーバーにログインした後、Commerce ファイルシステムに書き込む権限を持つユーザーに切り替えます。 詳しくは、 [ファイルシステムの所有者に切り替え](../../installation/prerequisites/file-system/overview.md) 内 _インストールガイド_.

## コマンドの実行

bash シェルでは、次の構文を使用してファイルシステムの所有者に切り替え、同時にコマンドを入力します。

```bash
su <file system owner> -s /bin/bash -c <command>
```

ファイルシステムの所有者がログインを許可していない場合は、次を使用できます。

```bash
sudo -u <file system owner> <command>
```

**任意のディレクトリから CLI コマンドを実行するには**:

追加 `<magento_root>/bin` システムに `PATH`.

CentOS 用の bash シェルの例：

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

必要に応じて、次の操作を実行できます。

- `cd <magento_root>/bin` を実行します。 `./magento <command name>`
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` は、Web サーバーの docroot のサブディレクトリです。
