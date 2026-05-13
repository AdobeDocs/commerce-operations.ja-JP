---
title: 操作モードの設定
description: 開発者向けと本番向けのAdobe Commerceの運用モードを設定する方法について説明します。 モード切り替えコマンドとセキュリティへの影響をご覧ください。
exl-id: 62d183fa-d4ff-441d-b8bd-64ef5ae10978
source-git-commit: d20f9d38a06fcd0eed872fe6f7ef1f3ee015a00f
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# 操作モードの設定

{{file-system-owner}}

セキュリティと使いやすさを向上させるために、[ アプリケーションモード ](../bootstrap/application-modes.md)を開発者から実稼動に、またはその逆に切り替えるコマンドを追加しました。

静的ビューファイルが`pub/static` ディレクトリに入力され、コードのコンパイルが原因で実稼動モードのパフォーマンスが向上します。

>[!INFO]
>
>バージョン 2.0.6以降では、デフォルト、開発、実稼動モードを切り替える際に、Commerceがファイルまたはディレクトリの権限を明示的に設定しません。 他のモードとは異なり、開発者モードと実稼動モードは`env.php` ファイルで設定されます。 Adobe Commerce on cloud infrastructureでは、実稼動モードとメンテナンスモードのみがサポートされます。
>
>開発環境および本番環境での[Commerceの所有権と権限](../deployment/file-system-permissions.md)を参照してください。

開発者モードまたは実稼動モードに変更すると、以下のディレクトリの内容が消去されます。

```text
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

例外：

- `.htaccess` ファイルは削除されません
- `pub/static`には、静的コンテンツのバージョンを指定するファイルが含まれています。このファイルは削除されません

>[!INFO]
>
>デフォルトでは、Commerceは`var` ディレクトリを使用して、キャッシュ、ログ、コンパイルされたコードを保存します。 このディレクトリはカスタマイズできますが、このガイドでは`var`と見なされます。

## 現在のモードを表示

これを行う最も簡単な方法は、このコマンドを[ ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md)として実行することです。 共有ホスティングがある場合、これは、プロバイダーからサーバーにログインするユーザーです。 プライベートサーバーがある場合は、通常、Commerce サーバーのローカルユーザーアカウントです。

コマンドの使用状況：

```shell
bin/magento deploy:mode:show
```

次のようなメッセージが表示されます。

```text
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

どこで：

- **`{mode}`**&#x200B;は、`default`、`developer`または`production`のいずれかです

## 変更モード

コマンドの使用状況：

```shell
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

どこで：

- **`{mode}`**&#x200B;が必要です。`developer`または`production`のいずれかです

- **`--skip-compilation`**&#x200B;は、実稼動モードに変更する際に[ コードコンパイル ](../cli/code-compiler.md)をスキップするために使用できるオプションのパラメーターです。

例は次のとおりです。

### 実稼動モードへの変更

```shell
bin/magento deploy:mode:set production
```

次のようなメッセージが表示されます。

```text
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

### 開発者向けモードに変更

実稼動環境から開発者モードに変更する場合は、予期しないエラーを防ぐために、生成されたクラスとプロキシなどのObject Manager エンティティをクリアする必要があります。 その後、モードを変更できます。 次の手順を使用します。

1. 実稼動モードから開発者モードに変更する場合は、`generated/code`および`generated/metadata` ディレクトリの内容を削除します。

   ```shell
   rm -rf <magento_root>/generated/metadata/* <magento_root>/generated/code/*
   ```

1. モードを設定します。

   ```shell
   bin/magento deploy:mode:set developer
   ```

   次のメッセージが表示されます。

   ```text
   Enabled developer mode.
   ```

### デフォルトモードに変更

```shell
bin/magento deploy:mode:set default
```

次のメッセージが表示されます。

```text
Enabled default mode.
```

### どこからでもCLI コマンドを実行

[どこからでもCLI コマンドを実行](../cli/config-cli.md#prerequisites)。

システム `PATH`に`<Commerce-install-directory>/bin`を追加していない場合は、コマンドを単独で実行する際にエラーが発生する可能性があります。
