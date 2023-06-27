---
title: オンプレミスのインストールセキュリティ
description: オンプレミスでのAdobe CommerceまたはMagento Open Sourceのインストールのセキュリティ姿勢を改善する方法について説明します。
feature: Install, Security
exl-id: 56724a72-c64d-44d4-a886-90d97ae5fb6d
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# オンプレミスのインストールセキュリティ

[セキュリティ強化 Linux(SELinux)](https://selinuxproject.org/page/Main_Page) を使用すると、CentOS および Ubuntu 管理者がサーバーに対するより優れたアクセス制御をおこなうことができます。 SELinux を使用する場合 *および* Apache は別のホストへの接続を開始する必要があります。この節で説明するコマンドを実行する必要があります。

>[!NOTE]
>
>Adobeには、SELinux の使用に関する推奨事項はありません。必要に応じて、セキュリティ強化に使用できます。 SELinux を使用する場合は、適切に設定する必要があります。設定しないと、Adobe CommerceとMagento Open Sourceが予想外に機能する可能性があります。 SELinux を使用する場合は、 [CentOS Wiki](https://wiki.centos.org/HowTos/SELinux) ：通信を有効にするルールを設定します。

## Apache とのインストールに関する推奨事項

SELinux を有効にする場合、 *セキュリティコンテキスト* の一部のディレクトリを次に示します。

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

前述のコマンドは、Apache Web サーバーでのみ機能します。 さまざまな設定とセキュリティ要件があるので、これらのコマンドがどのような状況でも機能するとは限りません。 詳しくは、以下を参照してください。

* [man ページ](https://linux.die.net/man/8/httpd_selinux)
* [サーバーラボ](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## サーバー間通信を有効にする

Apache とデータベースサーバーが同じホスト上にある場合、 `curl` ( 例： Paypal と USPS)。
SELinux を有効にして Apache が別のホストへの接続を開始できるようにするには：

1. SELinux が有効かどうかを判断するには、次のコマンドを使用します。

   ```bash
   getenforce
   ```

   `Enforcing` 「 」が表示され、SELinux が実行中であることを確認します。

   * CentOS: `setsebool -P httpd_can_network_connect=1`
   * Ubuntu: `setsebool -P apache2_can_network_connect=1`

## ファイアウォールでポートを開く

セキュリティ要件によっては、ファイアウォール内のポート 80 および他のポートを開く必要が生じる場合があります。 ネットワークセキュリティは機密性が高いので、Adobeは先に進む前に IT 部門に相談することを強くお勧めします。 次に、推奨される参照を示します。

* Ubuntu: [Ubuntu ドキュメントページ](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS: [CentOS のハウツー](https://wiki.centos.org/HowTos/Network/IPTables).
