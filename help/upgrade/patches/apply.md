---
title: パッチを適用
description: Adobe Commerce プロジェクトにパッチを適用する方法について説明します。
exl-id: 1d5d81ad-0115-4575-adfd-dde7c2826d85
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# パッチを適用

パッチは、次のいずれかの方法を使用して適用できます。

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja){target="_blank"}
- [コマンドライン](../patches/apply.md#command-line)
- [Composer](../patches/apply.md#composer)


>[!TIP]
>
>Adobe Commerceのエンタープライズ規模での一元的なパッチ適用について詳しくは、[&#x200B; ベストプラクティス &#x200B;](../../implementation-playbook/best-practices/maintenance/patching-at-scale.md)を参照してください。

## Composer

{{custom-patches-disclaimer}}

Composerを使用してカスタムパッチを適用するには：

1. コマンドラインアプリケーションを開き、プロジェクトディレクトリに移動します。
1. `cweagans/composer-patches` プラグインを`composer.json` ファイルに追加します。

   ```shell
   composer require cweagans/composer-patches
   ```

1. `composer.json` ファイルを編集し、次のセクションを追加して指定します。
   - **モジュール：** *\&quot;magento/module-payment\&quot;*
   - **タイトル：** *\&quot;MAGETWO-56934：無効なクレジットカードでAuthorize.netに注文すると、チェックアウトページがフリーズする\&quot;*
   - **パッチへのパス：** *\&quot;patches/composer/github-issue-6474.diff\&quot;*

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

   パッチが複数のモジュールに影響を与える場合は、複数のモジュールを対象とした複数のパッチファイルを作成する必要があります。

1. パッチを適用します。 デバッグ情報を表示する場合にのみ、`-v` オプションを使用してください。

   ```shell
   composer -v install
   ```

1. `composer.lock` ファイルを更新します。 ロックファイルは、オブジェクト内の各Composer パッケージに適用されたパッチを追跡します。

   ```shell
   composer update --lock
   ```

## コマンドライン

コマンドラインからパッチを適用するには：

1. FTP、SFTP、SSH、または通常のトランスポートメソッドを使用して、ローカルファイルをサーバーの`<Magento_root>` ディレクトリにアップロードします。
1. サーバーに[管理者ユーザー](../../configuration/cli/config-cli.md#prerequisites)としてログインし、ファイルが正しいディレクトリにあることを確認します。
1. コマンドラインインターフェイスで、パッチ拡張機能に従って次のコマンドを実行します。

   ```shell
   patch < patch_file_name.patch
   ```

   このコマンドは、パッチを適用するファイルがパッチ ファイルに関連する場所にあることを前提としています。

   >[!NOTE]
   >
   >コマンドラインに次の内容が表示されている場合は、パスが正しいと思われても、目的のファイルを見つけることができないことを意味します。 `File to patch:`コマンドラインターミナルに表示されるボックスに、最初の行にパッチを適用するファイルが表示されます。 ファイルパスをコピーして`File to patch:` プロンプトに貼り付け、`Enter`を押すと、パッチが完了します。

1. 変更を反映するには、**システム**/ツール/**キャッシュ管理**&#x200B;の下の管理者でキャッシュを更新します。

   あるいは、パッチは同じコマンドを使用してローカルに適用し、コミットして通常どおりにプッシュすることもできます。
