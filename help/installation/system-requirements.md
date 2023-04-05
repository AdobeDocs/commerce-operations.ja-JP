---
title: 必要システム構成
description: このリファレンスを使用して、Adobe CommerceとMagento Open Sourceのリリースでテストされた、必要なソフトウェアの依存関係を特定します。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---


# 必要システム構成

次の表は、特定のAdobe CommerceおよびMagento Open SourceリリースでAdobeがテストしたサードパーティソフトウェアの依存関係のバージョンを示しています。 Adobeは、次の表に示すシステム要件の組み合わせのみをサポートします。

例えば、MariaDB 10.4 で 2.4.5 が完全にテストされています。Adobeでは、2.4.5 にアップグレードする前に MariaDB 10.4 にアップグレードすることをお勧めします。

{{$include /help/_includes/templated/system-requirements-table.md}}

## その他

このセクションでは、その他のすべての種類の必須およびオプションソフトウェアのサポートと互換性について説明します。

>[!NOTE]
>
>以下の要件は、Adobe CommerceとMagento Open Sourceの最新 2.4.x パッチリリースに適用されます。

### メールサーバー

メール転送エージェント (MTA) または SMTP サーバー

### オペレーティングシステム (Linux x86～64)

RedHat Enterprise Linux(RHEL)、CentOS、Ubuntu、Debian などの Linux ディストリビューション。 Microsoft Windows とmacOSはサポートされていません。

### PHP 拡張機能

>[!NOTE]
>
>この [PHP のインストール手順](prerequisites/php-settings.md) には、これらの拡張機能をインストールする手順が含まれています。

{{$include /help/_includes/templated/php-extensions.md}}

参照： [公式の PHP ドキュメント](https://php.net/manual/en/extensions.php) インストールの詳細については、を参照してください。

### PHP OPcache

を確認することを強くお勧めします。 [PHP OPcache](https://php.net/manual/en/intro.opcache.php) は、パフォーマンス上の理由から有効になっています。 OPcache は多くの PHP ディストリビューションで有効になっています。 インストールされているかどうかを確認するには、 [PHP ドキュメント](prerequisites/php-settings.md).

個別にインストールする必要がある場合は、 [PHP OPcache のドキュメント](https://php.net/manual/en/opcache.setup.php).

### PHP 設定

特定の PHP 設定 ( `memory_limit`を使用すると、Adobe CommerceとMagento Open Sourceの使用時に発生する一般的な問題を回避できます。

詳しくは、 [必要な PHP 設定](prerequisites/php-settings.md).

### PHPUnit

PHPUnit （コマンドラインツールとして） 9.0.0

### RAM

Commerce Marketplaceやその他のソースから入手したアプリケーションや拡張機能をアップグレードする場合、最大 2 GB の RAM が必要になる場合があります。 RAM が 2 GB 未満のシステムを使用している場合は、 [スワップファイル](https://support.magento.com/hc/en-us/articles/360032980432);そうしないと、アップグレードが失敗する場合があります。

### システムの依存関係

Adobe CommerceおよびMagento Open Sourceでは、一部の操作に次のシステムツールが必要です。

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gzip.org/)
- [[!DNL lsof]](https://linux.die.net/man/8/lsof)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)
- [[!DNL nice]](https://linux.die.net/man/1/nice)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://linux.die.net/man/1/tar)

### SSL

- HTTPS には有効なセキュリティ証明書が必要です。
- 自己署名 SSL 証明書はサポートされていません。
- トランスポート層セキュリティ (TLS) の要件 — PayPal および `repo.magento.com` どちらも TLS 1.2 以降が必要です。

### サポートされているブラウザー

ストアフロントと管理：

- Microsoft Edge（最新および以前のメジャーバージョン）
- Firefox（最新および以前のメジャーバージョン）任意のオペレーティングシステム
- Chrome（最新および以前のメジャーバージョン）任意のオペレーティングシステム
- Safari（最新および以前のメジャーバージョン）macOSのみ )
- Safari Mobile for iPad 2、iPad Mini、Retina ディスプレイ搭載iPad(iOS 12 以降 )（デスクトップストアフロント用）
- Safari Mobile for iPhone 6 以降iOS 12 以降（モバイルストアフロント用）
- モバイル用 Chrome（最新および以前のメジャーバージョン） [Android 4 以降] （モバイルストアフロント用）

### Xdebug

[php_xdebug 2.5.x](https://xdebug.org/download) 以降（開発環境のみ）（性能に悪影響を及ぼす可能性がある）

>[!NOTE]
>
>次の既知の問題があります： `xdebug` これは、Adobe CommerceまたはMagento Open Sourceのインストールや、インストール後のストアフロントまたは Admin へのアクセスに影響を与える可能性があります。 詳しくは、 [xdebug に関する既知の問題](https://support.magento.com/hc/en-us/articles/360034242212).
