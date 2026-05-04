---
title: オンプレミスのインストールのセキュリティ
description: Adobe Commerce オンプレミス インストールのセキュリティ対策を強化する方法について説明します。
feature: Install, Security
exl-id: 56724a72-c64d-44d4-a886-90d97ae5fb6d
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# オンプレミスのインストールのセキュリティ

[&#x200B; セキュリティ強化Linux （SELinux） &#x200B;](https://selinuxproject.org/page/Main_Page)を使用すると、CentOSおよびUbuntu管理者は、サーバーに対するアクセス制御を強化できます。 SELinux *および*&#x200B;を使用している場合、Apacheは別のホストへの接続を開始する必要があります。この節で説明するコマンドを実行する必要があります。

>[!NOTE]
>
>Adobeでは、SELinuxの使用に関する推奨事項はありません。必要に応じて、セキュリティを強化するために使用できます。 SELinuxを使用する場合は、適切に設定する必要があります。そうしないと、Adobe Commerceが予測不可能に機能する可能性があります。 SELinuxを使用する場合は、[CentOS wiki](https://wiki.centos.org/HowTos/SELinux)などのリソースを参照して、通信を有効にするルールを設定します。

## Apacheを使用したインストールの提案

SELinuxを有効にするように選択した場合、一部のディレクトリの&#x200B;*セキュリティコンテキスト*&#x200B;を次のように変更しない限り、インストーラーの実行に問題が発生する可能性があります。

```shell
chcon -R --type httpd_sys_rw_content_t <magento_root>/app/etc
```

```shell
chcon -R --type httpd_sys_rw_content_t <magento_root>/var
```

```shell
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/media
```

```shell
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/static
```

```shell
chcon -R --type httpd_sys_rw_content_t <magento_root>/generated
```

上記のコマンドは、Apache Web サーバーでのみ機能します。 様々な設定やセキュリティ要件があるため、これらのコマンドがすべての状況で機能することを保証するものではありません。 詳細は、次を参照してください。

* [man ページ](https://linux.die.net/man/8/httpd_selinux)
* [サーバーラボ](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## サーバー間通信の有効化

Apacheとデータベースサーバーが同じホスト上にある場合、`curl`を使用する統合を使用する予定の場合は、次のコマンドを使用します（例： PaypalとUSPS）。
SELinuxが有効になっている別のホストへの接続をApacheが開始できるようにするには：

1. SELinuxが有効かどうかを判断するには、次のコマンドを使用します。

   ```shell
   getenforce
   ```

   `Enforcing`が表示され、SELinuxが実行されていることを確認します。

   * CentOS: `setsebool -P httpd_can_network_connect=1`
   * Ubuntu: `setsebool -P apache2_can_network_connect=1`

## ファイアウォールでポートを開く

セキュリティ要件に応じて、ファイアウォールのポート 80やその他のポートを開く必要がある場合があります。 ネットワークセキュリティは機密性が高いため、Adobeでは、先に進む前にIT部門に相談することを強くお勧めします。 推奨される参照を次に示します。

* Ubuntu: [Ubuntu ドキュメントページ &#x200B;](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS: [CentOS ハウツー](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html)。
