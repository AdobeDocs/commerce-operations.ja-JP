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

必要に応じて、Web サイトまたはストアビューの既存の `index.php` エントリポイントスクリプトをコピーし、次のように追加します。

- 開発マシン（ラップトップ、仮想マシンなど）で作業している

  ホストされた環境に複数の web サイトをデプロイするには、追加のタスクが必要になる場合があります。詳しくは、ホスティングプロバイダーにお問い合わせください。

  クラウドインフラストラクチャー上にAdobe Commerceをセットアップするには、追加のタスクが必要になります。 Commerceこのトピックで取り上げる作業が完了したら、[Cloud Infrastructure ガイドの ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) 複数の web サイトまたはストアの設定 _を参照してください_。

- Web サイトごとに 1 つのバーチャルホストを使用します。バーチャルホスト設定ファイルは `/etc/httpd/httpd.conf` です

  異なるオペレーティングシステム上の異なるバージョンの Apache では、異なる方法で仮想ホストを設定します。 [Apache のドキュメント ](https://httpd.apache.org/docs/2.4/vhosts) を参照するか、仮想ホストの設定方法が不明な場合はネットワーク管理者に問い合わせてください。

- Commerce ソフトウェアは `/var/www/html/magento2` にインストールされています
- デフォルト以外に 2 つの web サイトがあります。

   - web サイトコード `french.mysite.mg` とストアビューコード `french` を使用した `fr`
   - web サイトコード `german.mysite.mg` とストアビューコード `german` を使用した `de`

## Apache で複数の web サイトを設定するためのロードマップ

複数のストアを設定するには、次のタスクを実行します。

1. 管理画面で [web サイト、ストア、ストア表示を設定 ](ms-admin.md) します。
1. Commerceの web サイトごとに 1 つの [Apache バーチャルホスト ](#step-2-create-apache-virtual-hosts) を作成します。

## 手順 1：管理での web サイト、ストア、ストアビューの作成

詳しくは [ 管理での複数の web サイト、ストア、ストア表示の設定 ](ms-admin.md) を参照してください。

## 手順 2:Apache 仮想ホストを作成する

この節では、仮想ホストで Apache サーバー変数 `MAGE_RUN_TYPE` を使用して `MAGE_RUN_CODE` および `SetEnvIf` の値を設定する方法について説明します。

`SetEnvIf` について詳しくは、以下を参照してください。

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**Apache 仮想ホストを作成するには**:

1. `root` 権限を持つユーザーとして、仮想ホスト設定ファイルをテキストエディターで開きます。

   例えば、を開きます `/etc/httpd/conf/httpd.conf`

1. `<VirtualHost *:80>` で始まるセクションを見つけます。
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

1. `httpd.conf` への変更を保存し、テキストエディターを終了します。
1. Apache を再起動します。

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

## サイトの検証

ストアの URL に対して DNS を設定していない限り、`hosts` ファイルのホストへの静的ルートを追加する必要があります。

1. オペレーティングシステムの `hosts` ファイルを見つけます。
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
>- クラウドインフラストラクチャー上にAdobe Commerceを設定するには、さらに作業が必要です。[2} クラウドインフラストラクチャー上のCommerceガイド ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) 複数のクラウド Web サイトまたはストアの設定 _を参照してください。_

### トラブルシューティング

- フランス語およびドイツ語のサイトが 404 を返すが、管理者が読み込む場合は、[ 手順 6：ベース URL にストアコードを追加する ](ms-admin.md#step-6-add-the-store-code-to-the-base-url) を完了していることを確認します。
- すべての URL が 404 を返す場合は、web サーバーを再起動していることを確認します。
- 管理者が正しく機能しない場合は、仮想ホストを正しく設定していることを確認してください。
