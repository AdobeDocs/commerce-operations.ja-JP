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
- 次のすべてがソース管理に含まれている _含まれている_ ことを確認します。

   - `app/etc/config.php`
   - `generated` ディレクトリ（およびサブディレクトリ）
   - `pub/media` ディレクトリ
   - `pub/media/wysiwyg` ディレクトリ（およびサブディレクトリ）
   - `pub/static` ディレクトリ（およびサブディレクトリ）

- Commerce 2.2 以降がインストールされ、[&#x200B; 実稼動モード &#x200B;](../bootstrap/application-modes.md#production-mode) に設定されている必要があります
- [&#x200B; 開発、ビルド、実稼働システムの前提条件 &#x200B;](../deployment/prerequisites.md) で説明されているように、ファイルシステムの所有権と権限が設定されています。

## 実稼動マシンの設定

実稼動マシンを設定するには：

1. Commerceをインストールするか、ソース管理から取り出した後、ファイルシステムのオーナーとして実稼動サーバーにログインするか、切り替えます。
1. まだ作成していない場合は、`~/.ssh/.composer/auth.json` を作成します。

   次のディレクトリを作成します。

   ```bash
   mkdir -p ~/.ssh/.composer
   ```

   そのディレクトリに `auth.json` を作成します。

   `auth.json` 認証キー [&#x200B; が含まれている必要があり &#x200B;](../../installation/prerequisites/authentication-keys.md) す。

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

1. `auth.json` に対する変更を保存します。
1. 開発システムから実稼動システムに `<Commerce root dir>/app/etc/env.php` をコピーします。
1. `env.php` をテキストエディターで開き、必要な値（データベース接続情報など）を変更します。
1. [`magento config:set`](../cli/set-configuration-values.md) または [`magento config:set-sensitive`](../cli/set-configuration-values.md) コマンドを実行して、それぞれシステム固有の設定値または機密設定値を設定します。

   次の節で例を示します。

## 実稼動システムでの設定値の設定

この節では、`magento config:sensitive:set` コマンドを使用して、実稼動システムに機密性の高い値を設定する方法について説明します。

機密性の高い値を設定するには：

1. [&#x200B; 大文字と小文字を区別した値参照 &#x200B;](../reference/config-reference-sens.md) を使用して、設定する値を検索します。
1. 設定の設定パスをメモしておきます。
1. ファイルシステムの所有者として実稼動システムにログインするか、所有者に切り替えます。
1. Commerce インストールディレクトリに移動します。
1. 次のコマンドを入力します。

   ```bash
   bin/magento config:sensitive:set {configuration path} {value}
   ```

   例えば、YouTube API キーの値を `1234` に設定するには、と入力します。

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

   例えば、YouTube API キー設定は、**Stores**/設定/**Configuration**/**Catalog**/**Catalog**/**Product Video** にあります。

   設定は管理者に表示され、編集できません。 次の図に例を示します。

   ![Admin の機密設定 &#x200B;](../../assets/configuration/sensitive-set.png)
