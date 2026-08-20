---
title: Apacheを使用した複数のweb サイトの設定
description: Apacheを使用して複数のweb サイトを設定するには、このチュートリアルに従ってください。
exl-id: 4c6890b3-f15a-46f2-a3e8-6f2a9b57a6ad
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# Apacheを使用した複数のweb サイトの設定

私たちは、次のことを想定しています。

必要に応じて、web サイトまたはストアビュー用の既存の`index.php` エントリポイントスクリプトをコピーし、次のように追加します。

- 開発用マシン（ラップトップ、仮想マシンなど）で作業している

  ホスト環境に複数のweb サイトをデプロイするには、追加のタスクが必要になる場合があります。詳しくは、ホスティングプロバイダーを確認してください。

  クラウドインフラストラクチャでAdobe Commerceを設定するには、追加のタスクが必要です。 このトピックで説明したタスクを完了したら、_Commerce on Cloud Infrastructure ガイド_&#x200B;の「[複数のweb サイトまたはストアを設定する](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure-store/multiple-sites)」を参照してください。

- Web サイトごとに1つの仮想ホストを使用します。仮想ホスト設定ファイルは`/etc/httpd/httpd.conf`です

  異なるオペレーティングシステム上のApacheの異なるバージョンは、仮想ホストを異なる方法で設定します。 仮想ホストの設定方法がわからない場合は、[Apache ドキュメント &#x200B;](https://httpd.apache.org/docs/2.4/vhosts)またはネットワーク管理者に問い合わせてください。

- Commerce ソフトウェアが`/var/www/html/magento2`にインストールされています
- デフォルト以外に2つのWeb サイトがあります。

  - `french.mysite.mg` （web サイト コード `french`およびストアビューコード `fr`）
  - `german.mysite.mg` （web サイト コード `german`およびストアビューコード `de`）

## Apacheを使用して複数のweb サイトを設定するためのロードマップ

複数のストアを設定するには、次のタスクを実行します。

1. [管理画面でweb サイト、ストア、ストアビューを設定](ms-admin.md)。
1. Commerce web サイトごとに[Apache バーチャルホスト &#x200B;](#step-2-create-apache-virtual-hosts)を1つ作成します。

## 手順1：管理画面でweb サイト、ストアビュー、ストアビューを作成する

[管理者](ms-admin.md)で複数のweb サイト、ストア、ストアビューを設定するを参照してください。

## 手順2:Apache仮想ホストの作成

この節では、仮想ホストでApache サーバー変数`SetEnvIf`を使用して`MAGE_RUN_TYPE`と`MAGE_RUN_CODE`の値を設定する方法について説明します。

`SetEnvIf`の詳細については、次を参照してください。

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**Apache仮想ホストを作成するには**:

1. `root`権限を持つユーザーとして、仮想ホスト設定ファイルをテキストエディターで開きます。

   例えば、`/etc/httpd/conf/httpd.conf`を開きます

1. `<VirtualHost *:80>`で始まるセクションを探します。
1. 既存の仮想ホストの後に次の仮想ホストを作成します。

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

1. 変更を`httpd.conf`に保存して、テキストエディターを終了します。
1. Apacheを再起動します。

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

## サイトの確認

ストアのURLにDNSを設定していない限り、`hosts` ファイルのホストに静的ルートを追加する必要があります。

1. オペレーティング システム `hosts` ファイルを探します。
1. 静的ルートを次の形式で追加します。

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
   ```

1. ブラウザーで次のいずれかのURLに移動します。

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- ホスト環境に複数のweb サイトをデプロイするには、追加のタスクが必要になる場合があります。詳しくは、ホスティングプロバイダーを確認してください。
>- クラウドインフラストラクチャ上にAdobe Commerceを設定するには、追加のタスクが必要です。_クラウドインフラストラクチャ上のCommerce ガイド_&#x200B;の[複数のクラウドウェブサイトまたはストアの設定](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure-store/multiple-sites)を参照してください。

### トラブルシューティング

- フランス語とドイツ語のサイトで404が返され、管理者が読み込まれる場合は、[手順6: ストア コードをベース URLに追加](ms-admin.md#step-6-add-the-store-code-to-the-base-url)してください。
- すべてのURLが404を返す場合は、必ずweb サーバーを再起動してください。
- 管理者が正しく機能しない場合は、仮想ホストを適切に設定してください。
