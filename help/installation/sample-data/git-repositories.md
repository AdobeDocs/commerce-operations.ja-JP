---
title: サンプルデータ Git リポジトリのクローン
description: Git リポジトリをクローンしてAdobe Commerce サンプルデータをインストールするには、次の手順に従います。
exl-id: 748eee30-2821-457d-9c1c-62ede8bc0510
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 0%

---

# サンプルデータ Git リポジトリのクローン

このトピックでは、Magento Open Source GitHub リポジトリのクローンを作成した場合に、サンプルデータをクローンして追加する方法について説明します。 この手法は、コントリビューションをおこなう開発者（Magento Open Source コードベースにコントリビューションする予定の開発者）のみを対象としています。

コントリビューションを行う開発者でない場合は、ページの左側にある目次に表示されている他のオプションの 1 つを選択します。

コントリビューションを行う開発者は、次の条件が満たされる場合に、このサンプルデータのインストール方法を使用できます *のみ*。

* Magento Open Sourceの使用
* [GitHub リポジトリのクローンを作成しました ](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

>[!WARNING]
>
>サンプルデータは、`develop` ブランチ（より最新）またはリリースされたブランチ（より安定した `2.4` など）で使用できます。 リリース済みのブランチは安定性が高いので、使用することをお勧めします。 リポジトリにコードを提供していて、最新のコードが必要な場合は、`develop` ブランチを使用します。 選択するブランチに関係なく、Magento Open Source GitHub リポジトリの対応するブランチを [ クローン ](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository) する必要があります。 例えば、`develop` ブランチのサンプルデータは、Magento Open Source *ブランチと共に* のみ `develop` 使用できます。

## サンプルデータリポジトリのクローンの作成

この項では、サンプル・データ・リポジトリをクローニングしてサンプル・データをインストールする方法について説明します。 サンプルデータリポジトリは、次のいずれかの方法でクローンできます。

* [SSH プロトコル ](#clone-with-ssh) を使用したクローン
* [HTTPS プロトコル ](#clone-with-https) を使用して複製

### SSH によるクローン

SSH プロトコルを使用してサンプルデータ GitHub リポジトリのクローンを作成するには：

1. Web ブラウザーで、[ サンプルデータリポジトリ ](https://github.com/magento/magento2-sample-data) に移動します。
1. ブランチ名の横にあるリストの「**SSH**」をクリックします。
1. 「**クリップボードにコピー**」をクリックします

   次の図に例を示します。

   ![SSH を使用した GitHub リポジトリのクローン ](../../assets/installation/install_mage2_clone-ssh.png)

1. を web サーバーの docroot ディレクトリに変更します。

   通常、Ubuntu の場合は `/var/www` で、CentOS の場合は `/var/www/html` です。

1. `git clone` と入力し、以前に取得した値を貼り付けます。

   次に例を示します。

   ```bash
   git clone git@github.com:magento/magento2-sample-data.git
   ```

1. リポジトリがサーバー上でクローンされるのを待ちます。

   >[!NOTE]
   >
   >次のエラーが表示される場合は、[SSH キーを共有 ](https://docs.github.com/articles/generating-ssh-keys/) していることを GitHub で確認してください。<br>

   ```
   Cloning into 'magento2'...
   Permission denied (publickey).
   fatal: The remote end hung up unexpectedly
   ```

1. メインの `magento2` リポジトリから、使用したブランチに対応するサンプルデータリポジトリのブランチをチェックアウトします。

   例：

   Magento Open Source GitHub リポジトリの `2.4-develop` ブランチを使用した場合は、Sample Data ブランチを `2.4-develop` す必要があります。

   正しいブランチをチェックアウトするには、サンプルデータリポジトリのルートディレクトリ（`2.4-develop` ブランチが必要な場合）から次のコマンドを実行します。

   ```bash
   git checkout 2.4-develop
   ```

1. `<app_root>` に変更します。
1. 次のコマンドを入力して、クローンを作成したファイル間にシンボリックリンクを作成し、サンプルデータが正しく動作するようにします。

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

1. コマンドが完了するまで待ちます。

1. [ ファイルシステムの権限と所有権の設定 ](#set-file-system-ownership-and-permissions) を参照してください。

1. 次のコマンドを実行します。

   ```bash
   bin/magento setup:upgrade
   ```

### HTTPS を使用してクローン

HTTPS プロトコルを使用してサンプルデータ GitHub リポジトリを複製するには：

1. Web ブラウザーで、[ サンプルデータリポジトリ ](https://github.com/magento/magento2-sample-data) に移動します。
1. ページの右側にある「**クローン URL**」フィールドで **HTTPS** をクリックします。
1. **クリップボードにコピー** をクリックします。

   次の図に例を示します。

   ![HTTPS を使用して GitHub リポジトリを複製する ](../../assets/installation/install_mage2_clone-https.png)

1. を web サーバーの docroot ディレクトリに変更します。

   通常、Ubuntu の場合は `/var/www` で、CentOS の場合は `/var/www/html` です。

1. `git clone` と入力し、以前に取得した値を貼り付けます。

   次に例を示します。

   ```bash
   git clone https://github.com/magento/magento2-sample-data.git
   ```

1. リポジトリがサーバー上でクローンされるのを待ちます。
1. メインの `magento2` リポジトリから、使用したブランチに対応するサンプルデータリポジトリのブランチをチェックアウトします。

   例：

   Magento Open Source GitHub リポジトリの `2.4-develop` ブランチを使用した場合は、Sample Data ブランチを `2.4-develop` す必要があります。

   正しいブランチをチェックアウトするには、サンプルデータリポジトリのルートディレクトリ（`2.4-develop` ブランチが必要な場合）から次のコマンドを実行します。

   ```bash
   git checkout 2.4-develop
   ```

1. `<magento_root>` に変更します。
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
>Adobe Commerceをインストールした *後* サンプルデータをインストールする場合は、次のコマンドも実行してデータベースとスキーマを更新する必要があります。
>
>```bash
><magento_root>/bin/magento setup:upgrade
>```

## ファイルシステムの所有権と権限の設定

`php build-sample-data.php` スクリプトは、サンプルデータリポジトリとMagento Open Source リポジトリの間にシンボリックリンクを作成するので、ファイルシステムの権限と所有権をサンプルデータリポジトリで設定する必要があります。 これをおこなわないと、ストアフロントへのアクセスでエラーが発生します。

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

<!-- Last updated from includes: 2022-09-08 11:33:05 -->
