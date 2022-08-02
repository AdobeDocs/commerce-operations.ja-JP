---
title: 実稼動システムの設定
description: コマースアプリケーションの実稼動システムを設定する方法を説明します。
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# 実稼動システムの設定

1 つの実稼動システムを使用できます。 次のすべてが真である必要があります。

- すべてのコマースコードは、開発およびビルドシステムと同じリポジトリ内のソース管理下にあります
- 次のすべてを確認します。 _含む_ ソース管理：

   - `app/etc/config.php`
   - `generated` ディレクトリ（およびサブディレクトリ）
   - `pub/media` directory
   - `pub/media/wysiwyg` ディレクトリ（およびサブディレクトリ）
   - `pub/static` ディレクトリ（およびサブディレクトリ）

- Commerce 2.2 以降をインストールし、次のように設定する必要があります。 [実稼動モード](../bootstrap/application-modes.md#production-mode)
- ファイル・システムの所有権と権限が設定されています。 [開発、ビルド、実稼動システムの前提条件](../deployment/prerequisites.md).

## 実稼動マシンのセットアップ

生産マシンを設定する手順は、次のとおりです。

1. Commerce をインストールした後、またはソース管理から取り込んだ後、本番サーバーにとしてログインするか、に切り替えます。 [ファイルシステム所有者](https://glossary.magento.com/magento-file-system-owner).
1. 作成 `~/.ssh/.composer/auth.json` まだおこなっていない場合は、

   ディレクトリを作成します。

   ```bash
   mkdir -p ~/.ssh/.composer
   ```

   作成 `auth.json` を選択します。

   `auth.json` は、 [認証キー](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

   次に例を示します。

   ```json
   {
      "http-basic": {
         "repo.magento.com": {
            "username": "<your public key>",
            "password": "<your private key>"
         }
      }
   }
   ```

1. 変更をに保存します。 `auth.json`.
1. コピー `<Commerce root dir>/app/etc/env.php` 開発システムから実稼動システムに移行します。
1. 開く `env.php` 必要に応じて値（データベース接続情報など）を変更します。
1. を実行します。 [`magento config:set`](../cli/set-configuration-values.md) または [`magento config:set-sensitive`](../cli/set-configuration-values.md) コマンドを使用して、システム固有の設定値または機密設定値の値をそれぞれ設定します。

   次の節では、例を示します。

## 本番システムでの設定値の設定

この項では、 `magento config:sensitive:set` コマンドを使用します。

機密値を設定する手順は、次のとおりです。

1. 設定する値を、 [機密値の参照](../reference/config-reference-sens.md).
1. 設定の設定パスをメモしておきます。
1. 本番システムに、ファイルシステムの所有者としてログインするか、ファイルシステムの所有者に切り替えます。
1. Commerce のインストールディレクトリに移動します。
1. 次のコマンドを入力します。

   ```bash
   bin/magento config:sensitive:set {configuration path} {value}
   ```

   例えば、YouTube API キーの値をに設定するには、次のようにします。 `1234`を入力して、

   ```bash
   bin/magento config:sensitive:set catalog/product_video/youtube_api_key 1234
   ```

   また、次のように、1 つ以上の値をインタラクティブに設定することもできます。

   ```bash
   bin/magento config:sensitive:set -i
   ```

   プロンプトが表示されたら、機密設定ごとに値を入力するか、Enter キーを押して値をスキップし、次の設定に移動します。

1. 値が設定されたことを確認するには、管理者にログインします。
1. 管理画面で設定を見つけます。

   例えば、YouTube API キー設定は、 **ストア** /設定/ **設定** > **カタログ** > **カタログ** > **製品ビデオ**.

   この設定は管理者に表示され、編集できません。 次の図に例を示します。

   ![管理者の機密設定](../../assets/configuration/sensitive-set.png)
