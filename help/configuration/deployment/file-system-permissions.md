---
title: ファイルシステムのアクセス権限
description: 開発用および実稼動用のCommerce アプリケーションファイルシステムの所有者を設定する方法を参照してください。
feature: Configuration, Roles/Permissions
exl-id: 95b27db9-5247-4f58-a9af-1590897d73db
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---

# ファイルシステムのアクセス権限

この節では、開発用および実稼動用のCommerce ファイルシステムの所有者を設定する方法について説明します。 続行する前に、[ ファイルシステムの所有権と権限の概要 ](../../installation/prerequisites/file-system/overview.md) で説明されている概念を確認してください。

ここでは、Commerceの開発および実稼働システムに焦点を当てます。 Commerceをインストールする場合は、[ インストール前の所有権と権限の設定 ](../../installation/prerequisites/file-system/configure-permissions.md) を参照してください。

以降のセクションでは、1 人または 2 人のファイル・システム所有者の要件について説明します。 つまり、

- **1 人のユーザー** – 通常は、サーバー上の 1 人のユーザーにのみアクセスできる共有ホスティングプロバイダーで必要です。このユーザーはログインでき、FTP を使用してファイルを転送できます。このユーザーは web サーバーも実行します。

- **2 人のユーザー** – 独自のCommerce サーバーを実行する場合は、2 人のユーザーをお勧めします。1 人はファイルの転送とコマンドラインユーティリティの実行を行うユーザー、もう 1 人は web サーバーソフトウェアの別のユーザーです。 可能であれば、より安全なので、この方法をお勧めします。

  代わりに、次のように別々のユーザーを使用できます。

   - 管理およびストアフロントを実行する web サーバーユーザー。

   - _コマンドラインユーザー_：サーバーへのログインに使用できるローカルユーザーアカウントです。 Commerce cron ジョブとコマンドラインユーティリティを実行します。

## 共有ホスティング用の実稼動ファイルシステムの所有権（1 人のユーザー）

1 人の所有者による設定を使用するには、web サーバーを実行するユーザーと同じユーザーとしてCommerce サーバーにログインする必要があります。 これは、共有ホスティングで一般的です。

ファイルシステム所有者が 1 人であることは安全性が低いので、可能であれば、Commerceを共有ホスティングではなくプライベートサーバーの実稼動環境にデプロイすることをお勧めします。

### デフォルトまたは開発者モード用に 1 つの所有者を設定

デフォルトまたは開発者モードでは、次のディレクトリをユーザーが書き込み可能にする必要があります。

- `vendor`
- `app/etc`
- `pub/static`
- `var`
- その他の静的リソース
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

これらのアクセス許可は、コマンド ラインまたは共有ホスティング プロバイダが提供するファイル マネージャ アプリケーションを使用して設定できます。

### 実稼動モード用に 1 つの所有者を設定

サイトを実稼動環境にデプロイする準備が整ったら、セキュリティを強化するために、次のディレクトリにあるファイルからの書き込みアクセス権を削除する必要があります。

- `vendor`
- `app/code`
- `app/etc`
- `pub/static`
- その他の静的リソース
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

コンポーネントを更新したり、新しいコンポーネントをインストールしたり、Commerce ソフトウェアをアップグレードしたりするには、上記のディレクトリがすべて読み取り/書き込み可能である必要があります。

#### コードファイルとディレクトリを読み取り専用にする

Web サーバーユーザーのグループからファイルおよびディレクトリへの書き込み権限を削除するには、次の手順に従います。

1. Commerce サーバーにログインします。

1. Commerce インストールディレクトリに移動します。

1. 実稼動モードに変更します。

   ```bash
   bin/magento deploy:mode:set production
   ```

1. 次のディレクトリへの書き込み権限を削除します。

   ```bash
   find app/code var/view_preprocessed vendor pub/static app/etc generated/code generated/metadata \( -type f -or -type d \) -exec chmod u-w {} + && chmod o-rwx app/etc/env.php
   ```

1. コマンドラインツールを実行可能にします。

   ```bash
   chmod u+x bin/magento
   ```

#### コードファイルとディレクトリを書き込み可能にする

ファイルとディレクトリを書き込み可能にして、コンポーネントを更新し、Commerce ソフトウェアをアップグレードできるようにするには：

1. Commerce サーバーにログインします。
1. Commerce インストールディレクトリに移動します。
1. 次のコマンドを入力します。

   ```bash
   chmod -R u+w .
   ```

### オプションで `magento_umask` を設定

_インストールガイド_ の [umask の設定（オプション ](../../installation/next-steps/set-umask.md) を参照してください。

## プライベートホスティング用の実稼動ファイルシステムの所有権（2 人のユーザー）

独自のサーバー（ホスティングプロバイダーのプライベートサーバー設定を含む）を使用する場合、次の 2 つのユーザーがあります。

- 管理およびストアフロントを実行する **web サーバーユーザー**。

  Linux システムには通常、このユーザー向けのシェルはありません。web サーバーユーザーとしてCommerce サーバーにログインしたり、web サーバーユーザーに切り替えたりすることはできません。

- **コマンドラインユーザー**：としてCommerce サーバーにログインするか、に切り替えます。

  Commerceは、このユーザーを使用して CLI コマンドおよび cron を実行します。

  >[!INFO]
  >
  >コマンドラインユーザーは、_ファイルシステム所有者_ とも呼ばれます。

これらのユーザーは同じファイルにアクセスする必要があるので、両方が属する [ 共有グループ ](../../installation/prerequisites/file-system/configure-permissions.md#about-the-shared-group) を作成することをお勧めします。 次の手順は、既にこれを行っていることを前提としています。

以下のセクションの 1 つを参照してください。

- 開発者モードまたはデフォルトモードの 2 人のファイルシステム所有者
- 本番モードで 2 人のファイル・システム・オーナー

### デフォルトまたは開発者モード用に 2 つの所有者を設定

次のディレクトリのファイルは、開発者モードとデフォルトモードの両方のユーザーが書き込み可能にする必要があります。

- `var`
- `generated`
- `pub/static`
- `pub/media`
- `app/etc`

ディレクトリの [`setgid`](https://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/) ビットを設定して、アクセス許可が常に親ディレクトリから継承されるようにします。

>[!INFO]
>
>`setgid` はディレクトリにのみ適用され、ファイルには適用されません __。

さらに、web サーバーグループによるディレクトリの書き込みも可能にする必要があります。 これらのディレクトリにはコンテンツが存在する可能性があるので、権限を再帰的に追加します。

#### 権限と `setgid` の設定

開発者モードの `setgid` ーザーと権限を設定するには：

1. ファイルシステムの所有者としてCommerce サーバーにログインするか、に切り替えます。
1. 次のコマンドを表示されている順序で入力します。

   ```bash
   cd <magento_root>
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

### 本番モードで 2 人のファイル・システム・オーナー

サイトを実稼動環境にデプロイする準備が整ったら、セキュリティを強化するために、次のディレクトリにあるファイルからの書き込みアクセス権を削除する必要があります。

- `vendor`
- `app/code`
- `app/etc`
- `lib`
- `pub/static`
- その他の静的リソース
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

#### コードファイルとディレクトリを読み取り専用にする

Web サーバーユーザーのグループからファイルおよびディレクトリへの書き込み可能なアクセス許可を削除するには、次の手順に従います。

1. Commerce サーバーにログインします。
1. Commerce インストールディレクトリに移動します。
1. ファイルシステムの所有者として、次のコマンドを入力して実稼動モードに変更します。

   ```bash
   bin/magento deploy:mode:set production
   ```

1. `root` 権限を持つユーザーとして、次のコマンドを入力します。

   ```bash
   find app/code lib pub/static app/etc generated/code generated/metadata var/view_preprocessed \( -type d -or -type f \) -exec chmod g-w {} + && chmod o-rwx app/etc/env.php
   ```

#### コードファイルとディレクトリを書き込み可能にする

ファイルとディレクトリを書き込み可能にして、コンポーネントを更新し、Commerce ソフトウェアをアップグレードできるようにするには：

1. Commerce サーバーにログインします。
1. Commerce インストールディレクトリに移動します。
1. 次のコマンドを入力します。

   ```bash
   find app/code lib var generated vendor pub/static pub/media app/etc \( -type d -or -type f \) -exec chmod g+w {} + && chmod o+rwx app/etc/env.php
   ```
