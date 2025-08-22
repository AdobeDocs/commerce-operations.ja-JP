---
title: サンプルの Data Composer パッケージのダウンロード
description: Composer PHP Package Manager を使用してAdobe Commerce サンプル データをインストールするには、次の手順に従います。
feature: Install, Deploy
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# サンプルの Data Composer パッケージのダウンロード

この節では、Adobe Commerce ソフトウェアを次のいずれかの方法で入手した場合、サンプルデータをインストールする方法について説明します。

* `https://magento.com/tech-resources/download` から圧縮されたアーカイブをダウンロードしました。

  GitHub からアーカイブをダウンロードした場合、`composer.json` ファイルに `repo.magento.com` の URL が含まれていないので、このメソッドは機能しません。

* 使用済み `composer create-project`

この方法を使用して、Adobe Commerceのサンプルデータを取得できますが、アプリケーションのインストールに使用したのと同じ [ 認証キー ](../prerequisites/authentication-keys.md) を使用する必要があります。

>[!NOTE]
>
>`Could not find package...` や `...no matching package found...` などのエラーが発生した場合は、コマンドに入力ミスがないことを確認してください。 それでもエラーが発生する場合、特にAdobe Commerceを使用している場合は、適切な Composer リポジトリにアクセスできない可能性があります。 [Adobe Commerce サポート ](https://support.magento.com/hc/en-us) にお問い合わせください。

Composer を使用して、アプリケーションのインストールの前または後にサンプル データをインストールできます。ただし、[ 追加のタスク ](remove-or-update.md) が存在する場合があります。

コントリビューションを行う開発者は、[ リポジトリのクローンによるインストール ](git-repositories.md) を参照してください。

>[!WARNING]
>
>アプリケーションが [ 実稼動モード ](../../configuration/bootstrap/application-modes.md#production-mode) に設定されている場合は、サンプルデータをインストールしないでください。 最初に [ 開発者モード ](../../configuration/bootstrap/application-modes.md#developer-mode) に切り替えます。 実稼動モードでのサンプルデータのインストール [ 失敗 ](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-)。

コマンドラインを使用してサンプルデータをインストールするには、`<app_root>` ディレクトリで、ファイルシステムの所有者として次のコマンドを入力します。

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>アプリケーションのインストール後にサンプルデータをインストールする場合は _次のコマンドも実行して、_ ディレクトリ内のデータベースとスキーマを更新する必要があります `<app_root>`。

```bash
bin/magento setup:upgrade
```

アクションを完了するには、[ 認証 ](../prerequisites/authentication-keys.md) する必要があります。

## 認証エラー

次の認証エラーが表示される場合があります。

```
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

エラーが表示された場合は、をアプリケーションのインストールディレクトリに変更して `composer update` を実行します。これにより、[ 認証キー ](../prerequisites/authentication-keys.md) の入力を求められます。

## サンプルデータのインストールの完了

{{$include /help/_includes/sample-data-complete.md}}

<!-- Last updated from includes: 2022-09-08 11:33:05 -->
