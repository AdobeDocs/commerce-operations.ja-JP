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

セキュリティと使いやすさを向上させるために、切り替えるコマンドを追加しました [アプリケーションモード](../bootstrap/application-modes.md) 開発者から実稼動環境へ、またはその逆も同様です。

静的ビューファイルが以下に入力されるので、実稼動モードのパフォーマンスが向上します。 `pub/static` ディレクトリと（コードのコンパイルにより）。

>[!INFO]
>
>バージョン 2.0.6 以降では、デフォルト、開発、実稼動の各モードに切り替えても、Commerceはファイルまたはディレクトリの権限を明示的に設定しません。 他のモードとは異なり、開発者モードと実稼動モードは `env.php` ファイル。 クラウドインフラストラクチャー上のAdobe Commerceでは、実稼動モードとメンテナンスモードのみをサポートしています。
>
>参照： [Commerceの所有権と開発および実稼働環境での権限](../deployment/file-system-permissions.md).

開発者モードまたは実稼動モードに変更する場合は、次のディレクトリの内容を消去します。

```terminal
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

例外：

- `.htaccess` ファイルは削除されません
- `pub/static` 静的コンテンツのバージョンを指定するファイルが含まれます。このファイルは削除されません

>[!INFO]
>
>デフォルトでは、Commerceはを使用します `var` キャッシュ、ログおよびコンパイル済みコードを格納するディレクトリ。 このディレクトリはカスタマイズできますが、このガイドでは、次のように想定しています `var`.

## 現在のモードを表示

これを行う最も簡単な方法は、このコマンドを [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md). ホスティングを共有している場合、これはプロバイダーからサーバーにログインするためのユーザーです。 プライベートサーバーがある場合、通常はCommerce サーバーのローカルユーザーアカウントになります。

コマンドの使用法：

```bash
bin/magento deploy:mode:show
```

次のようなメッセージが表示されます。

```terminal
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

ここで、

- **`{mode}`** 次のいずれかになります `default`, `developer`、または `production`

## モードの変更

コマンドの使用法：

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

ここで、

- **`{mode}`** は必須で、次のいずれかを指定できます `developer` または `production`

- **`--skip-compilation`** スキップに使用できるオプションのパラメーターです [コードコンパイル](../cli/code-compiler.md) 実稼動モードに変更した場合。

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

1. 実稼動モードから開発者モードに変更する場合は、の内容を削除します `generated/code` および `generated/metadata` ディレクトリ：

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

[どこからでも CLI コマンドを実行](../cli/config-cli.md#config-install-cli-first).

を追加していない場合 `<Commerce-install-directory>/bin` お使いのシステム `PATH`を選択した場合は、コマンド自体を実行したときにエラーが発生することがあります。
