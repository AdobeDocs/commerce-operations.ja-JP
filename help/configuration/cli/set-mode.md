---
title: 操作モードの設定
description: Adobe Commerce操作モードの設定について説明します。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---


# 操作モードの設定

{{file-system-owner}}

セキュリティと使いやすさを向上させるために、スイッチを切り替えるコマンドを追加しました。 [アプリケーションモード](../bootstrap/application-modes.md) 開発者から実稼動へ、または開発者から実稼動へ。

静的ビューファイルが `pub/static` ディレクトリとコードコンパイルの問題を修正しました。

>[!INFO]
>
>バージョン 2.0.6 以降では、デフォルト、開発、実稼動の各モードを切り替える際に、Commerce はファイルまたはディレクトリの権限を明示的に設定しません。 他のモードとは異なり、開発者モードと実稼動モードは `env.php` ファイル。 Adobe Commerce on cloud infrastructure は、実稼働とメンテナンスのモードのみをサポートしています。
>
>詳しくは、 [開発および実稼動環境でのコマースの所有権と権限](../deployment/file-system-permissions.md).

開発者モードまたは実稼動モードに変更すると、次のディレクトリの内容が消去されます。

```terminal
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

例外：

- `.htaccess` ファイルは削除されません
- `pub/static` には、静的コンテンツのバージョンを指定するファイルが含まれます。このファイルは削除されません

>[!INFO]
>
>Commerce では、デフォルトで `var` キャッシュ、ログ、コンパイル済みコードを格納するディレクトリ。 このディレクトリはカスタマイズできますが、このガイドでは、 `var`.

## 現在のモードを表示

これを行う最も簡単な方法は、このコマンドを [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md). ホスティングを共有している場合は、プロバイダーがサーバーにログインするために提供するユーザーです。 プライベートサーバーがある場合、通常は Commerce サーバー上のローカルユーザーアカウントです。

コマンドの使用：

```bash
bin/magento deploy:mode:show
```

次のようなメッセージが表示されます。

```terminal
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

場所：

- **`{mode}`** 次のいずれかを指定できます。 `default`, `developer`または `production`

## モードの変更

コマンドの使用：

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

場所：

- **`{mode}`** は必須です。次のどちらかを指定できます。 `developer` または `production`

- **`--skip-compilation`** は、スキップに使用できるオプションのパラメータです [コードコンパイル](../cli/code-compiler.md) 実稼動モードに変更した場合。

以下に例を示します。

### 実稼動モードに変更

```bash
bin/magento deploy:mode:set production
```

次のようなメッセージが表示されます。

```terminal
Enabled maintenance mode
Requested languages: en_US
=== frontend -> Magento/luma -> en_US ===
... more ...
Successful: 1884 files; errors: 0
---

=== frontend -> Magento/blank -> en_US ===
... more ...
Successful: 1828 files; errors: 0
---

=== adminhtml -> Magento/backend -> en_US ===
... more ...
---

=== Minify templates ===
... more ...
Successful: 897 files modified
---

New version of deployed files: 1440461332
Static content deployment complete
Gathering css/styles-m.less sources.
Successfully processed LESS and/or [Sass](https://glossary.magento.com/sass) files
[CSS](https://glossary.magento.com/css) deployment complete
Generated classes:
      Magento\Sales\Api\Data\CreditmemoCommentInterfacePersistor
      Magento\Sales\Api\Data\CreditmemoCommentInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoCommentSearchResultInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoComment\Repository
      Magento\Sales\Api\Data\CreditmemoItemInterfacePersistor
      ... more ...
Compilation complete
Disabled maintenance mode
Enabled production mode.
```

### 開発者モードに変更

実稼動モードから開発モードに変更する場合、予期しないエラーを防ぐために、生成されたクラスとプロキシなどの Object Manager エンティティをクリアする必要があります。 その後、モードを変更できます。 次の手順を実行します。

1. 実稼動モードから開発モードに変更する場合は、 `generated/code` および `generated/metadata` ディレクトリ：

   ```bash
   rm -rf <magento_root>/generated/metadata/* <magento_root>/generated/code/*
   ```

1. モードを設定します。

   ```bash
   bin/magento deploy:mode:set developer
   ```

   次のメッセージが表示されます。

   ```terminal
   Enabled developer mode.
   ```

### デフォルトモードに変更

```bash
bin/magento deploy:mode:set default
```

次のメッセージが表示されます。

```terminal
Enabled default mode.
```

### CLI コマンドをどこからでも実行

[CLI コマンドをどこからでも実行](../cli/config-cli.md#config-install-cli-first).

まだ `<Commerce-install-directory>/bin` システムに `PATH`を指定しない場合は、単独でコマンドを実行する際にエラーが発生する可能性があります。
