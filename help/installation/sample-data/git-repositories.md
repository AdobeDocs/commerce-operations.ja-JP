---
title: サンプルデータ Git リポジトリーの複製
description: Git リポジトリーを複製してAdobe CommerceおよびMagento Open Sourceサンプルデータをインストールするには、次の手順に従います。
source-git-commit: 3692dcfd5b50c2f036b005d40a22db061b9ea5fd
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 0%

---


# サンプルデータ Git リポジトリーの複製

このトピックでは、Magento Open SourceGitHub リポジトリーを複製した場合の、サンプルデータの複製および追加方法について説明します。 この方法は、開発者 (Magento Open Sourceコードベースへの貢献を計画している開発者 ) への貢献のみを目的としています。

投稿者でない場合は、ページの左側にある目次に表示される他のオプションの 1 つを選択します。

貢献する開発者は、この方法を使用してサンプルデータをインストールできます *のみ* 次の値が true の場合：

* Magento Open Source
* あなた [GitHub リポジトリを複製しました](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

>[!WARNING]
>
>サンプルデータは `develop` ブランチ（より最新）またはリリースされたブランチ ( `2.4` （より安定）。 リリースされたブランチはより安定しているので、使用することをお勧めします。 リポジトリにコードをコントリビュートする場合に、最新のコードが必要な場合は、 `develop` 分岐。 選択するブランチに関係なく、次の操作を行う必要があります。 [複製](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) Magento Open SourceGitHub リポジトリの対応するブランチ。 例えば、 `develop` ブランチを使用できます *のみ* Magento Open Source `develop` 分岐。

## サンプルデータリポジトリのクローン

この項では、サンプル・データ・リポジトリを複製してサンプル・データをインストールする方法について説明します。 次のいずれかの方法で、サンプルデータリポジトリのクローンを作成できます。

* を使用して複製 [SSH プロトコル](#clone-with-ssh)
* を使用して複製 [HTTPS プロトコル](#clone-with-https)

### SSH で複製

SSH プロトコルを使用してサンプルデータ GitHub リポジトリのクローンを作成するには：

1. Web ブラウザーで、 [サンプルデータリポジトリ](https://github.com/magento/magento2-sample-data).
1. ブランチ名の横にある **SSH** を選択します。
1. クリック **クリップボードにコピー**

   次の図に例を示します。

   ![SSH を使用して GitHub リポジトリを複製する](../../assets/installation/install_mage2_clone-ssh.png)

1. Web サーバーのドキュメントルートディレクトリに移動します。

   Ubuntu の場合は、通常、 `/var/www` CentOS の場合は `/var/www/html`.

1. 入力 `git clone` 前に取得した値を貼り付けます。

   次に例を示します。

   ```bash
   git clone git@github.com:magento/magento2-sample-data.git
   ```

1. リポジトリがサーバー上で複製されるのを待ちます。

   >[!NOTE]
   >
   >次のエラーが表示される場合は、 [SSH キーを共有しました](https://docs.github.com/articles/generating-ssh-keys/) GitHub の場合：<br>

   ```terminal
   Cloning into 'magento2'...
   Permission denied (publickey).
   fatal: The remote end hung up unexpectedly
   ```

1. メインから使用したブランチに対応するサンプルデータリポジトリのブランチを確認してください。 `magento2` リポジトリ。

   例：

   次の `2.4-develop` Magento Open SourceGitHub リポジトリのブランチ。Sample Data ブランチは、 `2.4-develop`.

   正しいブランチをチェックアウトするには、サンプルのデータリポジトリのルートディレクトリから次のコマンドを実行します ( 必要に応じて `2.4-develop` ブランチ ):

   ```bash
   git checkout 2.4-develop
   ```

1. 置換文字列 `<app_root>`.
1. 次のコマンドを入力して、サンプルデータが正しく機能するように、複製したファイル間にシンボリックリンクを作成します。

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

1. コマンドが完了するまで待ちます。

1. 詳しくは、 [ファイル・システムの権限と所有権を設定](#set-file-system-ownership-and-permissions).

1. 次のコマンドを実行します。

   ```bash
   bin/magento setup:upgrade
   ```

### HTTPS で複製

HTTPS プロトコルを使用してサンプルデータ GitHub リポジトリのクローンを作成するには：

1. Web ブラウザーで、 [サンプルデータリポジトリ](https://github.com/magento/magento2-sample-data).
1. ページの右側の、 **複製 URL** フィールド、クリック **HTTPS**.
1. クリック **クリップボードにコピー**.

   次の図に例を示します。

   ![HTTPS を使用して GitHub リポジトリを複製する](../../assets/installation/install_mage2_clone-https.png)

1. Web サーバーのドキュメントルートディレクトリに移動します。

   Ubuntu の場合は、通常、 `/var/www` CentOS の場合は `/var/www/html`.

1. 入力 `git clone` 前に取得した値を貼り付けます。

   次に例を示します。

   ```bash
   git clone https://github.com/magento/magento2-sample-data.git
   ```

1. リポジトリがサーバー上で複製されるのを待ちます。
1. メインから使用したブランチに対応するサンプルデータリポジトリのブランチを確認してください。 `magento2` リポジトリ。

   例：

   次の `2.4-develop` Magento Open SourceGitHub リポジトリのブランチ。Sample Data ブランチは、 `2.4-develop`.

   正しいブランチをチェックアウトするには、サンプルのデータリポジトリのルートディレクトリから次のコマンドを実行します ( 必要に応じて `2.4-develop` ブランチ ):

   ```bash
   git checkout 2.4-develop
   ```

1. 置換文字列 `<magento_root>`.
1. 次のコマンドを入力して、サンプルデータが正しく機能するように、複製したファイル間にシンボリックリンクを作成します。

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

   以下に例を挙げます。

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="/var/www/magento2"
   ```

1. コマンドが完了するまで待ちます。
1. 次の節を参照してください。

>[!WARNING]
>
>サンプルデータをインストールする場合 *後* Adobe CommerceまたはMagento Open Sourceをインストールする場合は、次のコマンドを実行して、データベースとスキーマを更新する必要があります。
>
>
```bash
><magento_root>/bin/magento setup:upgrade
>```

## ファイル・システムの所有権と権限を設定

これは、 `php build-sample-data.php` スクリプトは、サンプル・データ・リポジトリとMagento Open Source・リポジトリの間にシンボリック・リンクを作成します。サンプル・データ・リポジトリでファイル・システムの権限と所有権を設定する必要があります。 そうしないと、ストアフロントにアクセス中にエラーが発生します。

サンプル・データ・リポジトリにファイル・システムの権限と所有権を設定するには、次の手順に従います。

1. サンプルのデータ複製ディレクトリに変更します。
1. 所有権を設定：

   ```bash
   chown -R :<your web server group name> .
   ```

   典型的な例：

   * CentOS: `chown -R :apache .`

   * Ubuntu: `chown -R :www-data .`

1. 権限の設定：

   ```bash
   find . -type d -exec chmod g+ws {} +
   ```

1. 静的ファイルをクリア：

   ```bash
   cd <your Magento Open Source install dir>
   ```

   ```bash
   rm -rf var/cache/* var/page_cache/* generated/*
   ```

## サンプルデータのインストールを完了します。

{{$include /help/_includes/sample-data-complete.md}}
