---
title: サードパーティ拡張機能の管理
description: Adobe Commerce Extensions をインストール、有効化、アップグレード、アンインストールするには、次の手順に従います。
exl-id: b564662a-2e5f-4fa9-bae1-ca7498478fa9
source-git-commit: f057cf082eeab1e34957e284817c6b93517de21b
workflow-type: tm+mt
source-wordcount: '802'
ht-degree: 0%

---


# サードパーティ拡張機能の管理

Adobe Commerceの動作を拡張またはカスタマイズするコードは、拡張機能と呼ばれます。 オプションで、[ Commerce Marketplaceまたは別の拡張機能配布システムで ](https://commercemarketplace.adobe.com/) 拡張機能をパッケージ化して配布できます。

拡張機能には次のものが含まれます。

- モジュール（Adobe Commerceの機能の拡張）
- テーマ（ストアフロントと管理者のルックアンドフィールを変更）
- 言語パッケージ （ストアフロントをローカライズおよび管理者）

ここでは、コマンド ライン インターフェイスを使用して、（オンプレミス _プロジェクトのCommerce Marketplaceから購入したサード パーティ製の拡張機能を管理する方法について説明します_。 クラウドインフラストラクチャプロジェクトの場合は、[ 拡張機能の管理 ](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/configure-store/extensions) を参照してください。

_any_ 拡張機能のインストールにも同じ手順を使用できます。必要なのは、拡張機能の Composer 名とバージョンだけです。 これを見つけるには、拡張機能の `composer.json` ファイルを開き、`"name"` と `"version"` の値を確認します。

## インストール

インストールの前に、次の操作を行うことができます。

1. データベースをバックアップします。
1. メンテナンスモードを有効にする：

   ```bash
   bin/magento maintenance:enable
   ```

拡張機能をインストールするには、次の手順を実行します。

1. Commerce Marketplaceまたは別の拡張機能開発者から拡張機能を取得します。
1. Commerce Marketplaceから拡張機能をインストールする場合は、`repo.magento.com` リポジトリが `composer.json` ファイルに存在することを確認します。

   ```bash
   "repositories": [
       {
           "type": "composer",
           "url": "https://repo.magento.com/"
       }
   ]
   ```

1. 拡張機能の Composer 名とバージョンを取得します。
1. プロジェクトの `composer.json` ファイルを拡張子の名前とバージョンで更新します。
1. 拡張機能が正しくインストールされていることを確認します。
1. 拡張機能を有効にして設定します。

### 拡張機能に関する情報の取得

拡張機能の Composer 名とバージョンが既にわかっている場合は、この手順をスキップして [`composer.json` ファイルを更新 ](#update-composer-dependencies) に進みます。

Commerce Marketplaceから拡張機能の Composer 名とバージョンを取得するには：

1. 拡張機能の購入に使用したユーザー名とパスワードを使用して [&#128279;](https://commercemarketplace.adobe.com/)Commerce Marketplaceにログインします。

1. 右上隅で、**あなたの名前**/**マイプロファイル** をクリックします。

   ![Marketplace アカウントにアクセス ](../../assets/installation/marketplace-my-profile.png)

1. **購入状況** をクリックします。

   ![Marketplace の購入履歴 ](../../assets/installation//marketplace-my-purchases.png)

1. インストールする拡張機能を見つけ、コンポーネント名とバージョンをメモします。

   ![ 技術的な詳細は、拡張機能の Composer 名を示します ](../../assets/installation/marketplace-extension-technical-details.png)

>[!TIP]
>
>または、Composer の名前とバージョン _any_ 拡張子（Commerce Marketplaceで購入したか他の場所で購入したか）は、拡張機能の `composer.json` ファイルにあります。

### Composer の依存関係の更新

拡張機能の名前とバージョンを `composer.json` ファイルに追加します。

1. プロジェクトディレクトリに移動して `composer.json` ファイルを更新します。

   ```bash
   composer require <component-name>:<version>
   ```

   以下に例を挙げます。

   ```bash
   composer require j2t/module-payplug:2.0.2
   ```

1. [ 認証キー ](../prerequisites/authentication-keys.md) を入力します。 公開鍵はユーザー名で、秘密鍵はパスワードです。

1. Composer がプロジェクトの依存関係の更新を完了するのを待ち、エラーがないことを確認します。

   ```
   Updating dependencies (including require-dev)
   Package operations: 1 install, 0 updates, 0 removals
     - Installing j2t/module-payplug (2.0.2): Downloading (100%)
   Writing lock file
   Generating autoload files
   ```

### インストールの確認

拡張機能が正しくインストールされていることを確認するには、次のコマンドを実行します。

```bash
bin/magento module:status J2t_Payplug
```

デフォルトでは、おそらく次の設定で拡張機能が無効になっています。

```
Module is disabled
```

拡張子の名前は `<VendorName>_<ComponentName>` の形式です。これは Composer 名とは異なる形式です。 この形式を使用して、拡張機能を有効にします。 拡張機能名がわからない場合は、次を実行します。

```bash
bin/magento module:status
```

そして、「無効なモジュールのリスト」の下の拡張機能を探します。

### Enable （有効）

一部の拡張子は、生成された静的ビューファイルを最初にクリアしない限り、正しく機能しません。 拡張機能を有効にする際に、静的ビューファイルをクリアするには、「`--clear-static-content`」オプションを使用します。

1. 拡張機能を有効にし、静的ビューファイルをクリアします。

   ```bash
   bin/magento module:enable J2t_Payplug --clear-static-content
   ```

   次の出力が表示されます。

   ```
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

1. プロジェクトの再コンパイル：実稼動モードでは、「Magentoコンパイルコマンドを再実行してください」というメッセージが表示される場合があります。 コンパイル コマンドを開発者モードで実行するように求めるメッセージは表示されません。

   ```bash
   bin/magento setup:di:compile
   ```

1. 拡張機能が有効になっていることを確認します。

   ```bash
   bin/magento module:status J2t_Payplug
   ```

   拡張機能が無効になっていないことを確認する出力が表示されます。

   ```
   Module is enabled
   ```

1. キャッシュのクリーンアップ：

   ```bash
   bin/magento cache:clean
   ```

1. 必要に応じて、管理者で拡張機能を設定します。

>[!TIP]
>
>ブラウザーでストアフロントを読み込む際にエラーが発生した場合は、次のコマンドを使用してキャッシュをクリアします：`bin/magento cache:flush`。

## アップグレード

モジュールまたは拡張機能を更新またはアップグレードするには：

1. Marketplace または別の拡張機能開発者から、更新されたファイルをダウンロードします。 モジュール名とバージョンをメモします。

1. 内容をアプリケーションのルートディレクトリに書き出します。

1. モジュール用の Composer パッケージが存在する場合は、次のいずれかを実行します。

   モジュール名ごとのアップデート：

   ```bash
   composer update vendor/module-name
   ```

   バージョンごとのアップデート：

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. 次のコマンドを実行して、キャッシュをアップグレード、デプロイおよびクリーンアップします。

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```

## Uninstall

サードパーティの拡張機能を削除する手順については、拡張機能のベンダーにお問い合わせください。 指示には、次の情報が記載されています。

- データベーステーブルの変更を元に戻す方法
- データベースのデータ変更を元に戻す方法
- どのファイルを削除または元に戻すか

>[!CAUTION]
>
>実稼動以外の環境でアンインストール手順を実行し _最初_、実稼動環境にデプロイする前に十分にテストします。

次の手順では、サードパーティの拡張機能をアンインストールする際の一般的な情報を示します。

1. Adobe Commerce プロジェクトリポジトリから拡張機能を削除します。

   - Composer ベースの拡張子の場合、Adobe Commerce `composer.json` ファイルから拡張子を削除します。

     ```bash
     composer remove <component-name>
     ```

   - Composer ベース以外の拡張機能の場合は、Adobe Commerce プロジェクトリポジトリから物理ファイルを削除します。

     ```bash
     rm -rf app/code/<vendor-name>/<component-name>
     ```

1. `config.php` ファイルがAdobe Commerce プロジェクトリポジトリのソース管理下にある場合は、`config.php` ファイルから拡張子を削除します。

1. ローカルデータベースをテストし、ベンダーが提供する手順が期待どおりに動作することを確認します。

1. 拡張機能が適切に無効になっていることと、Web サイトがステージング環境で期待どおりに動作していることを確認します。

1. 実稼動環境に変更をデプロイします。
