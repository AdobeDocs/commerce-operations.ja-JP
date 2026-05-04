---
title: コマンドラインツール
description: Adobe Commerce コマンドラインツールを使用して、インストールおよび設定タスクを実行する方法を説明します。 CLI コマンドと管理機能について説明します。
exl-id: 44470ce1-a5a2-4c12-962e-e42d11a6bd15
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---

# コマンドラインツール

Commerceには、次のようなインストールおよび設定タスクを実行する1つのコマンドラインインターフェイス（`<magento_root>/bin/magento`）があります。

- Commerceのインストール（およびデータベーススキーマの更新、デプロイメント設定の作成などの関連タスク）
- キャッシュのクリア
- インデックスの再作成を含むインデックスの管理
- 翻訳辞書と翻訳パッケージの作成
- プラグインのファクトリやインターセプタなどの存在しないクラスを生成し、オブジェクトマネージャーの依存関係インジェクション設定を生成する
- 静的ビューファイルのデプロイ
- LessからのCSSの作成

その他の利点には、次のようなものがあります。

- 単一のコマンド （`<magento_root>/bin/magento list`）には、使用可能なすべてのインストールおよび設定コマンドが一覧表示されます。
- Symfonyに基づいた一貫したユーザーインターフェイス。
- CLIは拡張可能なので、サードパーティの開発者はCLIに「プラグイン」できます。 これは、ユーザーの学習曲線を排除するという追加の利点があります。
- 無効なモジュールのコマンドは表示されません。

このトピックでは、CLIを使用したAdobe Commerce ソフトウェアの設定について説明します。 Commerceのインストールについて詳しくは、_インストールガイド_&#x200B;の[ インストールフロー](../../installation/overview.md)を参照してください。

## 前提条件

CLIの使用を開始する前に、次のことを確認してください。

1. お使いのシステムは、_インストールガイド_&#x200B;の[ システム要件](../../installation/system-requirements.md)で説明されている要件を満たしています。
1. _インストールガイド_&#x200B;の[前提条件](../../installation/prerequisites/overview.md)で説明したすべての前提条件タスクを完了しました。
1. Commerce サーバーにログインしたら、Commerce ファイルシステムへの書き込み権限を持つユーザーに切り替えます。 _インストールガイド_&#x200B;の「[ ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md)への切り替え」を参照してください。

## コマンドの実行

bash シェルの場合は、次の構文を使用してファイルシステム所有者に切り替え、同時にコマンドを入力します。

```shell
su <file system owner> -s /bin/bash -c <command>
```

ファイルシステムの所有者がログインを許可しない場合は、次を使用できます。

```shell
sudo -u <file system owner> <command>
```

**任意のディレクトリからCLI コマンドを実行するには**:

システム `PATH`に`<magento_root>/bin`を追加します。

CentOSのbash シェルの例：

```shell
export PATH=$PATH:/var/www/html/magento2/bin
```

必要に応じて、次を実行できます。

- `cd <magento_root>/bin`として実行`./magento <command name>`
- `<magento_root>/bin/magento <command name>`
- `<magento_root>`はweb サーバーのdocrootのサブディレクトリです
