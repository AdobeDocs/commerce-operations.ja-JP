---
title: ブートストラップパラメーターの値を設定
description: Commerce アプリケーションのブートストラップパラメーターを設定する方法を説明します。
exl-id: 4e1e4e5e-e1bc-49a5-8a2a-2e6b91ca9175
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 1%

---

# Bootstrapパラメーター

このトピックでは、Commerce アプリケーションのブートストラップパラメーターの値を設定する方法について説明します。 [ アプリケーションの初期化とブートストラップの概要 ](initialization.md) を参照してください。

次の表に、設定可能なブートストラップパラメーターを示します。

| Bootstrapパラメーター | 説明 |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | カスタムディレクトリと URL パスを指定します |
| MAGE_PROFILER | 依存性グラフとHTML・プロファイリングを使用可能にします。 |

>[!INFO]
>
>- すべての bootstrap パラメーターがドキュメントに記載されているわけではありません。
>- ここで、[`magento deploy:mode:set {mode}`](../cli/set-mode.md) コマンドを使用してアプリケーションモード（開発者、デフォルト、実稼動）を設定します。

## 環境変数を使用したパラメーターの設定

この節では、環境変数を使用してブートストラップパラメーターの値を設定する方法について説明します。

### アプリケーションモードの設定

Bootstrap 変数をシステム全体の環境変数として指定すると、すべてのプロセスでその変数を使用できます。

例えば、`MAGE_PROFILER` システム環境変数を使用して、次のようにモードを指定できます。

```
MAGE_PROFILER={firebug|csv|<custom value>}
```

シェル固有のコマンドを使用して変数を設定します。 シェルは構文が異なるため、[unix.stackexchange.com][unix-stackx] などのリファレンスを参照してください。

CentOS 用の bash シェルの例：

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>プロファイラの値を設定した後にブラウザに `PHP Fatal error` が表示された場合は、Web サーバを再起動します。 その理由は、バイトコードと PHP クラスパスをキャッシュする PHP バイトコードのキャッシュに関連している可能性があります。

## Apache または Nginx のパラメーターを設定する

この節では、Apache または Nginx のいずれかのモードを指定する方法について説明します。

### Nginx 設定

詳しくは、[GitHub _の_ Nginx サンプル設定 ] を参照してください。

### Apache .htaccess 設定

アプリケーションモードを設定する 1 つの方法は、`.htaccess` を編集することです。 これにより、Apache 設定を変更する必要がなくなります。

Commerce アプリケーションへのエントリポイントに応じて、次のいずれかの場所で `.htaccess` を変更できます。

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**変数を設定するには**:

1. 上記のファイルをテキストエディターで開き、目的の設定を追加またはコメント解除します。

   例えば、[mode](application-modes.md) を指定するには、次のコメントを解除します。

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. `MAGE_PROFILER` の値を次のいずれかに設定します。

   ```
   firebug
   csvfile
   <custom value>
   ```

1. 変更内容を `.htaccess` に保存します。変更内容を有効にするために Apache を再起動する必要はありません。

### Apache 設定

Apache web サーバーは、`mod_env` ディレクティブを使用してアプリケーションモードを設定できます。

Apache `mod_env` ディレクティブは [Apache バージョン 2.2] と [Apache バージョン 2.4] ではやや異なります。

Apache 仮想ホストでアプリケーションモードを設定する手順を以下に示します。 `mod_env` ディレクティブを使用する方法は、これだけではありません。詳しくは、Apache ドキュメントを参照してください。

>[!TIP]
>
>次の節では、仮想ホストが既に設定されていることを前提としています。 まだ公開されていない場合は、[ この DigitalOcean チュートリアル ](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts) などのリソースを参照してください。

**Ubuntu 上の Apache のブートストラップ変数を指定するには**:

1. `root` 権限を持つユーザーとして、仮想ホスト設定ファイルをテキストエディターで開きます。

   例えば、仮想ホストの名前が `my.magento` の場合、

   - Apache 2.4: `vim /etc/apache2/sites-available/my.magento.conf`
   - Apache 2.2:`vim /etc/apache2/sites-available/my.magento`

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
>この節では、仮想ホストが既に設定されていることを前提としています。 まだ公開されていない場合は、[ この DigitalOcean チュートリアル ](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6) などのリソースを参照してください。

**CentOS 上の Apache のブートストラップ変数を指定するには**:

1. `root` 権限を持つユーザーとして、`/etc/httpd/conf/httpd.conf` をテキストエディターで開きます。

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
