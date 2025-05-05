---
title: パッチの適用
description: Adobe Commerce プロジェクトにパッチを適用する方法について説明します。
exl-id: 1d5d81ad-0115-4575-adfd-dde7c2826d85
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# パッチの適用

パッチは、次のいずれかの方法で適用できます。

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja){target="_blank"}
- [コマンドライン](../patches/apply.md#command-line)
- [コンポーザー](../patches/apply.md#composer)


>[!TIP]
>
>企業規模でのAdobe Commerceの一元的なパッチ適用については、[ ベストプラクティス ](../../implementation-playbook/best-practices/maintenance/patching-at-scale.md) を参照してください。

## コンポーザー

>[!IMPORTANT]
>
>公式の品質パッチを適用するには、[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja){target="_blank"} を使用します。 カスタムパッチをデプロイする前に、必ず包括的なテストを実施してください。

Composer を使用してカスタム パッチを適用するには：

1. コマンドラインアプリケーションを開き、プロジェクトディレクトリに移動します。
1. `composer.json` ファイルに `cweagans/composer-patches` プラグインを追加します。

   ```bash
   composer require cweagans/composer-patches
   ```

1. `composer.json` ファイルを編集し、次のセクションを追加して指定します。
   - **Module:** *\&quot;magento/module-payment\&quot;*
   - **タイトル：** *\&quot;MAGETWO-56934：無効なクレジットカードでAuthorize.netを注文すると、チェックアウトページがフリーズする\&quot;*
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

   パッチが複数のモジュールに影響を与える場合は、複数のモジュールをターゲットとする複数のパッチファイルを作成する必要があります。

1. パッチを適用します。 デバッグ情報を表示する場合にのみ、「`-v`」オプションを使用します。

   ```bash
   composer -v install
   ```

1. `composer.lock` ファイルを更新します。 ロック ファイルは、オブジェクト内の各 Composer パッケージに適用されたパッチを追跡します。

   ```bash
   composer update --lock
   ```

## コマンドライン

コマンドラインからパッチを適用するには：

1. FTP、SFTP、SSH、または通常の転送方法を使用して、ローカルファイルをサーバー上の `<Magento_root>` ディレクトリにアップロードします。
1. [admin ユーザー ](../../configuration/cli/config-cli.md#prerequisites) としてサーバーにログインし、ファイルが正しいディレクトリにあることを確認します。
1. コマンドラインインターフェイスで、パッチ拡張機能に従って次のコマンドを実行します。

   ```bash
   patch < patch_file_name.patch
   ```

   このコマンドは、パッチを適用するファイルがパッチ ファイルを基準とした相対パスにあることを前提としています。

   >[!NOTE]
   >
   >コマンドラインに「`File to patch:`」と表示されている場合は、パスが正しく見えても、目的のファイルを見つけることができないことを意味します。 コマンドラインターミナルに表示されるボックスの最初の行は、パッチを適用するファイルを示します。 ファイルパスをコピーして `File to patch:` プロンプトに貼り付け、`Enter` キーを押すと、パッチが完了します。

1. 変更を反映するには、管理画面の **システム**/ツール/**キャッシュ管理** でキャッシュを更新します。

   または、同じコマンドを使用してパッチをローカルに適用し、正常にコミットおよびプッシュすることもできます。
