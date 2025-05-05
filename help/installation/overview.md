---
title: オンプレミス インストールの概要
description: Adobe Commerce のオンプレミスデプロイメントに関するインストールプロセスについて説明します。
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 7%

---

# オンプレミス インストールの概要

>[!NOTE]
>
>次の図は、Adobe Commerceの _&#x200B;**オンプレミス**&#x200B;_ インストールの概要を示しています。

![ インストールの仕組み ](../assets/installation/install-diagram-24.svg)

一般的なインストールフローを次に示します。

1. サーバー環境を設定します。

   PHP、Apache、MySQL、検索エンジンなど、前提条件のソフトウェアをインストールします。 詳しくは、[ 必要システム構成 ](system-requirements.md) を参照してください。

1. [ 認証キー ](prerequisites/authentication-keys.md) をCommerce Composer リポジトリに取得します。

1. Adobe Commerce ソフトウェアを入手します。

   * （推奨） [Composer メタパッケージ ](composer.md) を取得して、モジュールとその依存関係を管理します。

   * アプリケーションのコードベースに投稿したり、Magento Open Sourceをカスタマイズしたりする場合は、GitHub リポジトリを [ クローン ](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) します。 この方法を使用するには、GitHub と Composer の両方に関する知識が必要です。

1. コマンドラインを使用してアプリケーションをインストールします。

   前提条件ソフトウェアが正しく設定されていないために手順が失敗した場合は、[ 前提条件 ](prerequisites/overview.md) を確認してください。

1. ストアフロントと管理者を表示して、インストールを [ 確認 ](next-steps/verify.md) します。
