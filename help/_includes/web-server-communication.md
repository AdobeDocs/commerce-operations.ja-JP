---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---
# 安全な Web サーバー通信

このトピックでは、Transport Layer Security(TLS) 暗号化と [HTTP 基本認証](https://datatracker.ietf.org/doc/html/rfc2617). 他のタイプの認証もオプションで設定できます。その情報の参照を提供します。

( 古い用語である Secure Sockets Layer(SSL) は、TLS と同じ意味で頻繁に使用されます。 このトピックでは、 *TLS*.)

>[!WARNING]
>
>特に断りのない限り、このトピック内のすべてのコマンドは、を使用するユーザーとして入力する必要があります。 `root` 権限。

## Recommendations

以下をお勧めします。

* Web サーバーが TLS を使用している。

  TLS はこのトピックの範囲外です。ただし、実稼動環境では、自己署名証明書ではなく、実際の証明書を使用することを強くお勧めします。

* 検索エンジンは、Web サーバーと同じホストで実行されます。 異なるホスト上で検索エンジンと Web サーバーを実行する方法は、このトピックでは扱いません。

  検索エンジンと Web サーバーを同じホスト上に配置する利点は、暗号化された通信を傍受できないことです。 検索エンジンの Web サーバーは、Adobe CommerceまたはMagento Open Sourceの Web サーバーと同じである必要はありません。例えば、Adobe Commerceは Apache を実行し、Elasticsearch/OpenSearch は nginx を実行します。

  検索エンジンがパブリック Web に公開されている場合は、認証を設定する必要があります。 検索エンジンのインスタンスがネットワーク内で保護されている場合は、この操作が不要な場合があります。 ホスティングプロバイダーと協力して、インスタンスを保護するために実装する必要があるセキュリティ対策を決定します。

## TLS の詳細

次のリソースのいずれかを参照してください。

* Apache

   * [Apache 2.4 強力な暗号化のハウツー](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)
   * [Ubuntu 14.04 用の Apache で SSL 証明書を作成する方法（Digitalocean チュートリアル）](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)
   * [CentOS での SSL 保護 Web サーバーの設定 (CentOS Wiki)](https://wiki.centos.org/HowTos/Https)

* Nginx

   * [Nginx SSL の終了](https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/)
   * [Ubuntu 14.04 用 Nginx で SSL 証明書を作成する方法（Digitalocean チュートリアル）](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04)
   * [Nginx SSL 証明書のインストール (digicert)](https://www.digicert.com/ssl-certificate-installation-nginx.htm)
