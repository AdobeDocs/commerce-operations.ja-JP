---
title: ブートストラップパラメーターの値を設定
description: Commerce アプリケーションのブートストラップパラメーターを設定する方法を説明します。
exl-id: 4e1e4e5e-e1bc-49a5-8a2a-2e6b91ca9175
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 1%

---

# Bootstrapパラメーター

このトピックでは、Commerce アプリケーションのブートストラップパラメーターの値を設定する方法について説明します。 参照： [アプリケーションの初期化とブートストラップの概要](initialization.md).

次の表に、設定可能なブートストラップパラメーターを示します。

| Bootstrapパラメーター | 説明 |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | カスタムディレクトリと URL パスを指定します |
| MAGE_PROFILER | 依存性グラフとHTML・プロファイリングを使用可能にします。 |

>[!INFO]
>
>- すべての bootstrap パラメーターがドキュメントに記載されているわけではありません。
>- 以下を使用してアプリケーションモード（開発者、デフォルト、実稼動）を設定しました。 [`magento deploy:mode:set {mode}`](../cli/set-mode.md) コマンド。

## 環境変数を使用したパラメーターの設定

この節では、環境変数を使用してブートストラップパラメーターの値を設定する方法について説明します。

### アプリケーションモードの設定

Bootstrap 変数をシステム全体の環境変数として指定すると、すべてのプロセスでその変数を使用できます。

例えば、 `MAGE_PROFILER` モードを次のように指定するためのシステム環境変数。

```terminal
MAGE_PROFILER={firebug|csv|<custom value>}
```

シェル固有のコマンドを使用して変数を設定します。 シェルは構文が異なるので、のようなリファレンスを参照してください。 [unix.stackexchange.com][unix-stackx].

CentOS 用の bash シェルの例：

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>If a `PHP Fatal error` プロファイラの値を設定した後、ブラウザに表示され、Web サーバーを再起動します。 その理由は、バイトコードと PHP クラスパスをキャッシュする PHP バイトコードのキャッシュに関連している可能性があります。

## Apache または Nginx のパラメーターを設定する

この節では、Apache または Nginx のいずれかのモードを指定する方法について説明します。

### Nginx 設定

を参照してください。 [Nginx サンプル構成] 日付： _GitHub_.

### Apache .htaccess 設定

アプリケーションモードを設定する 1 つの方法は、次を編集することです。 `.htaccess`. これにより、Apache 設定を変更する必要がなくなります。

次を変更できます `.htaccess` Commerce アプリケーションへのエントリポイントに応じて、次のいずれかの場所で行います。

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**変数を設定するには**:

1. 上記のファイルをテキストエディターで開き、目的の設定を追加またはコメント解除します。

   例えば、を指定します。 [モード](application-modes.md)で、以下のコメントを解除します。

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. 次の値を設定 `MAGE_PROFILER` を次のいずれかに変更します。

   ```terminal
   firebug
   csvfile
   <custom value>
   ```

1. 変更をに保存します。 `.htaccess`ただし、変更を有効にするために Apache を再起動する必要はありません。

### Apache 設定

Apache web サーバーは、を使用したアプリケーションモードの設定をサポートしています。 `mod_env` ディレクティブ。

Apache `mod_env` ディレクティブが次の点で若干異なる： [Apache バージョン 2.2] および [Apache バージョン 2.4].

Apache 仮想ホストでアプリケーションモードを設定する手順を以下に示します。 これは唯一の使い方ではありません `mod_env` ディレクティブ。詳しくは Apache ドキュメントを参照してください。

>[!TIP]
>
>次の節では、仮想ホストが既に設定されていることを前提としています。 まだインストールされていない場合は、次のようなリソースを参照してください [この DigitalOcean チュートリアル](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts).

**Ubuntu で Apache のブートストラップ変数を指定するには**:

1. を使用した As a ユーザー `root` 仮想ホスト構成ファイルをテキスト・エディタで開きます。

   例えば、仮想ホストの名前がの場合 `my.magento`,

   - Apache 2.4: `vim /etc/apache2/sites-available/my.magento.conf`
   - Apache 2.2: `vim /etc/apache2/sites-available/my.magento`

1. 仮想ホスト設定の任意の場所で、次の行を追加します。

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   以下に例を挙げます。

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. 変更を保存し、テキストエディターを終了します。
1. 仮想ホストをまだ有効にしていない場合は、有効にします。

   ```bash
   a2ensite <virtual host config file name>
   ```

   以下に例を挙げます。

   ```bash
   a2ensite my.magento.conf
   ```

1. モードを設定した後、web サーバーを再起動します。

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

>[!TIP]
>
>この節では、仮想ホストが既に設定されていることを前提としています。 まだインストールされていない場合は、次のようなリソースを参照してください [この DigitalOcean チュートリアル](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6).

**CentOS 上の Apache のブートストラップ変数を指定するには**:

1. を使用した As a ユーザー `root` 権限、開く `/etc/httpd/conf/httpd.conf` テキストエディター。

1. 仮想ホスト設定の任意の場所で、次の行を追加します。

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   以下に例を挙げます。

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. 変更を保存し、テキストエディターを終了します。

1. モードを設定した後、web サーバーを再起動します。

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

<!-- link definitions -->

[Apache バージョン 2.2]: https://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv
[Apache バージョン 2.4]: https://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv
[Nginx サンプル構成]: https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16
[unix-stackx]: https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables
