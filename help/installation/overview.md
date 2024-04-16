---
title: オンプレミス インストールの概要
description: Adobe Commerceのオンプレミスデプロイメントのインストールプロセスについて説明します。
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# オンプレミス インストールの概要

>[!NOTE]
>
>次の図は、の概要を示しています。 _**オンプレミス**_ Adobe Commerceのインストール：

![インストールの仕組み](../assets/installation/install-diagram-24.svg)

一般的なインストールフローを次に示します。

1. サーバー環境を設定します。

   PHP、Apache、MySQL、検索エンジンなど、前提条件のソフトウェアをインストールします。 を参照してください。 [必要システム構成](system-requirements.md) を参照してください。

1. 取得 [認証キー](prerequisites/authentication-keys.md) をCommerce Composer リポジトリに追加します。

1. Adobe CommerceまたはMagento Open Sourceのソフトウェアを入手します。

   * （推奨）を取得します [Composer メタパッケージ](composer.md) モジュールとその依存関係を管理します。

   * アプリケーションのコードベースにコントリビューションしたり、Magento Open Sourceをカスタマイズしたりする場合は、 [クローン](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) github リポジトリ。 この方法を使用するには、GitHub と Composer の両方に関する知識が必要です。

1. コマンドラインを使用してアプリケーションをインストールします。

   前提条件のソフトウェアが正しく設定されていないために手順が失敗した場合は、 [前提条件](prerequisites/overview.md).

1. [検証](next-steps/verify.md) ストアフロントと管理者を表示したインストール。
