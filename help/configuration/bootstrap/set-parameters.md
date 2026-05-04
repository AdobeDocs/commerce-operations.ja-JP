---
title: ブートストラップパラメーターの値を設定する
description: Commerce アプリケーションのブートストラップパラメーターを設定する方法について説明します。
exl-id: 4e1e4e5e-e1bc-49a5-8a2a-2e6b91ca9175
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 1%

---

# Bootstrap パラメーター

このトピックでは、Commerce アプリケーションのブートストラップパラメーターの値を設定する方法を説明します。 アプリケーションの初期化とブートストラップの概要[を参照してください](initialization.md)。

次の表では、設定できるブートストラップパラメーターについて説明します。

| Bootstrap パラメーター | 説明 |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | カスタムディレクトリとURL パスを指定します |
| MAGE_PROFILER | 依存関係グラフとHTML プロファイリングを有効にします |

>[!INFO]
>
>- すべてのブートストラップパラメーターが文書化されているわけではありません。
>- これで、[`magento deploy:mode:set {mode}`](../cli/set-mode.md) コマンドを使用してアプリケーションモード（開発者、デフォルト、実稼動環境）を設定できました。

## 環境変数を使用したパラメーターの設定

この節では、環境変数を使用してブートストラップパラメーターの値を設定する方法について説明します。

### アプリケーションモードの設定

ブートストラップ変数をシステム全体の環境変数として指定すると、すべてのプロセスでそれらを使用できるようになります。

例えば、`MAGE_PROFILER` システム環境変数を使用して、次のようにモードを指定できます。

```text
MAGE_PROFILER={firebug|csv|<custom value>}
```

シェル固有のコマンドを使用して変数を設定します。 シェルの構文は異なるので、[unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables)などの参照を参照してください。

CentOSのBash シェルの例：

```shell
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>プロファイラー値を設定した後に`PHP Fatal error`がブラウザーに表示される場合は、web サーバーを再起動します。 その理由は、バイトコードとPHP クラスパスをキャッシュするPHP バイトコードキャッシュに関連している可能性があります。

## ApacheまたはNginxのパラメーターの設定

この節では、ApacheまたはNginxのモードを指定する方法について説明します。

### Nginx設定

_GitHub_&#x200B;の[Nginx サンプル設定](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16)を参照してください。

### Apache .htaccess設定

アプリケーションモードを設定する方法の1つは、`.htaccess`を編集することです。 これにより、Apacheの設定を変更する必要はありません。

Commerce アプリケーションへのエントリーポイントに応じて、次のいずれかの場所で`.htaccess`を変更できます。

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**変数を設定するには**:

1. 上記のファイルのいずれかをテキストエディターで開き、目的の設定を追加またはコメント解除します。

   例えば、[mode](application-modes.md)を指定するには、次のコメントを解除します。

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. `MAGE_PROFILER`の値を次のいずれかに設定します。

   ```text
   firebug
   csvfile
   <custom value>
   ```

1. 変更を`.htaccess`に保存します。変更を有効にするためにApacheを再起動する必要はありません。

### Apache設定

Apache Web サーバーでは、`mod_env` ディレクティブを使用したアプリケーションモードの設定をサポートしています。

Apache `mod_env` ディレクティブは、[Apache バージョン 2.2](https://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv)と[Apache バージョン 2.4](https://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv)で若干異なります。

次の手順は、Apache仮想ホストでアプリケーションモードを設定する方法を示しています。 これは`mod_env` ディレクティブを使用する唯一の方法ではありません。詳しくは、Apache ドキュメントを参照してください。

>[!TIP]
>
>次の節では、仮想ホストを既に設定していることを前提としています。 まだ使用していない場合は、[このDigitalOcean チュートリアル &#x200B;](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts)などのリソースを参照してください。

**Ubuntu**&#x200B;でApacheのブートストラップ変数を指定するには：

1. `root`権限を持つユーザーとして、仮想ホスト設定ファイルをテキストエディターで開きます。

   例えば、仮想ホストの名前が`my.magento`の場合，

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
1. 仮想ホストをまだ有効にしていない場合は、次の手順を実行します。

   ```shell
   a2ensite <virtual host config file name>
   ```

   以下に例を挙げます。

   ```shell
   a2ensite my.magento.conf
   ```

1. モードを設定したら、web サーバーを再起動します。

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

>[!TIP]
>
>このセクションでは、仮想ホストが既に設定されていることを前提としています。 まだ使用していない場合は、[このDigitalOcean チュートリアル &#x200B;](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6)などのリソースを参照してください。

**CentOS**&#x200B;でApacheのブートストラップ変数を指定するには：

1. `root`権限を持つユーザーは、テキストエディターで`/etc/httpd/conf/httpd.conf`を開きます。

1. 仮想ホスト設定の任意の場所で、次の行を追加します。

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   以下に例を挙げます。

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. 変更を保存し、テキストエディターを終了します。

1. モードを設定したら、web サーバーを再起動します。

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

