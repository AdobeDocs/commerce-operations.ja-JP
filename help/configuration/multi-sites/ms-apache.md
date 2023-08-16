---
title: Apache で複数の Web サイトを設定
description: Apache で複数の Web サイトを設定するには、このチュートリアルに従います。
exl-id: 4c6890b3-f15a-46f2-a3e8-6f2a9b57a6ad
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Apache で複数の Web サイトを設定

我々は、以下を想定する。

必要に応じて、既存の `index.php` web サイトまたはストア表示のエントリポイントスクリプトを次のように追加します。

- 開発マシン（ノート PC、仮想マシンなど）で作業している

  ホスト環境で複数の Web サイトをデプロイする場合は、追加のタスクが必要になる場合があります。詳しくは、ホスティングプロバイダーにお問い合わせください。

  クラウドインフラストラクチャ上にAdobe Commerceを設定するには、追加のタスクが必要です。 このトピックで説明したタスクを完了した後、 [複数の Web サイトまたはストアを設定する](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) （内） _Commerce on Cloud Infrastructure ガイド_.

- Web サイトごとに 1 つの仮想ホストを使用します。仮想ホストの設定ファイルは次のとおりです。 `/etc/httpd/httpd.conf`

  オペレーティングシステムごとに、Apache のバージョンが異なると、仮想ホストの設定も異なります。 詳しくは、 [Apache ドキュメント](https://httpd.apache.org/docs/2.4/vhosts) 仮想ホストの設定方法が不明な場合は、ネットワーク管理者。

- Commerce ソフトウェアは、 `/var/www/html/magento2`
- デフォルト以外の 2 つの Web サイトがあります。

   - `french.mysite.mg` Web サイトコード `french` およびビューコードをストア `fr`
   - `german.mysite.mg` Web サイトコード `german` およびビューコードをストア `de`

## Apache を使用して複数の Web サイトを設定するためのロードマップ

複数のストアを設定するには、次のタスクを実行します。

1. [Web サイト、ストア、ストアの表示を設定する](ms-admin.md) 」と入力します。
1. 1 つ作成 [Apache 仮想ホスト](#step-2-create-apache-virtual-hosts) コマース Web サイトごと。

## 手順 1:Web サイト、ストアを作成し、管理者にビューを保存する

詳しくは、 [複数の Web サイト、ストア、管理者での表示の設定](ms-admin.md).

## 手順 2:Apache 仮想ホストを作成する

このセクションでは、 `MAGE_RUN_TYPE` および `MAGE_RUN_CODE` Apache サーバー変数の使用 `SetEnvIf` 仮想ホスト内。

詳しくは、 `SetEnvIf`を参照してください。

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**Apache 仮想ホストを作成するには**:

1. を使用して `root` 権限を設定し、仮想ホストの設定ファイルをテキストエディターで開きます。

   例えば、を開きます。 `/etc/httpd/conf/httpd.conf`

1. 次で始まるセクションを見つけます。 `<VirtualHost *:80>`.
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

1. 変更をに保存します。 `httpd.conf` をクリックし、テキストエディタを終了します。
1. Apache を再起動します。

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

## サイトの検証

ストアの URL に対して DNS が設定されていない限り、 `hosts` ファイル：

1. オペレーティングシステムを見つける `hosts` ファイル。
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
>- ホスト環境で複数の Web サイトをデプロイする場合は、追加のタスクが必要になる場合があります。詳しくは、ホスティングプロバイダーにお問い合わせください。
>- クラウドインフラストラクチャ上にAdobe Commerceを設定するには、追加のタスクが必要です。詳しくは、 [複数のクラウド Web サイトまたはストアを設定する](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) （内） _Commerce on Cloud Infrastructure ガイド_.

### トラブルシューティング

- フランス語およびドイツ語のサイトが 404 秒を返すが、管理者が読み込まれる場合は、必ず [手順 6：ベース URL にストアコードを追加する](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- すべての URL が 404 秒を返す場合は、Web サーバーを再起動したことを確認してください。
- 管理者が正しく機能しない場合は、仮想ホストを正しく設定していることを確認してください。
