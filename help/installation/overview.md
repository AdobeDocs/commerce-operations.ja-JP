---
title: オンプレミス インストールの概要
description: Adobe Commerce のオンプレミスデプロイメントに関するインストールプロセスについて説明します。
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: 7cc77a204d2a3c0773e6a0ab60e57e6e35f12091
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 3%

---


# オンプレミス インストールの概要

ここでは、独自のインフラストラクチャにAdobe Commerceをインストールする方法の概要について説明します。 インストールプロセスには、サーバー環境の設定、必要なソフトウェアと資格情報の取得、インストールコマンドの実行が含まれます。

Adobe Commerce ソフトウェアは、約 30～60 分でインストールできます。 ただし、インストール前にサーバー環境をセットアップするのに必要な時間は、経験と選択したテクノロジーによって異なります。

>[!TIP]
>
>正常に続行するには、中程度の技術的知識とサーバーへのアクセス権が必要です。

インストールすると、[ 顧客向けのストアフロント ](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront) と [ 管理パネル ](https://experienceleague.adobe.com/en/docs/commerce-admin/start/admin/admin) の両方を備えた完全に機能するAdobe Commerce ストアが作成されます。 プロセスを開始する前に、データベース資格情報、ドメイン情報および認証キーの準備が完了している必要があります。

## ワークフロー

次の図は、オンプレミス環境用のAdobe Commerceをインストールする際の主な手順を示しています。

![ インストールの仕組み ](../assets/installation/on-premises-install.drawio.svg)

### サーバー環境の設定

[ 前提条件 ](prerequisites/overview.md) に従って、PHP、Web サーバー、データベースおよび検索エンジンをインストールして設定します。

### 認証キーの取得

Adobe Commerce Composer パッケージにアクセスするには、Commerce Marketplaceから新しい [ 認証キー ](prerequisites/authentication-keys.md) を生成（または既存のキーをコピー）します。

### Adobe Commerce ソフトウェアの入手

[Composer](prerequisites/commerce.md) （推奨）を使用してダウンロードするか、GitHub からクローンを使用して開発の投稿をダウンロードします。

Magento Open Source コードベースに投稿したり、アプリケーションをカスタマイズしたりする場合は、GitHub リポジトリを [ クローン ](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) します。 この方法を使用するには、GitHub と Composer の両方に関する知識が必要です。

### アプリケーションのインストール

特定の設定でインストールコマンドを実行します。 完全な例については、[ クイックスタート ](composer.md) を参照してください。

>[!NOTE]
>
>前提条件ソフトウェアが正しく設定されていないために手順が失敗した場合は、[ 前提条件 ](prerequisites/overview.md) を確認してください。

### インストールの確認

ストアフロントと管理パネルの [ テスト ](next-steps/verify.md) を実行して、すべてが正しく動作することを確認します。

## インストールに関するよくある問題

- **権限エラー**：ファイルシステムの所有権と権限が適切であることを確認します
- **データベース接続の失敗**: データベース資格情報とネットワーク接続を確認します
- **認証キーエラー**:Commerce Marketplace キーが有効でアクティブであることを確認します
- **メモリ制限**：十分な PHP メモリ割り当てを確保する（推奨される最小 2 GB）
