---
title: パッチの適用
description: Adobe CommerceまたはMagento Open Sourceプロジェクトにパッチを適用する方法について説明します。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---


# パッチの適用

次のいずれかの方法でパッチを適用できます。

- [品質パッチツール](https://devdocs.magento.com/quality-patches/tool.html)
- [コマンドライン](../patches/apply.md#command-line)
- [コンポーザー](../patches/apply.md#composer)

## コンポーザー

>[!IMPORTANT]
>
>公式の品質パッチを適用するには、 [品質パッチツール](https://devdocs.magento.com/quality-patches/tool.html). カスタムパッチをデプロイする前に、必ず包括的なテストを実行してください。

Composer を使用してカスタムパッチを適用するには：

1. コマンドラインアプリケーションを開き、プロジェクトディレクトリに移動します。
1. を `cweagans/composer-patches` プラグイン `composer.json` ファイル。

   ```bash
   composer require cweagans/composer-patches
   ```

1. を編集します。 `composer.json` ファイルを開き、次のセクションを追加して指定します。
   - **モジュール：** *\&quot;magento/module-payment\&quot;*
   - **タイトル：** *\&quot;MAGETWO-56934:Authorize.net での注文時に、無効なクレジットカードを使用するとチェックアウトページがフリーズする\&quot;*
   - **パッチのパス：** *\&quot;patches/composer/github-issue-6474.diff\&quot;*

   例：

   ```json
   "extra": {
       "composer-exit-on-patch-failure": true,
       "patches": {
           "magento/module-payment": {
               "MAGETWO-56934: Checkout page freezes when ordering with Authorize.net with invalid credit card": "patches/composer/github-issue-6474.diff"
           }
       }
   }
   ```

   パッチが複数のモジュールに影響する場合は、複数のモジュールをターゲットとする複数のパッチファイルを作成する必要があります。

1. パッチを適用します。 以下を使用： `-v` オプションを使用する必要があります。

   ```bash
   composer -v install
   ```

1. を更新します。 `composer.lock` ファイル。 ロックファイルは、オブジェクト内の各 Composer パッケージに適用されたパッチを追跡します。

   ```bash
   composer update --lock
   ```

## コマンドライン

コマンドラインからパッチを適用するには、次の手順に従います。

1. ローカルファイルを `<Magento_root>` FTP、SFTP、SSH、または通常のトランスポート方法を使用して、サーバー上のディレクトリに保存する必要があります。
1. サーバーに、 [管理者ユーザー](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli.html#config-install-cli-first) ファイルが正しいディレクトリにあることを確認します。
1. コマンドラインインターフェイスで、パッチ拡張に従って次のコマンドを実行します。

   ```bash
   patch < patch_file_name.patch
   ```

   このコマンドは、パッチを適用するファイルがパッチファイルを基準として配置されていると想定します。

   >[!NOTE]
   >
   >コマンドラインに次のように表示される場合： `File to patch:`を指定した場合、パスが正しいと思われる場合でも、目的のファイルが見つからないことを意味します。 コマンドラインターミナルに表示されるボックスで、最初の行にパッチを適用するファイルが表示されます。 ファイルパスをコピーし、 `File to patch:` プロンプトと押します `Enter` そして、パッチが完了するはずです。

1. 変更を反映するには、以下の管理者でキャッシュを更新します。 **システム** /ツール/ **キャッシュ管理**.

   または、同じコマンドを使用してローカルにパッチを適用し、正常にコミットしてプッシュすることもできます。
