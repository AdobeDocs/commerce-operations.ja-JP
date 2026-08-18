---
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---
# 安全なweb サーバー通信

このトピックでは、Transport Layer Security （TLS）暗号化と[HTTP Basic authentication](https://datatracker.ietf.org/doc/html/rfc2617)を組み合わせて使用して、web サーバーと検索エンジン（ElasticsearchまたはOpenSearch）との間の通信を保護する例について説明します。 他の種類の認証もオプションで設定できます。この情報の参照を提供します。

（古い用語であるSSL （Secure Sockets Layer）は、TLSと同じ意味で頻繁に使用されます。 このトピックでは、*TLS*&#x200B;を参照します）。

>[!WARNING]
>
>特に記載のない限り、このトピックのすべてのコマンドは、`root`権限を持つユーザーとして入力する必要があります。

## 推奨事項

推奨事項は次のとおりです。

* Web サーバーはTLSを使用しています。

  TLSはこのトピックの範囲を超えていますが、自己署名証明書ではなく実稼動証明書を使用することを強くお勧めします。

* 検索エンジンは、web サーバーと同じホスト上で実行されます。 検索エンジンとweb サーバーを異なるホストで実行することは、このトピックの範囲を超えています。

  検索エンジンとウェブサーバーを同じホスト上に置く利点は、暗号化された通信を傍受できないことである。 検索エンジン web サーバーは、Adobe Commerce web サーバーと同じである必要はありません。例えば、Adobe CommerceはApacheを実行でき、Elasticsearch/OpenSearchはnginxを実行できます。

  検索エンジンがパブリック webに公開されている場合は、認証を設定する必要があります。 検索エンジンインスタンスがネットワーク内で保護されている場合、これは必要ない場合があります。 ホスティングプロバイダーと協力して、インスタンスを保護するために実装する必要があるセキュリティ対策を決定します。

## TLSに関する詳細情報

次のいずれかのリソースを参照してください。

* Apache

  * [Apache 2.4の強力な暗号化のハウツー](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)
  * [Ubuntu 14.04向けApacheでSSL証明書を作成する方法（Digitalocean チュートリアル）](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)
  * [CentOSを使用したSSL セキュアなWeb サーバーの設定（CentOS wiki）](https://wiki.centos.org/HowTos/Https)

* Nginx

  * [Nginx SSL終了](https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/)
  * [Ubuntu 14.04向けNginxでSSL証明書を作成する方法（Digitalocean チュートリアル）](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04)
  * [Nginx SSL証明書のインストール（digicert）](https://www.digicert.com/ssl-certificate-installation-nginx.htm)
