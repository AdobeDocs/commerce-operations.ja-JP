---
title: サンプルの Data Composer パッケージをダウンロードします。
description: Composer PHP Package Manager を使用してAdobe CommerceおよびMagento Open Sourceサンプルデータをインストールするには、次の手順に従います。
feature: Install, Deploy
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# サンプルの Data Composer パッケージをダウンロードします。

この節では、次のいずれかの方法でAdobe CommerceまたはMagento Open Sourceソフトウェアを入手した場合に、サンプルデータをインストールする方法について説明します。

* 圧縮されたアーカイブをからダウンロード `https://magento.com/tech-resources/download`.

  GitHub からアーカイブをダウンロードした場合、このメソッドは機能しません。これは、 `composer.json` ファイルに `repo.magento.com` URL。

* 使用済み `composer create-project`

この方法を使用して、Adobe CommerceとMagento Open Sourceの両方のサンプルデータを取得できますが、同じ方法を使用する必要があります [認証キー](../prerequisites/authentication-keys.md) アプリケーションのインストールに使用した

>[!NOTE]
>
>次のようなエラーが発生した場合： `Could not find package...` または `...no matching package found...`で、コマンドに入力ミスがないことを確認します。 それでもエラーが発生する場合、特にAdobe Commerceを使用している場合は、適切な Composer リポジトリにアクセスできない可能性があります。 連絡先 [Adobe Commerceサポート](https://support.magento.com/hc/en-us) を参照してください。

Composer を使用して、アプリケーションのインストール前またはインストール後にサンプルデータをインストールできます。ただし、次の場合があります [その他のタスク](remove-or-update.md).

貢献する開発者の場合は、 [リポジトリの複製によるインストール](git-repositories.md).

>[!WARNING]
>
>アプリケーションが [実稼動モード](../../configuration/bootstrap/application-modes.md#production-mode). 切り替え先 [開発者モード](../../configuration/bootstrap/application-modes.md#developer-mode) 1 つ目は。 実稼働モードでのサンプルデータのインストール [失敗](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

コマンドラインを使用してサンプルデータをインストールするには、次のコマンドをファイルシステムの所有者として `<app_root>` ディレクトリ：

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>サンプルデータをインストールする場合 _次より後_ アプリケーションをインストールする場合は、次のコマンドを実行して、 `<app_root>` ディレクトリ：

```bash
bin/magento setup:upgrade
```

次の操作が必要です。 [認証](../prerequisites/authentication-keys.md) 」をクリックしてアクションを完了します。

## 認証エラー

次の認証エラーが表示される場合があります。

```terminal
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

エラーが表示された場合は、アプリケーションのインストールディレクトリに移動して、を実行します。 `composer update`をクリックします。これにより、 [認証キー](../prerequisites/authentication-keys.md).

## サンプルデータのインストールを完了します。

{{$include /help/_includes/sample-data-complete.md}}
