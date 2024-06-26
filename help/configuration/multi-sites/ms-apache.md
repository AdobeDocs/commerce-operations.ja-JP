---
title: Apache での複数の web サイトの設定
description: このチュートリアルに従って、Apache で複数の web サイトを設定します。
exl-id: 4c6890b3-f15a-46f2-a3e8-6f2a9b57a6ad
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# Apache での複数の web サイトの設定

以下を前提としています。

必要に応じて、既存のを `index.php` web サイトまたはストアビューのエントリポイントスクリプトを作成し、それに次を追加します。

- 開発マシン（ラップトップ、仮想マシンなど）で作業している

  ホストされた環境に複数の web サイトをデプロイするには、追加のタスクが必要になる場合があります。詳しくは、ホスティングプロバイダーにお問い合わせください。

  クラウドインフラストラクチャー上にAdobe Commerceをセットアップするには、追加のタスクが必要になります。 このトピックで説明するタスクを完了したら、次を参照してください [複数の web サイトまたはストアを設定](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) が含まれる _クラウドインフラストラクチャー上のCommerce ガイド_.

- Web サイトごとに 1 つのバーチャルホストを使用します。バーチャルホスト設定ファイルは、です。 `/etc/httpd/httpd.conf`

  異なるオペレーティングシステム上の異なるバージョンの Apache では、異なる方法で仮想ホストを設定します。 を参照してください [Apache ドキュメント](https://httpd.apache.org/docs/2.4/vhosts) または、仮想ホストのセットアップ方法がわからない場合はネットワーク管理者に問い合わせてください。

- Commerce ソフトウェアのインストール先 `/var/www/html/magento2`
- デフォルト以外に 2 つの web サイトがあります。

   - `french.mysite.mg` （web サイトコードを使用） `french` およびストア表示コード `fr`
   - `german.mysite.mg` （web サイトコードを使用） `german` およびストア表示コード `de`

## Apache で複数の web サイトを設定するためのロードマップ

複数のストアを設定するには、次のタスクを実行します。

1. [Web サイト、ストア、ストアビューの設定](ms-admin.md) admin.
1. 1 つ作成 [Apache 仮想ホスト](#step-2-create-apache-virtual-hosts) Commerce web サイトあたり。

## 手順 1：管理での web サイト、ストア、ストアビューの作成

参照： [管理での複数の web サイト、ストア、ストア表示の設定](ms-admin.md).

## 手順 2:Apache 仮想ホストを作成する

この節では、の値を設定する方法について説明します `MAGE_RUN_TYPE` および `MAGE_RUN_CODE` apache サーバー変数の使用 `SetEnvIf` 仮想ホストの場合。

詳しくは、 `SetEnvIf`を参照してください。

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**Apache 仮想ホストを作成するには**:

1. を使用した As a ユーザー `root` 「privileges」を選択し、仮想ホスト構成ファイルをテキスト・エディタで開きます。

   例えば、次を開きます `/etc/httpd/conf/httpd.conf`

1. で始まるセクションを見つけます `<VirtualHost *:80>`.
1. 既存の仮想ホストの後に、次の仮想ホストを作成します。

   ```conf
   <VirtualHost *:80>
      ServerName          mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          french.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "french"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          german.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "german"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   ```

1. 変更をに保存します。 `httpd.conf` をクリックして、テキストエディターを終了します。
1. Apache を再起動します。

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

## サイトの検証

ストアの URL に対して DNS を設定していない限り、のホストへの静的ルートを追加する必要があります `hosts` ファイル：

1. オペレーティングシステムの場所 `hosts` ファイル。
1. 次の形式で静的ルートを追加します。

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
   ```

1. ブラウザーで次の URL のいずれかに移動します。

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- ホストされた環境に複数の web サイトをデプロイするには、追加のタスクが必要になる場合があります。詳しくは、ホスティングプロバイダーにお問い合わせください。
>- クラウドインフラストラクチャにAdobe Commerceを設定するには、さらに作業が必要です。詳しくは、以下を参照してください [複数のクラウド web サイトまたはストアを設定する](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) が含まれる _クラウドインフラストラクチャー上のCommerce ガイド_.

### トラブルシューティング

- フランス語およびドイツ語のサイトが 404 を返したが、管理者が読み込まれる場合は、完了していることを確認します [手順 6：ベース URL へのストアコードの追加](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- すべての URL が 404 を返す場合は、web サーバーを再起動していることを確認します。
- 管理者が正しく機能しない場合は、仮想ホストを正しく設定していることを確認してください。
