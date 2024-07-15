---
title: 操作モードの設定
description: Adobe Commerceのオペレーションモードの設定について説明します。
exl-id: 62d183fa-d4ff-441d-b8bd-64ef5ae10978
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# 操作モードの設定

{{file-system-owner}}

セキュリティと使いやすさを向上させるために、開発者から実稼動環境へ、またはその逆に [ アプリケーションモード ](../bootstrap/application-modes.md) を切り替えるコマンドを追加しました。

実稼動モードでは、静的ビューファイルがロー `pub/static` ルディレクトリに入力され、コードがコンパイルされるので、パフォーマンスが向上します。

>[!INFO]
>
>バージョン 2.0.6 以降では、デフォルト、開発、実稼動の各モードに切り替えても、Commerceはファイルまたはディレクトリの権限を明示的に設定しません。 他のモードとは異なり、開発者モードと実稼動モードは `env.php` ファイルで設定されます。 クラウドインフラストラクチャー上のAdobe Commerceでは、実稼動モードとメンテナンスモードのみをサポートしています。
>
>詳しくは、[ 開発および実稼動におけるCommerceの所有権と権限 ](../deployment/file-system-permissions.md) を参照してください。

開発者モードまたは実稼動モードに変更する場合は、次のディレクトリの内容を消去します。

```terminal
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

例外：

- `.htaccess` 個のファイルが削除されません
- `pub/static` には、静的コンテンツのバージョンを指定するファイルが含まれています。このファイルは削除されません

>[!INFO]
>
>デフォルトでは、Commerceは `var` ディレクトリを使用して、キャッシュ、ログ、コンパイル済みコードを保存します。 このディレクトリはカスタマイズできますが、このガイドでは `var` と想定しています。

## 現在のモードを表示

これを行う最も簡単な方法は、このコマンドを [ ファイルシステムの所有者 ](../../installation/prerequisites/file-system/overview.md) として実行することです。 ホスティングを共有している場合、これはプロバイダーからサーバーにログインするためのユーザーです。 プライベートサーバーがある場合、通常はCommerce サーバーのローカルユーザーアカウントになります。

コマンドの使用法：

```bash
bin/magento deploy:mode:show
```

次のようなメッセージが表示されます。

```terminal
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

ここで、

- **`{mode}`** は、`default`、`developer`、`production` のいずれかです

## モードの変更

コマンドの使用法：

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

ここで、

- **`{mode}`** が必要です。`developer` または `production` を指定できます

- **`--skip-compilation`** は、実稼動モードに変更する際に [ コードのコンパイル ](../cli/code-compiler.md) をスキップするために使用できるオプションのパラメーターです。

次に例を示します。

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
Successfully processed LESS and/or Sass files
CSS deployment complete
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

実稼動モードから開発者モードに変更する場合は、予期しないエラーを防ぐために、生成されたクラスおよびプロキシなどのオブジェクトマネージャーエンティティをクリアする必要があります。 その後、モードを変更できます。 次の手順を使用します。

1. 実稼動モードから開発者モードに変更する場合は、`generated/code` ディレクトリと `generated/metadata` ディレクトリの内容を削除します。

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

### どこからでも CLI コマンドを実行

[CLI コマンドをどこからでも実行する ](../cli/config-cli.md#config-install-cli-first)。

`<Commerce-install-directory>/bin` をシステム `PATH` に追加していない場合は、コマンド自体を実行したときにエラーが発生する可能性があります。
