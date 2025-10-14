---
title: オンプレミス インストールのセキュリティ
description: Adobe Commerce オンプレミスのインストールのセキュリティ体制を強化する方法について説明します。
feature: Install, Security
exl-id: 56724a72-c64d-44d4-a886-90d97ae5fb6d
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# オンプレミス インストールのセキュリティ

[Security Enhanced Linux （SELinux） &#x200B;](https://selinuxproject.org/page/Main_Page) により、CentOS および Ubuntu 管理者はサーバーに対するより優れたアクセス制御が可能になります。 SELinux *および* を使用している場合、Apache が別のホストへの接続を開始する必要があります。この節で説明するコマンドを実行する必要があります。

>[!NOTE]
>
>Adobeでは、SELinux の使用に関する推奨事項はありません。必要に応じて、セキュリティの強化に使用できます。 SELinux を使用する場合は、適切に設定する必要があります。そうしないと、Adobe Commerceが予期せず機能することがあります。 SELinux を使用する場合は、[CentOS wiki](https://wiki.centos.org/HowTos/SELinux) などのリソースを参照して、通信を有効にするルールを設定してください。

## を Apache とインストールする際の推奨事項

SELinux を有効にすることを選択した場合、次のように一部のディレクトリの *セキュリティコンテキスト* を変更しない限り、インストーラーの実行に問題が生じる可能性があります。

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

* [&#x200B; マニュアルページ &#x200B;](https://linux.die.net/man/8/httpd_selinux)
* [Server Lab](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## サーバー間通信を有効にする

Apache とデータベースサーバーが同じホスト上にある場合、`curl` を使用する統合を使用する予定があれば次のコマンドを使用します（例： Paypal および USPS）。
SELinux を有効にして Apache が別のホストへの接続を開始できるようにするには、次の手順に従います。

1. SELinux が有効かどうかを確認するには、次のコマンドを使用します。

   ```bash
   getenforce
   ```

   `Enforcing` が表示され、SELinux が実行中であることを確認します。

   * CentOS: `setsebool -P httpd_can_network_connect=1`
   * Ubuntu: `setsebool -P apache2_can_network_connect=1`

## ファイアウォールでポートを開く

セキュリティ要件によっては、ポート 80 やその他のポートをファイアウォールで開く必要がある場合があります。 ネットワークセキュリティは機密性が高いため、Adobeでは、先に進む前に IT 部門に問い合わせることを強くお勧めします。 以下に、推奨参照を示します。

* Ubuntu: [Ubuntu ドキュメントページ &#x200B;](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS: [CentOS のハウツー &#x200B;](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html)。
