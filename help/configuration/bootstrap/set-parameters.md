---
title: ブートストラップパラメータの値を設定する
description: コマースアプリケーションのブートストラップパラメーターを設定する方法を説明します。
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Bootstrapパラメーター

このトピックでは、コマースアプリケーションのブートストラップパラメーターの値を設定する方法を説明します。 詳しくは、 [アプリケーションの初期化とブートストラップの概要](initialization.md).

次の表に、設定できるブートストラップパラメータを示します。

| Bootstrapパラメータ | 説明 |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | カスタムディレクトリと URL パスを指定します |
| MAGE_PROFILER | 依存関係グラフとHTMLプロファイルを有効化 |

>[!INFO]
>
>- ブートストラップパラメータの一部が記載されているわけではありません。
>- これで、 [`magento deploy:mode:set {mode}`](../cli/set-mode.md) コマンドを使用します。


## 環境変数を使用したパラメーターの設定

この項では、環境変数を使用してブートストラップパラメータの値を設定する方法について説明します。

### アプリケーションモードの設定

ブートストラップ変数は、システム全体の環境変数として指定できます。これにより、すべてのプロセスで使用できます。

例えば、 `MAGE_PROFILER` システム環境変数を使用して、次のようにモードを指定します。

```terminal
MAGE_PROFILER={firebug|csv|<custom value>}
```

シェル固有のコマンドを使用して変数を設定します。 シェルの構文は異なるので、次のような参照を参照してください。 [unix.stackexchange.com][unix-stackx].

CentOS 用の Bash シェルの例：

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>次の場合、 `PHP Fatal error` は、プロファイラー値を設定した後、Web サーバーを再起動した後にブラウザに表示されます。 この理由は、PHP のバイトコードキャッシュに関連している可能性があります。このキャッシュは、バイトコードと PHP クラスパスをキャッシュします。

## Apache または Nginx のパラメーターの設定

この節では、Apache または Nginx のモードを指定する方法について説明します。

### Nginx 設定

詳しくは、 [Nginx サンプル設定] オン _GitHub_.

### Apache .htaccess 設定

アプリケーションモードを設定する 1 つの方法は、 `.htaccess`. これにより、Apache の設定を変更する必要がなくなります。

次の項目を変更できます。 `.htaccess` を次の場所に置き、Commerce アプリケーションのエントリポイントに応じて、

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**変数を設定するには**:

1. 前述のファイルをテキストエディターで開き、必要な設定を追加またはコメント解除します。

   例えば、 [mode](application-modes.md)、次のコメントを解除します。

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. 値を `MAGE_PROFILER` を次のいずれかに変更します。

   ```terminal
   firebug
   csvfile
   <custom value>
   ```

1. 変更をに保存します。 `.htaccess`;変更を有効にするために、Apache を再起動する必要はありません。

### Apache 設定

Apache Web サーバーでは、 `mod_env` ディレクティブ。

Apache `mod_env` 指示が～で少し異なる [Apache バージョン 2.2] および [Apache バージョン 2.4].

次の手順は、Apache 仮想ホストでアプリケーションモードを設定する方法を示しています。 これが唯一の使用方法ではありません `mod_env` 指令；詳しくは、Apache のドキュメントを参照してください。

>[!TIP]
>
>次の節では、仮想ホストが既に設定されていることを前提としています。 まだの場合は、次のようなリソースを参照してください。 [この DigitalOcean チュートリアル](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts).

**Ubuntu 上の Apache のブートストラップ変数を指定するには**:

1. を使用して `root` 権限を設定し、仮想ホスト設定ファイルをテキストエディターで開きます。

   例えば、仮想ホストの名前が `my.magento`,

   - Apache 2.4: `vim /etc/apache2/sites-available/my.magento.conf`
   - Apache 2.2: `vim /etc/apache2/sites-available/my.magento`

1. 仮想ホスト設定の任意の場所に、次の行を追加します。

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   以下に例を挙げます。

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. 変更を保存し、テキストエディターを終了します。
1. 仮想ホストを有効にする（まだ有効にしていない場合）。

   ```bash
   a2ensite <virtual host config file name>
   ```

   以下に例を挙げます。

   ```bash
   a2ensite my.magento.conf
   ```

1. モードを設定した後、Web サーバーを再起動します。

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

>[!TIP]
>
>この節では、仮想ホストが既に設定されていることを前提としています。 まだの場合は、次のようなリソースを参照してください。 [この DigitalOcean チュートリアル](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6).

**CentOS 上の Apache のブートストラップ変数を指定するには**:

1. を使用して `root` 権限、開く `/etc/httpd/conf/httpd.conf` をクリックします。

1. 仮想ホスト設定の任意の場所に、次の行を追加します。

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   以下に例を挙げます。

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. 変更を保存し、テキストエディターを終了します。

1. モードを設定した後、Web サーバーを再起動します。

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

<!-- link definitions -->

[Apache バージョン 2.2]: https://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv
[Apache バージョン 2.4]: https://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv
[Nginx サンプル設定]: https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16
[unix-stackx]: https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables
