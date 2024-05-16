---
title: 実稼動システムのセットアップ
description: Commerce アプリケーションの実稼動システムの設定方法について説明します。
exl-id: e678e97e-d9f2-4f24-bb6b-1994a2a1167c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# 実稼動システムのセットアップ

1 つの実稼動システムを持つことができます。 次のすべてに該当する必要があります。

- すべてのCommerce コードは、開発システムおよびビルドシステムと同じリポジトリ内のソース管理にあります
- 次のすべてを確認します _included_ ソース管理で、次の操作を行います。

   - `app/etc/config.php`
   - `generated` ディレクトリ（およびサブディレクトリ）
   - `pub/media` directory
   - `pub/media/wysiwyg` ディレクトリ（およびサブディレクトリ）
   - `pub/static` ディレクトリ（およびサブディレクトリ）

- Commerce 2.2 以降をインストールして、次のように設定する必要があります [実稼動モード](../bootstrap/application-modes.md#production-mode)
- ファイル・システムの所有権と権限が設定されています（を参照）。 [開発、ビルド、実稼動システムの前提条件](../deployment/prerequisites.md).

## 実稼動マシンの設定

実稼動マシンを設定するには：

1. Commerceをインストールするか、ソース管理から取り出した後、ファイルシステムのオーナーとして実稼動サーバーにログインするか、切り替えます。
1. 作成 `~/.ssh/.composer/auth.json` まだ行っていない場合は、

   次のディレクトリを作成します。

   ```bash
   mkdir -p ~/.ssh/.composer
   ```

   作成 `auth.json` そのディレクトリ内。

   `auth.json` を含める必要があります [認証キー](../../installation/prerequisites/authentication-keys.md).

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
1. コピー `<Commerce root dir>/app/etc/env.php` 開発システムから実稼動システムへ。
1. 開く `env.php` テキスト・エディタで、必要な値（データベース接続情報など）を変更します。
1. を実行 [`magento config:set`](../cli/set-configuration-values.md) または [`magento config:set-sensitive`](../cli/set-configuration-values.md) コマンドを使用して、システム固有の設定値または機密性の高い設定値をそれぞれ設定できます。

   次の節で例を示します。

## 実稼動システムでの設定値の設定

この節では、を使用して、実稼動システムに機密性の高い値を設定する方法について説明します `magento config:sensitive:set` コマンド。

機密性の高い値を設定するには：

1. を使用して、設定する値を検索します [機密性の高い値参照](../reference/config-reference-sens.md).
1. 設定の設定パスをメモしておきます。
1. ファイルシステムの所有者として実稼動システムにログインするか、所有者に切り替えます。
1. Commerce インストールディレクトリに移動します。
1. 次のコマンドを入力します。

   ```bash
   bin/magento config:sensitive:set {configuration path} {value}
   ```

   例えば、YouTube API キーの値をに設定するには `1234`、と入力します

   ```bash
   bin/magento config:sensitive:set catalog/product_video/youtube_api_key 1234
   ```

   また、次のように、1 つ以上の値をインタラクティブに設定することもできます。

   ```bash
   bin/magento config:sensitive:set -i
   ```

   プロンプトが表示されたら、各機密設定の値を入力するか、Enter キーを押して値をスキップし、次の値に移動します。

1. 値が設定されたことを確認するには、管理者にログインします。
1. 管理者で、設定を見つけます。

   例えば、YouTube API キーの設定は、次の場所にあります。 **ストア** > 設定 > **設定** > **カタログ** > **カタログ** > **製品ビデオ**.

   設定は管理者に表示され、編集できません。 次の図に例を示します。

   ![管理の機密設定](../../assets/configuration/sensitive-set.png)
