---
title: Adobe Commerceのアンインストールまたは再インストール
description: 次の手順に従って、Adobe CommerceとMagento Open Sourceのオンプレミスインストールをアンインストールして再インストールします。
exl-id: fbaeee2c-8da0-4c89-a6d1-882a65014520
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Adobe Commerceのアンインストールまたは再インストール

これらのコマンドを使用する前に、次の操作を行う必要があります。 [アプリケーションのインストール](../tutorials/install.md).

## アプリケーションの更新

アプリケーションを更新するには、次の手順に従います。

* ソフトウェアをアーカイブからインストールした場合、または&#39;composer-create-project&#39;を使用した場合は、 [アップグレードガイド](../../upgrade/overview.md).
* 貢献している開発者 ( つまり、 `git clone`) を参照してください。 [アプリケーションの更新](../../upgrade/developer/git-installs.md).

## アプリケーションを再インストールする

コマンドラインからアプリケーションを再インストールする方法は、次の役割によって異なります。

* ソフトウェアをアーカイブからインストールした場合、または&#39;composer-create-project&#39;を使用した場合は、 [インストールの依存関係を更新](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).
* 貢献している開発者 ( `git clone`) を参照してください。 [インストールの依存関係を更新](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## アプリケーションのアンインストール

アプリケーションのアンインストールにより、データベースが削除されてリストアされ、デプロイメント設定が削除され、以下のディレクトリがクリアされます。 `var`.

アプリケーションをアンインストールするには、次のコマンドを入力します。

```bash
bin/magento setup:uninstall
```

アンインストールが成功したことを確認する次のメッセージが表示されます。

```terminal
[SUCCESS]: Magento uninstallation complete.
```

## 生成されたファイルを保持する（オプション）

デフォルトでは、 `bin/magento setup:upgrade` は、コンパイル済みのコードとキャッシュをクリアします。 通常、 `bin/magento setup:upgrade` コンポーネントを更新するには、各コンポーネントに異なるコンパイル済みクラスを必要とする場合があります。

ただし、場合によっては（特に実稼動環境にデプロイする場合）、コンパイル済みのコードをクリアしないようにしたい場合があります。これには時間がかかる可能性があります。 （キャッシュはクリアされます）。 データベーススキーマとデータを更新するには *なし* コンパイル済みコードを消去する場合は、次のように入力します。

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>オプションの `--keep-generated` 経験豊富なシステムインテグレーターが、限られた状況でオプションを使用する必要がある *のみ*. このオプションは、 *なし* を開発環境で使用する。 このオプションパラメーターを不適切に使用すると、コードの実行中にエラーが発生する可能性があります。

## アプリケーションのインストール

* [コマンドラインを使用してインストールする](../advanced.md)
