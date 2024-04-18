---
title: サンプルの Data Composer パッケージのダウンロード
description: Composer PHP Package Manager を使用してAdobe Commerce サンプル データをインストールするには、次の手順に従います。
feature: Install, Deploy
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# サンプルの Data Composer パッケージのダウンロード

この節では、Adobe Commerce ソフトウェアを次のいずれかの方法で入手した場合、サンプルデータをインストールする方法について説明します。

* から圧縮アーカイブをダウンロードしました `https://magento.com/tech-resources/download`.

  GitHub からアーカイブをダウンロードした場合、このメソッドは次の理由で機能しません。 `composer.json` ファイルにが含まれていない `repo.magento.com` URL。

* 使用済み `composer create-project`

この方法を使用してAdobe Commerceのサンプルデータを取得できますが、同じものを使用する必要があります [認証キー](../prerequisites/authentication-keys.md) アプリケーションのインストールに使用した。

>[!NOTE]
>
>エラー（例：）が発生した場合 `Could not find package...` または `...no matching package found...`コマンドに入力ミスがないことを確認します。 それでもエラーが発生する場合、特にAdobe Commerceを使用している場合は、適切な Composer リポジトリにアクセスできない可能性があります。 連絡先 [Adobe Commerce サポート](https://support.magento.com/hc/en-us) ヘルプを参照してください。

Composer を使用して、アプリケーションのインストール前またはインストール後にサンプル データをインストールできます。ただし、次の場合があります [追加のタスク](remove-or-update.md).

コントリビューションする開発者の場合は、を参照してください。 [リポジトリーを複製してインストール](git-repositories.md).

>[!WARNING]
>
>アプリケーションが次のように設定されている場合は、サンプルデータをインストールしないでください [実稼動モード](../../configuration/bootstrap/application-modes.md#production-mode). 切り替え先 [開発者モード](../../configuration/bootstrap/application-modes.md#developer-mode) 1 番目。 実稼動モードでのサンプルデータのインストール [失敗](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

コマンドラインを使用してサンプルデータをインストールするには、ファイルシステムの所有者として次のコマンドを入力します。 `<app_root>` ディレクトリ：

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>サンプルデータをインストールする場合 _後_ アプリケーションをインストールする際には、次のコマンドを実行してのデータベースとスキーマを更新する必要もあります。 `<app_root>` ディレクトリ：

```bash
bin/magento setup:upgrade
```

次が必要です [認証](../prerequisites/authentication-keys.md) をクリックしてアクションを完了します。

## 認証エラー

次の認証エラーが表示される場合があります。

```terminal
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

エラーが表示された場合は、をアプリケーションのインストールディレクトリに変更して実行します。 `composer update`を入力します [認証キー](../prerequisites/authentication-keys.md).

## サンプルデータのインストールの完了

{{$include /help/_includes/sample-data-complete.md}}
