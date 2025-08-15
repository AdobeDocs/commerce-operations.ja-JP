---
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---
# 安全な Web サーバー通信

ここでは、Transport Layer Security （TLS）暗号化と [HTTP 基本認証 ](https://datatracker.ietf.org/doc/html/rfc2617) の組み合わせを使用して、web サーバーと検索エンジン（Elasticsearchまたは OpenSearch）間の通信を保護する例について説明します。 オプションで、その他のタイプの認証も設定できます。この情報の参照を提供しています。

（古い用語である Secure Sockets Layer （SSL）は、多くの場合、TLS と同じ意味で使用されます。 このトピックでは、*TLS*）を参照します。

>[!WARNING]
>
>特に明記されていない限り、このトピックのすべてのコマンドは、`root` 権限を持つユーザーとして入力する必要があります。

## 推奨事項

以下をお勧めします。

* Web サーバーで TLS が使用されている。

  TLS はこのトピックの範囲外ですが、実稼動環境では、自己署名証明書ではなく、実際の証明書を使用することを強くお勧めします。

* 検索エンジンは、web サーバーと同じホストで実行されます。 異なるホスト上で検索エンジンと Web サーバーを実行する方法については、このトピックの範囲外です。

  検索エンジンと Web サーバを同一ホストに配置する利点は、暗号化された通信を傍受できないことです。 検索エンジン web サーバーは、Adobe Commerce web サーバーと同じである必要はありません。例えば、Adobe Commerceは Apache を実行でき、Elasticsearch/OpenSearch は nginx を実行できます。

  検索エンジンが公開 web に公開されている場合は、認証を設定する必要があります。 検索エンジンインスタンスがネットワーク内で保護されている場合は、この操作は必要ない場合があります。 ホスティングプロバイダーと協力して、インスタンスを保護するために実装する必要があるセキュリティ対策を決定します。

## TLS の詳細情報

次のいずれかのリソースを参照してください。

* Apache

   * [Apache 2.4 強力な暗号化の使い方 ](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)
   * [Apache for Ubuntu 14.04 で SSL 証明書を作成する方法（Digitalocean チュートリアル） ](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)
   * [CentOS での SSL 保護 web サーバーの設定（CentOS wiki） ](https://wiki.centos.org/HowTos/Https)

* Nginx

   * [Nginx SSL ターミネーション ](https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/)
   * [Ubuntu 14.04 用 Nginx で SSL 証明書を作成する方法（Digitalocean チュートリアル） ](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04)
   * [Nginx SSL 証明書のインストール （digicert） ](https://www.digicert.com/ssl-certificate-installation-nginx.htm)
