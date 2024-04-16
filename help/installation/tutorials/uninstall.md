---
title: Adobe Commerceをアンインストールまたは再インストール
description: 次の手順に従って、Adobe Commerceのオンプレミスインストールをアンインストールして再インストールします。
exl-id: fbaeee2c-8da0-4c89-a6d1-882a65014520
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Adobe Commerceをアンインストールまたは再インストール

これらのコマンドを使用する前に、次の操作が必要です [アプリケーションのインストール](../tutorials/install.md).

## アプリケーションの更新

アプリケーションを更新するには：

* アーカイブからソフトウェアをインストールした場合、または「composer-create-project」を使用した場合は、 [アップグレードガイド](../../upgrade/overview.md).
* コントリビューションを行う開発者（つまり、 `git clone`）、を参照してください [アプリケーションの更新](../../upgrade/developer/git-installs.md).

## アプリケーションを再インストールします

コマンドラインからアプリケーションを再インストールする方法は、ユーザーの役割によって異なります。

* アーカイブからソフトウェアをインストールした場合、または「composer-create-project」を使用した場合は、を参照してください。 [インストールの依存関係の更新](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).
* コントリビューションを行う開発者は、を使用し始めています `git clone`）、を参照してください [インストールの依存関係の更新](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## アプリケーションをアンインストールします

アプリケーションをアンインストールすると、データベースが削除されて復元され、配置設定が削除されて、次のディレクトリがクリアされます `var`.

アプリケーションをアンインストールするには、次のコマンドを入力します。

```bash
bin/magento setup:uninstall
```

次のメッセージが表示され、アンインストールが正常に完了したことを確認します。

```terminal
[SUCCESS]: Magento uninstallation complete.
```

## オプションで生成されたファイルの保持

デフォルトでは `bin/magento setup:upgrade` コンパイル済みのコードとキャッシュをクリアします。 通常は、を使用します `bin/magento setup:upgrade` コンポーネントと各コンポーネントを更新するには、異なるコンパイル済みクラスが必要になる場合があります。

ただし、状況（特に実稼動環境へのデプロイ）によっては、時間がかかるので、コンパイル済みのコードをクリアするのを避けた方がよいでしょう。 （キャッシュはクリアされたままです）。 データベーススキーマとデータを更新するには *なし* コンパイル済みコードをクリアして、次のように入力します。

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>オプション `--keep-generated` オプションは、経験豊富なシステムインテグレーターが限られた状況で使用する必要があります。 *のみ*. このオプションは、 *なし* 開発環境で使用される。 このオプションパラメーターの使用が正しくないと、コード実行中にエラーが発生する可能性があります。

## アプリケーションのインストール

* [コマンドラインを使用したのインストール](../advanced.md)
