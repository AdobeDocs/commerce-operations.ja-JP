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

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}
- [コマンドライン](../patches/apply.md#command-line)
- [コンポーザー](../patches/apply.md#composer)


>[!TIP]
>
>参照： [ベストプラクティス](../../implementation-playbook/best-practices/maintenance/patching-at-scale.md) エンタープライズ規模でのAdobe Commerceの一元的なパッチ適用について詳しくは、

## コンポーザー

>[!IMPORTANT]
>
>公式のクオリティパッチを適用するには、 [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. カスタムパッチをデプロイする前に、必ず包括的なテストを実施してください。

Composer を使用してカスタム パッチを適用するには：

1. コマンドラインアプリケーションを開き、プロジェクトディレクトリに移動します。
1. を追加 `cweagans/composer-patches` へのプラグイン `composer.json` ファイル。

   ```bash
   composer require cweagans/composer-patches
   ```

1. を編集する `composer.json` をファイルに保存し、次のセクションを追加して指定します。
   - **モジュール：** *\&quot;magento/module-payment\&quot;*
   - **タイトル：** *\&quot;MAGETWO-56934：無効なクレジットカードでAuthorize.netを注文すると、チェックアウトページがフリーズする\&quot;*
   - **パッチを適用するパス：** *\&quot;patches/composer/github-issue-6474.diff\&quot;*

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

1. パッチを適用します。 の使用 `-v` デバッグ情報を表示する場合にのみ選択します。

   ```bash
   composer -v install
   ```

1. を更新 `composer.lock` ファイル。 ロック ファイルは、オブジェクト内の各 Composer パッケージに適用されたパッチを追跡します。

   ```bash
   composer update --lock
   ```

## コマンドライン

コマンドラインからパッチを適用するには：

1. ローカルファイルをにアップロードします `<Magento_root>` ftp、SFTP、SSH、または通常の転送方法を使用しているサーバー上のディレクトリ。
1. としてサーバーにログインします [管理者ユーザー](../../configuration/cli/config-cli.md#prerequisites) ファイルが正しいディレクトリにあることを確認します。
1. コマンドラインインターフェイスで、パッチ拡張機能に従って次のコマンドを実行します。

   ```bash
   patch < patch_file_name.patch
   ```

   このコマンドは、パッチを適用するファイルがパッチ ファイルを基準とした相対パスにあることを前提としています。

   >[!NOTE]
   >
   >コマンドラインに次と表示される場合： `File to patch:`つまり、パスが正しいと思われる場合でも、目的のファイルを見つけることができません。 コマンドラインターミナルに表示されるボックスの最初の行は、パッチを適用するファイルを示します。 ファイルパスをコピーして、に貼り付けます。 `File to patch:` プロンプトを表示して、を押します `Enter` パッチが完了します。

1. 変更を反映するには、の管理画面でキャッシュを更新します。 **システム** > ツール > **キャッシュ管理**.

   または、同じコマンドを使用してパッチをローカルに適用し、正常にコミットおよびプッシュすることもできます。
