---
title: サンプルのdata Composer パッケージのダウンロード
description: Composer PHP パッケージマネージャーを使用してAdobe Commerce サンプルデータをインストールするには、次の手順に従います。
feature: Install, Deploy
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: 87302734f3ff91f0403beac283ff21925d89318d
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# サンプルのdata Composer パッケージのダウンロード

この節では、次のいずれかの方法でAdobe Commerce ソフトウェアを入手した場合のサンプルデータのインストール方法について説明します。

* `https://magento.com/tech-resources/download`から圧縮アーカイブをダウンロードしました。

  GitHubからアーカイブをダウンロードした場合、`composer.json` ファイルに`repo.magento.com` URLが含まれていないため、このメソッドは機能しません。

* 使用済み`composer create-project`

この方法でAdobe Commerceのサンプルデータを取得できますが、アプリケーションのインストールに使用したのと同じ[認証キー](../prerequisites/authentication-keys.md)を使用する必要があります。

>[!NOTE]
>
>`Could not find package...`や`...no matching package found...`などのエラーが発生した場合は、コマンドにタイプミスがないことを確認してください。 それでもエラーが発生する場合は、特にAdobe Commerceを使用している場合は、適切なComposer リポジトリにアクセスできない可能性があります。 ヘルプについては、[Adobe Commerce サポート &#x200B;](https://support.magento.com/hc/en-us)にお問い合わせください。

Composerを使用して、アプリケーションのインストール前またはインストール後にサンプルデータをインストールできます。ただし、[追加タスク &#x200B;](remove-or-update.md)が発生する場合があります。

提供開発者の場合は、[&#x200B; リポジトリを複製してインストールする](git-repositories.md)を参照してください。

>[!WARNING]
>
>アプリケーションが[実稼動モード &#x200B;](../../configuration/bootstrap/application-modes.md#production-mode)に設定されている場合は、サンプルデータをインストールしないでください。 最初に[開発者モード &#x200B;](../../configuration/bootstrap/application-modes.md#developer-mode)に切り替えます。 サンプルデータを実稼動モード [にインストールできませんでした](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-)。

コマンドラインを使用してサンプルデータをインストールするには、`<app_root>` ディレクトリにファイルシステム所有者として次のコマンドを入力します。

```shell
bin/magento sampledata:deploy
```

>[!WARNING]
>
>アプリケーションをインストールした&#x200B;_後にサンプルデータ_&#x200B;をインストールする場合は、次のコマンドを実行して、`<app_root>` ディレクトリのデータベースとスキーマを更新する必要があります。

```shell
bin/magento setup:upgrade
```

アクションを完了するには、[認証](../prerequisites/authentication-keys.md)する必要があります。

## 認証エラー

次の認証エラーが表示される場合があります。

```text
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

エラーが表示された場合は、アプリケーションのインストールディレクトリに移動して`composer update`を実行し、[認証キー](../prerequisites/authentication-keys.md)の入力を求めます。

## サンプルデータのインストールを完了します

{{$include /help/_includes/sample-data-complete.md}}

<!-- Last updated from includes: 2026-04-17 13:49:36 -->
