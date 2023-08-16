---
title: 拡張機能のインストール
description: 次の手順に従って、Adobe CommerceまたはMagento Open Source拡張機能をインストールします。
exl-id: b564662a-2e5f-4fa9-bae1-ca7498478fa9
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---

# 拡張機能のインストール

Adobe CommerceとMagento Open Sourceの動作を拡張またはカスタマイズするコードは、拡張機能と呼ばれます。 オプションで、 [Commerce Marketplace](https://marketplace.magento.com) または別の拡張配信システム

拡張機能には以下が含まれます。

- モジュール (Adobe CommerceおよびMagento Open Source機能の拡張 )
- テーマ（ストアフロントと管理者の外観と操作性を変更する）
- 言語パッケージ（ストアフロントと管理者をローカライズ）

>[!TIP]
>
>このトピックでは、コマンドラインを使用して、Commerce Marketplaceから購入した拡張機能をインストールする方法について説明します。 同じ手順を使用して、 _任意_ 拡張機能。必要なのは、拡張機能のコンポーザー名とバージョンだけです。 検索するには、拡張機能の `composer.json` ファイルを作成し、 `"name"` および `"version"`.

インストール前に、次の作業を行うことができます。

1. データベースをバックアップします。
1. メンテナンスモードを有効にする：

   ```bash
   bin/magento maintenance:enable
   ```

拡張機能をインストールするには、次の操作をおこなう必要があります。

1. 拡張機能は、Commerce Marketplaceまたは他の拡張機能開発者から取得します。
1. 拡張機能をCommerce Marketplaceからインストールする場合は、必ず `repo.magento.com` リポジトリが次の場所に存在します： `composer.json` ファイル：

   ```bash
   "repositories": [
       {
           "type": "composer",
           "url": "https://repo.magento.com/"
       }
   ]
   ```

1. 拡張機能のコンポーザーの名前とバージョンを取得します。
1. を更新します。 `composer.json` ファイルの拡張子の名前とバージョンを指定します。
1. 拡張機能が正しくインストールされていることを確認します。
1. 拡張機能を有効にして設定します。

## 拡張機能コンポーザーの名前とバージョンの取得

拡張機能のコンポーザー名とバージョンが既にわかっている場合は、この手順をスキップして、次に進んでください。 [を更新します。 `composer.json` ファイル](#update-your-composer-file).

拡張機能から拡張機能のコンポーザー名とバージョンを取得するには、次のCommerce Marketplaceを実行します。

1. にログインします。 [Commerce Marketplace](https://marketplace.magento.com) 拡張機能の購入に使用したユーザー名とパスワード。

1. 右上隅で、 **お客様の名前** > **マイプロファイル**.

   ![Marketplace アカウントへのアクセス](../../assets/installation/marketplace-my-profile.png)

1. クリック **マイ購入**.

   ![Marketplace の購入履歴](../../assets/installation//marketplace-my-purchases.png)

1. インストールする拡張機能を見つけ、「 」をクリックします。 **技術的な詳細**.

   ![技術的な詳細は、拡張機能のコンポーザー名を示します](../../assets/installation/marketplace-extension-technical-details.png)

>[!TIP]
>
>または、のコンポーザー名とバージョンを確認できます。 _任意_ 拡張機能の拡張機能 (Commerce Marketplaceまたはその他の場所で購入したかどうか ) `composer.json` ファイル。

## Composer ファイルを更新する

拡張機能の名前とバージョンを `composer.json` ファイル：

1. プロジェクトディレクトリに移動し、を更新します。 `composer.json` ファイル。

   ```bash
   composer require <component-name>:<version>
   ```

   以下に例を挙げます。

   ```bash
   composer require j2t/module-payplug:2.0.2
   ```

1. を入力します。 [認証キー](../prerequisites/authentication-keys.md). 公開鍵はユーザー名、秘密鍵はパスワードです。

1. Composer がプロジェクトの依存関係の更新を完了するのを待ち、エラーがないことを確認します。

   ```terminal
   Updating dependencies (including require-dev)
   Package operations: 1 install, 0 updates, 0 removals
     - Installing j2t/module-payplug (2.0.2): Downloading (100%)
   Writing lock file
   Generating autoload files
   ```

## 拡張機能の検証

拡張機能が正しくインストールされていることを確認するには、次のコマンドを実行します。

```bash
bin/magento module:status J2t_Payplug
```

デフォルトでは、拡張機能はおそらく無効になっています。

```terminal
Module is disabled
```

拡張機能の名前の形式はです `<VendorName>_<ComponentName>`。これは、コンポーザー名とは異なる形式です。 この形式を使用して、拡張機能を有効にします。 拡張機能名が不明な場合は、次のコマンドを実行します。

```bash
bin/magento module:status
```

「無効なモジュールのリスト」の下に拡張機能があるかを確認します。

## 拡張機能の有効化

生成された静的ビューファイルを最初にクリアしない限り、一部の拡張子は正しく機能しません。 以下を使用します。 `--clear-static-content` 拡張機能を有効にしているときに静的表示ファイルをクリアするオプション。

1. 拡張機能を有効にし、静的表示ファイルをクリアします。

   ```bash
   bin/magento module:enable J2t_Payplug --clear-static-content
   ```

   次の出力が表示されます。

   ```terminal
   The following modules have been enabled:
   - J2t_Payplug
   
   To make sure that the enabled modules are properly registered, run 'setup:upgrade'.
   Cache cleared successfully.
   Generated classes cleared successfully. Please run the 'setup:di:compile' command to generate classes.
   Generated static view files cleared successfully.
   ```

1. 拡張機能を登録します。

   ```bash
   bin/magento setup:upgrade
   ```

1. プロジェクトを再コンパイルします：実稼働モードでは、「実稼働コンパイルコマンドを再実行してください」というメッセージが表示される場合があります。 開発者モードでコンパイルコマンドを実行するよう求めるプロンプトは表示されません。

   ```bash
   bin/magento setup:di:compile
   ```

1. 拡張機能が有効になっていることを確認します。

   ```bash
   bin/magento module:status J2t_Payplug
   ```

   次の出力で、拡張機能が無効化されていないことを確認できます。

   ```terminal
   Module is enabled
   ```

1. キャッシュをクリーンアップします。

   ```bash
   bin/magento cache:clean
   ```

1. 必要に応じて、管理で拡張機能を設定します。

>[!TIP]
>
>ブラウザーでストアフロントを読み込む際にエラーが発生した場合は、次のコマンドを使用してキャッシュをクリアします。 `bin/magento cache:flush`.

## 拡張機能のアップグレード

モジュールまたは拡張機能を更新またはアップグレードするには：

1. Marketplace または他の拡張機能の開発者から、更新したファイルをダウンロードします。 モジュールの名前とバージョンをメモしておきます。

1. コンテンツをアプリケーションのルートディレクトリに書き出します。

1. モジュール用の Composer パッケージが存在する場合は、次のいずれかを実行します。

   モジュール名ごとに更新：

   ```bash
   composer update vendor/module-name
   ```

   バージョンごとに更新：

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. 次のコマンドを実行して、キャッシュをアップグレード、デプロイ、クリーンアップします。

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```
