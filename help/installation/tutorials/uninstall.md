---
title: Adobe Commerceのアンインストールまたは再インストール
description: Adobe Commerceのオンプレミスインストールをアンインストールして再インストールするには、次の手順に従います。
exl-id: fbaeee2c-8da0-4c89-a6d1-882a65014520
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---

# Adobe Commerceのアンインストールまたは再インストール

これらのコマンドを使用する前に、アプリケーションを[ インストールする必要があります](../tutorials/install.md)。

## アプリケーションの更新

アプリケーションを更新するには：

* アーカイブからソフトウェアをインストールした場合、または「composer-create-project」を使用した場合は、[ アップグレードガイド ](../../upgrade/overview.md)を参照してください。
* 提供元の開発者（つまり、`git clone`を使用している）の場合は、[ アプリケーションの更新](../../upgrade/developer/git-installs.md)を参照してください。

## アプリケーションの再インストール

コマンドラインからアプリケーションを再インストールする方法は、役割によって異なります。

* アーカイブからソフトウェアをインストールした場合、または「composer-create-project」を使用した場合は、[ インストール依存関係の更新](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies)を参照してください。
* 提供開発者（つまり、`git clone`を使用し始めた）の場合は、[ インストール依存関係の更新](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies)を参照してください。

## アプリケーションのアンインストール

アプリケーションをアンインストールすると、データベースが削除および復元され、デプロイメント設定が削除され、`var`の下のディレクトリがクリアされます。

アプリケーションをアンインストールするには、次のコマンドを入力します。

```shell
bin/magento setup:uninstall
```

アンインストールが正常に完了したことを確認するには、次のメッセージが表示されます。

```text
[SUCCESS]: Magento uninstallation complete.
```

## 必要に応じて、生成されたファイルを保持

デフォルトでは、`bin/magento setup:upgrade`はコンパイルされたコードとキャッシュをクリアします。 通常、`bin/magento setup:upgrade`を使用してコンポーネントを更新します。各コンポーネントには異なるコンパイル済みクラスが必要になる場合があります。

ただし、状況によっては（特に実稼動環境にデプロイする場合）、コンパイル済みコードのクリアは時間がかかることがあるため、避ける必要があります。 （キャッシュはクリアされたままです）。 コンパイル済みコードを&#x200B;*クリアせずにデータベーススキーマとデータ*&#x200B;を更新するには、次のように入力します。

```shell
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>オプションの`--keep-generated` オプションは、経験豊富なシステムインテグレーター&#x200B;*のみ*&#x200B;が限られた状況で使用する必要があります。 このオプションは、開発環境で&#x200B;*never*&#x200B;を使用する必要があります。 このオプションのパラメーターを不適切に使用すると、コードの実行中にエラーが発生する可能性があります。

## アプリケーションのインストール

* [コマンドラインを使用してインストール](../advanced.md)
