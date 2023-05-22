---
title: ファイルシステムのアクセス権限
description: 開発および実稼動システム用にコマースアプリケーションファイルシステムの所有者または所有者を設定する方法を参照してください。
feature: Configuration, Roles/Permissions
exl-id: 95b27db9-5247-4f58-a9af-1590897d73db
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 0%

---

# ファイルシステムのアクセス権限

このセクションでは、開発および本番システム用にコマースファイルシステムの所有者または所有者を設定する方法について説明します。 続行する前に、 [ファイル・システムの所有権と権限の概要](../../installation/prerequisites/file-system/overview.md).

ここでは、コマースの開発と実稼動システムに焦点を当てます。 Commerce をインストールする場合は、 [プリインストールの所有権と権限を設定](../../installation/prerequisites/file-system/configure-permissions.md).

以降のセクションでは、1 つまたは 2 つのファイル・システム・オーナーの要件について説明します。 つまり、

- **1 人のユーザー** — 通常は共有ホスティングプロバイダで必要です。サーバー上の 1 人のユーザーにのみアクセスできます。このユーザーは、ログイン、FTP を使用したファイル転送が可能で、このユーザーも Web サーバーを実行します。

- **2 人のユーザー** — 独自の Commerce サーバーを実行する場合は、2 人のユーザーをお勧めします。1 つはファイルを転送し、コマンドラインユーティリティを実行するためのもので、もう 1 つは web サーバソフトウェア用の別のユーザです。 可能な場合は、より安全なので、この方が望ましいです。

   代わりに、別のユーザーが存在します。

   - Web サーバーユーザー。管理者とストアフロントを実行します。

   - A _コマンドラインユーザ_：サーバーへのログインに使用できるローカルユーザーアカウントです。 このユーザーは、コマース cron ジョブとコマンドラインユーティリティを実行します。

## 共有ホスティングの本番ファイル・システムの所有権（1 人のユーザー）

1 人の所有者の設定を使用するには、Web サーバーを実行するのと同じユーザーとして Commerce サーバーにログインする必要があります。 これは共有ホスティングの場合に典型的です。

1 つのファイルシステムの所有者の安全性が低いので、可能な場合は共有ホスティングではなく、実稼動環境でコマースをプライベートサーバーにデプロイすることをお勧めします。

### デフォルトまたは開発者モードに 1 人の所有者を設定

デフォルトまたは開発者モードでは、次のディレクトリをユーザーが書き込み可能にする必要があります。

- `vendor`
- `app/etc`
- `pub/static`
- `var`
- その他の静的リソース
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

これらの権限は、共有ホスティングプロバイダーが提供するコマンドラインまたはファイルマネージャーアプリケーションを使用して設定できます。

### 実稼働モード用に 1 人の所有者を設定

サイトを実稼動環境にデプロイする準備が整ったら、セキュリティを強化するために、次のディレクトリ内のファイルから書き込みアクセス権を削除する必要があります。

- `vendor`
- `app/code`
- `app/etc`
- `pub/static`
- その他の静的リソース
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

コンポーネントを更新する、新しいコンポーネントをインストールする、またはコマースソフトウェアをアップグレードするには、前のすべてのディレクトリを読み取り/書き込み可能にする必要があります。

#### コードファイルとディレクトリを読み取り専用にする

Web サーバーのユーザーのグループからファイルおよびディレクトリへの書き込み権限を削除するには、次の手順に従います。

1. Commerce サーバーにログインします。

1. Commerce のインストールディレクトリに移動します。

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

ファイルとディレクトリを書き込み可能にするには、コンポーネントを更新し、コマースソフトウェアをアップグレードします。

1. Commerce サーバーにログインします。
1. Commerce のインストールディレクトリに移動します。
1. 次のコマンドを入力します。

   ```bash
   chmod -R u+w .
   ```

### オプションで設定 `magento_umask`

詳しくは、 [オプションで umask を設定](../../installation/next-steps/set-umask.md) 内 _インストールガイド_.

## プライベート・ホスティングの本番ファイル・システムの所有権（2 人のユーザー）

独自のサーバー（ホスティングプロバイダーのプライベートサーバー設定を含む）を使用する場合、次の 2 人のユーザーがいます。

- この **web サーバーユーザー**:Admin とストアフロントを実行します。

   Linux システムは、通常、このユーザにシェルを提供しません。Commerce サーバーに web サーバーユーザーとしてログインしたり、web サーバーに切り替えたりすることはできません。

- この **コマンドラインユーザ**：またはに切り替えて Commerce Server にログインします。

   Commerce は、このユーザーを使用して CLI コマンドと cron を実行します。

   >[!INFO]
   >
   >コマンドラインユーザーは、 _ファイルシステム所有者_.

これらのユーザーは同じファイルにアクセスする必要があるので、 [共有グループ](../../installation/prerequisites/file-system/configure-permissions.md#about-the-shared-group) 彼らが属する 以下の手順は、既に実行済みであることを前提としています。

次のセクションのいずれかを参照してください。

- 2 つのファイル・システムの所有者（開発者モードまたはデフォルト・モード）
- 本番モードで 2 つのファイル・システムの所有者

### デフォルトまたは開発者モード用に 2 人の所有者を設定

次のディレクトリ内のファイルは、デベロッパーモードとデフォルトモードの両方のユーザーが書き込み可能である必要があります。

- `var`
- `generated`
- `pub/static`
- `pub/media`
- `app/etc`

を [`setgid`](https://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/) ディレクトリ上のビットの場合、権限は常に親ディレクトリから継承されます。

>[!INFO]
>
>`setgid` ディレクトリにのみ適用されます。 _not_ をファイルに追加します。

さらに、ディレクトリは Web サーバーグループで書き込み可能である必要があります。 これらのディレクトリにコンテンツが存在する可能性があるので、権限を再帰的に追加します。

#### 権限の設定および `setgid`

設定するには `setgid` および開発者モードの権限：

1. コマースサーバーに、ファイルシステムの所有者としてログインするか、ファイルシステムの所有者に切り替えます。
1. 次のコマンドを、次の順序で入力します。

   ```bash
   cd <magento_root>
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

### 本番モードで 2 つのファイル・システムの所有者

サイトを実稼動環境にデプロイする準備が整ったら、セキュリティを強化するために、次のディレクトリ内のファイルから書き込みアクセス権を削除する必要があります。

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

Web サーバー・ユーザーのグループからファイルおよびディレクトリに対する書き込み可能な権限を削除するには、次の手順に従います。

1. Commerce サーバーにログインします。
1. Commerce のインストールディレクトリに移動します。
1. ファイルシステムの所有者として、次のコマンドを入力して実稼動モードに切り替えます。

   ```bash
   bin/magento deploy:mode:set production
   ```

1. 次のコマンドを `root` 権限：

   ```bash
   find app/code lib pub/static app/etc generated/code generated/metadata var/view_preprocessed \( -type d -or -type f \) -exec chmod g-w {} + && chmod o-rwx app/etc/env.php
   ```

#### コードファイルとディレクトリを書き込み可能にする

ファイルとディレクトリを書き込み可能にするには、コンポーネントを更新し、コマースソフトウェアをアップグレードします。

1. Commerce サーバーにログインします。
1. Commerce のインストールディレクトリに移動します。
1. 次のコマンドを入力します。

   ```bash
   find app/code lib var generated vendor pub/static pub/media app/etc \( -type d -or -type f \) -exec chmod g+w {} + && chmod o+rwx app/etc/env.php
   ```
