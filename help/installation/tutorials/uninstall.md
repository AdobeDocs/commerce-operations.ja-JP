---
title: Adobe Commerceをアンインストールまたは再インストール
description: 次の手順に従って、Adobe Commerceのオンプレミスインストールをアンインストールして再インストールします。
exl-id: fbaeee2c-8da0-4c89-a6d1-882a65014520
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Adobe Commerceをアンインストールまたは再インストール

これらのコマンドを使用する前に、[ アプリケーションをインストールする ](../tutorials/install.md) 必要があります。

## アプリケーションの更新

アプリケーションを更新するには：

* アーカイブからソフトウェアをインストールした場合、または「composer-create-project」を使用した場合は、[ アップグレード ガイド ](../../upgrade/overview.md) を参照してください。
* コントリビューション開発者（つまり、`git clone` を使用した開発者）の場合は、[ アプリケーションの更新 ](../../upgrade/developer/git-installs.md) を参照してください。

## アプリケーションを再インストールします

コマンドラインからアプリケーションを再インストールする方法は、ユーザーの役割によって異なります。

* アーカイブからソフトウェアをインストールした場合、または「composer-create-project」を使用した場合は、[ インストールの依存関係の更新 ](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/) を参照してください。
* 貢献している開発者（つまり、`git clone` を使用し始めた開発者）の場合は、[ インストールの依存関係の更新 ](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/) を参照してください。

## アプリケーションをアンインストールします

アプリケーションをアンインストールすると、データベースが削除されて復元され、配置構成が削除されて、`var` のディレクトリがクリアされます。

アプリケーションをアンインストールするには、次のコマンドを入力します。

```bash
bin/magento setup:uninstall
```

次のメッセージが表示され、アンインストールが正常に完了したことを確認します。

```
[SUCCESS]: Magento uninstallation complete.
```

## オプションで生成されたファイルの保持

デフォルトでは、`bin/magento setup:upgrade` はコンパイル済みコードとキャッシュをクリアします。 通常は、`bin/magento setup:upgrade` を使用してコンポーネントを更新し、各コンポーネントに異なるコンパイル済みクラスを必要とすることができます。

ただし、状況（特に実稼動環境へのデプロイ）によっては、時間がかかるので、コンパイル済みのコードをクリアするのを避けた方がよいでしょう。 （キャッシュはクリアされたままです）。 コンパイル済みコードをクリアせずにデータベース・スキーマおよびデータを更新するには *次のように入力します*

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>オプションの `--keep-generated` オプションは、経験豊富なシステムインテグレーターが限られた状況で使用してください *のみ*。 このオプションは、開発環境では *使用しない* でください。 このオプションパラメーターの使用が正しくないと、コード実行中にエラーが発生する可能性があります。

## アプリケーションのインストール

* [コマンドラインを使用したのインストール](../advanced.md)
