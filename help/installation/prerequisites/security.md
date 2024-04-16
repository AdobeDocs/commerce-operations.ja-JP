---
title: オンプレミス インストールのセキュリティ
description: Adobe CommerceまたはMagento Open Sourceのオンプレミス環境のセキュリティ体制を強化する方法について説明します。
feature: Install, Security
exl-id: 56724a72-c64d-44d4-a886-90d97ae5fb6d
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# オンプレミス インストールのセキュリティ

[Security Enhanced Linux （SELinux）](https://selinuxproject.org/page/Main_Page) centOS 管理者と Ubuntu 管理者がサーバーに対するより優れたアクセス制御を可能にします。 SELinux を使用する場合 *および* Apache が別のホストへの接続を開始する必要があります。この節で説明するコマンドを実行する必要があります。

>[!NOTE]
>
>Adobeでは、SELinux の使用に関する推奨事項はありません。必要に応じて、セキュリティの強化に使用できます。 SELinux を使用する場合は、適切に設定する必要があります。そうしないと、Adobe Commerceが予期せず機能することがあります。 SELinux を使用する場合は、 [CentOS wiki](https://wiki.centos.org/HowTos/SELinux) ：通信を有効にするルールを設定します。

## を Apache とインストールする際の推奨事項

SELinux を有効にする場合、 *セキュリティ コンテキスト* ディレクトリの一部を次に示します。

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/app/etc
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/var
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/media
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/static
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/generated
```

上記のコマンドは Apache web サーバーでのみ機能します。 さまざまな設定とセキュリティ要件があるため、これらのコマンドがすべての状況で動作することを保証するものではありません。 詳しくは、以下を参照してください。

* [man ページ](https://linux.die.net/man/8/httpd_selinux)
* [サーバラボ](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## サーバー間通信を有効にする

Apache とデータベースサーバーが同じホスト上にある場合、を使用する統合を使用する予定があれば、次のコマンドを使用します `curl` （例： Paypal および USPS）。
SELinux を有効にして Apache が別のホストへの接続を開始できるようにするには、次の手順に従います。

1. SELinux が有効かどうかを確認するには、次のコマンドを使用します。

   ```bash
   getenforce
   ```

   `Enforcing` は、SELinux が実行中であることを確認するために表示されます。

   * CentOS: `setsebool -P httpd_can_network_connect=1`
   * Ubuntu: `setsebool -P apache2_can_network_connect=1`

## ファイアウォールでポートを開く

セキュリティ要件によっては、ポート 80 やその他のポートをファイアウォールで開く必要がある場合があります。 ネットワークセキュリティは機密性が高いため、Adobeでは、作業を進める前に IT 部門に問い合わせることを強くお勧めします。 以下に、推奨参照を示します。

* Ubuntu: [Ubuntu ドキュメントページ](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS: [CentOS のハウツー](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html).
