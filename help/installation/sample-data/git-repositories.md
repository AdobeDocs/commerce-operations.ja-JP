---
title: サンプルデータ Git リポジトリのクローン
description: Git リポジトリをクローンしてAdobe Commerce サンプルデータをインストールするには、次の手順に従います。
exl-id: 748eee30-2821-457d-9c1c-62ede8bc0510
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 0%

---

# サンプルデータ Git リポジトリのクローン

このトピックでは、Magento Open Source GitHub リポジトリのクローンを作成した場合に、サンプルデータをクローンして追加する方法について説明します。 この方法は、開発者（Magento Open Sourceコードベースにコントリビューションする予定の開発者）のみを対象としています。

コントリビューションを行う開発者でない場合は、ページの左側にある目次に表示されている他のオプションの 1 つを選択します。

コントリビューション開発者は、この方法を使用してサンプルデータをインストールできます *のみ* 次の条件に当てはまる場合：

* Magento Open Sourceを使用している場合
* あなた [github リポジトリのクローンを作成しました](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

>[!WARNING]
>
>サンプルデータは、次のいずれかで使用できます `develop` 分岐（より最新）またはリリースされた分岐（など） `2.4` （より安定）。 リリース済みのブランチは安定性が高いので、使用することをお勧めします。 リポジトリにコードを提供していて、最新のコードが必要な場合は、を使用します `develop` 分岐。 選択するブランチに関係なく、次の操作を行う必要があります [クローン](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) Magento Open Source GitHub リポジトリの対応するブランチ。 例えば、のサンプルデータです `develop` ブランチを使用できます *のみ* （Magento Open Sourceを使用） `develop` 分岐。

## サンプルデータリポジトリのクローンの作成

この項では、サンプル・データ・リポジトリをクローニングしてサンプル・データをインストールする方法について説明します。 サンプルデータリポジトリは、次のいずれかの方法でクローンできます。

* を使用したクローン [SSH プロトコル](#clone-with-ssh)
* を使用したクローン [HTTPS プロトコル](#clone-with-https)

### SSH によるクローン

SSH プロトコルを使用してサンプルデータ GitHub リポジトリのクローンを作成するには：

1. Web ブラウザーで、 [サンプルデータリポジトリ](https://github.com/magento/magento2-sample-data).
1. 支店の名前の横にある「」をクリックします **SSH** リストから。
1. クリック **クリップボードにコピー**

   次の図に例を示します。

   ![SSH を使用して GitHub リポジトリを複製します](../../assets/installation/install_mage2_clone-ssh.png)

1. を web サーバーの docroot ディレクトリに変更します。

   通常、Ubuntu の場合はです `/var/www` また、CentOS の場合はです。 `/var/www/html`.

1. Enter `git clone` そして、以前に取得した値を貼り付けます。

   次に例を示します。

   ```bash
   git clone git@github.com:magento/magento2-sample-data.git
   ```

1. リポジトリがサーバー上でクローンされるのを待ちます。

   >[!NOTE]
   >
   >次のエラーが表示される場合は、以下を確認します [が SSH キーを共有しました](https://docs.github.com/articles/generating-ssh-keys/) github を使用する場合：<br>

   ```terminal
   Cloning into 'magento2'...
   Permission denied (publickey).
   fatal: The remote end hung up unexpectedly
   ```

1. メインから使用したブランチに対応する、サンプルデータリポジトリのブランチをチェックアウトします `magento2` リポジトリ。

   例：

   を使用した場合 `2.4-develop` Magento Open Source GitHub リポジトリのブランチである、Sample Data ブランチは、 `2.4-develop`.

   正しいブランチをチェックアウトするには、サンプルデータリポジトリのルートディレクトリから次のコマンドを実行します（必要な場合）。 `2.4-develop` ブランチ）:

   ```bash
   git checkout 2.4-develop
   ```

1. をに変更 `<app_root>`.
1. 次のコマンドを入力して、クローンを作成したファイル間にシンボリックリンクを作成し、サンプルデータが正しく動作するようにします。

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

1. コマンドが完了するまで待ちます。

1. 参照： [ファイルシステムの権限と所有権の設定](#set-file-system-ownership-and-permissions).

1. 次のコマンドを実行します。

   ```bash
   bin/magento setup:upgrade
   ```

### HTTPS を使用してクローン

HTTPS プロトコルを使用してサンプルデータ GitHub リポジトリを複製するには：

1. Web ブラウザーで、 [サンプルデータリポジトリ](https://github.com/magento/magento2-sample-data).
1. ページの右側で、の **複製 URL** フィールド、クリック **HTTPS**.
1. クリック **クリップボードにコピー**.

   次の図に例を示します。

   ![HTTPS を使用して GitHub リポジトリを複製します](../../assets/installation/install_mage2_clone-https.png)

1. を web サーバーの docroot ディレクトリに変更します。

   通常、Ubuntu の場合はです `/var/www` また、CentOS の場合はです。 `/var/www/html`.

1. Enter `git clone` そして、以前に取得した値を貼り付けます。

   次に例を示します。

   ```bash
   git clone https://github.com/magento/magento2-sample-data.git
   ```

1. リポジトリがサーバー上でクローンされるのを待ちます。
1. メインから使用したブランチに対応する、サンプルデータリポジトリのブランチをチェックアウトします `magento2` リポジトリ。

   例：

   を使用した場合 `2.4-develop` Magento Open Source GitHub リポジトリのブランチである、Sample Data ブランチは、 `2.4-develop`.

   正しいブランチをチェックアウトするには、サンプルデータリポジトリのルートディレクトリから次のコマンドを実行します（必要な場合）。 `2.4-develop` ブランチ）:

   ```bash
   git checkout 2.4-develop
   ```

1. をに変更 `<magento_root>`.
1. 次のコマンドを入力して、クローンを作成したファイル間にシンボリックリンクを作成し、サンプルデータが正しく動作するようにします。

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
>サンプルデータをインストールする場合 *後* Adobe Commerceをインストールする際は、次のコマンドを実行してデータベースとスキーマを更新する必要もあります。
>
>```bash
><magento_root>/bin/magento setup:upgrade
>```

## ファイルシステムの所有権と権限の設定

なぜなら `php build-sample-data.php` スクリプトは、サンプルデータリポジトリとMagento Open Sourceリポジトリの間にシンボリックリンクを作成します。ファイルシステムの権限と所有権は、サンプルデータリポジトリで設定する必要があります。 これをおこなわないと、ストアフロントへのアクセスでエラーが発生します。

サンプルデータリポジトリに対するファイルシステムの権限と所有権を設定するには、次の手順に従います。

1. サンプルデータクローンディレクトリに移動します。
1. 所有権の設定：

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

1. 静的ファイルのクリア：

   ```bash
   cd <your Magento Open Source install dir>
   ```

   ```bash
   rm -rf var/cache/* var/page_cache/* generated/*
   ```

## サンプルデータのインストールの完了

{{$include /help/_includes/sample-data-complete.md}}
