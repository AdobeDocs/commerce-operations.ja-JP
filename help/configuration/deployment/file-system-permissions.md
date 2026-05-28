---
title: ファイルシステムアクセス権限
description: 開発用および実稼動用システム用のCommerce アプリケーションファイルシステムのオーナーを設定する方法を参照してください。
feature: Configuration, Roles/Permissions
exl-id: 95b27db9-5247-4f58-a9af-1590897d73db
source-git-commit: f9a135fc63574ccbecd3f564a87fc5c4ac03f009
workflow-type: tm+mt
source-wordcount: '887'
ht-degree: 0%

---

# ファイルシステムアクセス権限

この節では、開発用および実稼動用のCommerce ファイルシステムのオーナーを設定する方法について説明します。 続行する前に、[ ファイルシステムの所有権と権限の概要](../../installation/prerequisites/file-system/overview.md)で説明されている概念を確認してください。

このトピックでは、Commerceの開発および運用システムに焦点を当てます。 Commerceをインストールする場合は、[ インストール前の所有権と権限の設定](../../installation/prerequisites/file-system/configure-permissions.md)を参照してください。

以下の節では、1人または2人のファイルシステム所有者の要件について説明します。 つまり次の式になります。

- **1人のユーザー** – 通常、共有ホスティングプロバイダーで必要です。これにより、サーバー上の1人のユーザーのみにアクセスできます。このユーザーはログインし、FTPを使用してファイルを転送でき、このユーザーはweb サーバーも実行します。

- **2人のユーザー** – 独自のCommerce サーバーを実行する場合は、2人のユーザーをお勧めします。1人はファイルを転送し、コマンドラインユーティリティを実行するユーザーで、もう1人はWeb サーバーソフトウェア用の別のユーザーです。 可能であれば、より安全であるため、これが望ましいです。

  代わりに、次のユーザーが別々に存在します。

   - 管理者とストアフロントを実行するweb サーバーユーザー。

   - _コマンドラインユーザー_&#x200B;は、サーバーへのログインに使用できるローカルユーザーアカウントです。 このユーザーは、Commerce cron ジョブとコマンドラインユーティリティを実行します。

## 共有ホスティングの実稼動ファイルシステムの所有権（1 ユーザー）

One-owner設定を使用するには、web サーバーを実行するのと同じユーザーとしてCommerce サーバーにログインする必要があります。 これは、共有ホスティングの典型的な例です。

ファイルシステムの所有者が1人ではセキュリティが低いため、可能であれば、共有ホスティングではなくプライベートサーバーにCommerceを実稼動環境にデプロイすることをお勧めします。

### デフォルトモードまたは開発者モードの所有者を1人に設定

デフォルトまたは開発者モードでは、次のディレクトリをユーザーが書き込める必要があります。

- `vendor`
- `app/etc`
- `pub/static`
- `var`
- その他の静的リソース
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

これらの権限は、コマンドラインまたは共有ホスティングプロバイダーが提供するファイルマネージャーアプリケーションを使用して設定できます。

### 実稼動モード用に1人の所有者を設定する

サイトを実稼動環境にデプロイする準備ができたら、セキュリティを強化するために、次のディレクトリのファイルから書き込みアクセス権を削除する必要があります。

- `vendor`
- `app/code`
- `app/etc`
- `pub/static`
- その他の静的リソース
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

コンポーネントの更新、新しいコンポーネントのインストール、またはCommerce ソフトウェアのアップグレードを行うには、前述のすべてのディレクトリが読み取り/書き込みである必要があります。

#### コードファイルとディレクトリを読み取り専用にする

Web サーバーユーザーのグループからファイルとディレクトリへの書き込み権限を削除するには：

1. Commerce サーバーにログインします。

1. Commerceのインストールディレクトリに移動します。

1. 実稼動モードに変更します。

   ```shell
   bin/magento deploy:mode:set production
   ```

1. 次のディレクトリへの書き込み権限を削除します。

   ```shell
   find app/code var/view_preprocessed vendor pub/static app/etc generated/code generated/metadata \( -type f -or -type d \) -exec chmod u-w {} + && chmod o-rwx app/etc/env.php
   ```

1. コマンドラインツールを実行可能にします。

   ```shell
   chmod u+x bin/magento
   ```

#### コードファイルとディレクトリを書き込み可能にする

コンポーネントを更新し、Commerce ソフトウェアをアップグレードできるように、ファイルとディレクトリを書き込み可能にするには、次の手順を実行します。

1. Commerce サーバーにログインします。
1. Commerceのインストールディレクトリに移動します。
1. 次のコマンドを入力します。

   ```shell
   chmod -R u+w .
   ```

### オプションで`magento_umask`を設定します

_インストールガイド_&#x200B;の「[ オプションでumask](../../installation/next-steps/set-umask.md)を設定する」を参照してください。

## プライベートホスティングの実稼動ファイルシステムの所有権（2人のユーザー）

独自のサーバー（ホスティングプロバイダーのプライベートサーバー設定を含む）を使用する場合は、次の2つのユーザーがあります。

- 管理者とストアフロントを実行する&#x200B;**web サーバーユーザー**。

  Linux システムは通常、このユーザー用のシェルを提供しません。Commerce サーバーにweb サーバーユーザーとしてログインしたり、web サーバーユーザーに切り替えたりすることはできません。

- **コマンドラインユーザー**&#x200B;は、としてCommerce サーバーにログインするか、に切り替えます。

  Commerceでは、このユーザーを使用してCLI コマンドとcronを実行します。

  >[!INFO]
  >
  >コマンドラインユーザーは&#x200B;_ファイルシステム所有者_&#x200B;とも呼ばれます。

これらのユーザーは同じファイルにアクセスする必要があるため、両方が属する[共有グループ ](../../installation/prerequisites/file-system/configure-permissions.md#about-the-shared-group)を作成することをお勧めします。 次の手順では、既にこの操作を行っていることを前提としています。

次のいずれかのセクションを参照してください。

- デベロッパーモードまたはデフォルトモードの2人のファイルシステム所有者
- 実稼動モードの2つのファイルシステム所有者

### デフォルトモードまたは開発者モードの2つの所有者を設定する

次のディレクトリ内のファイルは、デベロッパーモードとデフォルトモードの両方のユーザーが書き込み可能である必要があります。

- `var`
- `generated`
- `pub/static`
- `pub/media`
- `app/etc`

権限が常に親ディレクトリから継承されるように、ディレクトリに[`setgid`](https://linuxconfig.org/how-to-use-special-permissions-the-setuid-setgid-and-sticky-bits) ビットを設定します。

>[!INFO]
>
>`setgid`はディレクトリにのみ適用され、ファイルには&#x200B;_ではなく_&#x200B;が適用されます。

さらに、ディレクトリはweb サーバーグループによって書き込み可能である必要があります。 コンテンツはこれらのディレクトリに存在する可能性があるので、権限を再帰的に追加します。

#### 権限と`setgid`を設定

開発者モードの`setgid`と権限を設定するには：

1. ファイルシステムの所有者としてCommerce サーバーにログインするか、切り替えます。
1. 次のコマンドを次の順序で入力します。

   ```shell
   cd <magento_root>
   ```

   ```shell
   find var generated pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```shell
   find var generated pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

### 実稼動モードの2つのファイルシステム所有者

サイトを実稼動環境にデプロイする準備ができたら、セキュリティを強化するために、次のディレクトリのファイルから書き込みアクセス権を削除する必要があります。

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

Web サーバーユーザーのグループからファイルやディレクトリへの書き込み可能な権限を削除するには：

1. Commerce サーバーにログインします。
1. Commerceのインストールディレクトリに移動します。
1. ファイルシステムの所有者として、次のコマンドを入力して実稼動モードに変更します。

   ```shell
   bin/magento deploy:mode:set production
   ```

1. `root`権限を持つユーザーとして次のコマンドを入力します。

   ```shell
   find app/code lib pub/static app/etc generated/code generated/metadata var/view_preprocessed \( -type d -or -type f \) -exec chmod g-w {} + && chmod o-rwx app/etc/env.php
   ```

#### コードファイルとディレクトリを書き込み可能にする

コンポーネントを更新し、Commerce ソフトウェアをアップグレードできるように、ファイルとディレクトリを書き込み可能にするには、次の手順を実行します。

1. Commerce サーバーにログインします。
1. Commerceのインストールディレクトリに移動します。
1. 次のコマンドを入力します。

   ```shell
   find app/code lib var generated vendor pub/static pub/media app/etc \( -type d -or -type f \) -exec chmod g+w {} + && chmod o+rwx app/etc/env.php
   ```
