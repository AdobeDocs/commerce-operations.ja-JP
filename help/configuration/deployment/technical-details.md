---
title: 技術的な詳細
description: パイプラインデプロイメントの技術的な詳細、設定のタイプ、推奨ワークフローについてお読みください。
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '1252'
ht-degree: 0%

---


# 技術的な詳細

このトピックでは、Commerce 2.2 以降でのパイプラインデプロイメントに関する技術的な実装の詳細について説明します。 改善点は、次の領域に分けられます。

- [設定管理](#configuration-management)
- [管理画面の変更点](#changes-in-the-admin)
- [cron をインストールして削除します。](#install-and-remove-cron)

このトピックでは、 [推奨ワークフロー](#recommended-workflow) パイプラインデプロイメントの例と、その仕組みを理解するのに役立つ例を示します。

開始する前に、 [開発、ビルドおよび実稼動システムの前提条件](../deployment/prerequisites.md).

## 設定管理

開発システムと実稼動システムの設定を同期および維持できるようにするには、次のオーバーライドスキームを使用します。

![設定変数の値の決定方法](../../assets/configuration/override-flow-diagram.png)

図に示すように、設定値は次の順序で使用されます。

1. 環境変数が存在する場合は、その他すべての値を上書きします。
1. 共有設定ファイルから `env.php` および `config.php`. の値 `env.php` 値を上書き `config.php`.
1. データベースに格納された値から。
1. これらのソースに値が存在しない場合は、デフォルト値または NULL が使用されます。

### 共有設定を管理

共有設定は、に保存されます。 `app/etc/config.php`（ソース管理下に置く必要があります）

開発環境 ( またはクラウドインフラストラクチャ上のAdobe Commerce) の管理者で共有設定を設定します。 _統合_) システムに書き込み、設定を次の場所に書き込みます。 `config.php` の使用 [`magento app:config:dump` command](../cli/export-configuration.md).

### システム固有の設定を管理する

システム固有の設定は、 `app/etc/env.php`で、 _not_ ソース管理下にある。

開発 ( またはAdobe Commerce on cloud infrastructure integration) システムの管理者で、システム固有の設定を指定し、その設定をに書き込みます。 `env.php` の使用 [`magento app:config:dump` command](../cli/export-configuration.md).

また、このコマンドは機密設定をに書き込みます。 `env.php`.

### 機密設定の管理

機密設定は、 `app/etc/env.php`.

機密設定は、次のいずれかの方法で管理できます。

- 環境変数
- 機密設定をに保存します。 `env.php` を使用して実稼動システム上で [`magento config:set:sensitive` command](../cli/set-configuration-values.md)

### 管理者でロックされた設定

の設定 `config.php` または `env.php` 管理者にロックされているつまり、これらの設定は管理で変更できません。
以下を使用： [`magento config:set` または `magento config:set --lock`](../cli/export-configuration.md#config-cli-config-set) コマンドを使用して、 `config.php` または `env.php` ファイル。

## コマース管理者

実稼働モードの場合、管理者は次の動作を示します。

- 管理でキャッシュタイプを有効または無効にすることはできません
- 開発者設定を使用できません (**ストア** /設定/ **設定** /詳細 > **開発者**) には、以下が含まれます。

   - CSS、JavaScript、HTMLの縮小
   - CSS と JavaScript の結合
   - サーバー側またはクライアント側の LESS コンパイル
   - インライン翻訳
   - 前述のように、 `config.php` または `env.php` はロックされており、管理者では編集できません。
   - 管理ロケールは、デプロイされたテーマで使用される言語にのみ変更できます

      次の図は、 **アカウント設定** > **インターフェイスロケール** リストに表示されるのは、デプロイ済みの 2 つのロケールのみです。

      ![管理ロケールは、デプロイ済みのロケールにのみ変更できます](../../assets/configuration/split-deploy-admin-locale.png)

- Admin を使用して、どのスコープのロケール設定も変更できません。

   実稼動モードに切り替える前に、これらの変更を行うことをお勧めします。

   ロケールは、環境変数または `config:set` パスを指定した CLI コマンド `general/locale/code`.

## cron をインストールして削除します。

バージョン 2.2 では初めて、 [`magento cron:install` command](../cli/configure-cron-jobs.md). このコマンドは、コマンドを実行するユーザーとして crontab を設定します。

また、crontab を削除するには、 `magento cron:remove` コマンドを使用します。

## 推奨されるパイプラインデプロイメントワークフロー

設定の管理にパイプラインデプロイメントを使用する方法を次の図に示します。

![推奨されるパイプラインデプロイメントワークフロー](../../assets/configuration/split-deploy-workflow.png)

### 開発システム

開発システムで、管理者で設定を変更し、共有設定を生成します。 `app/etc/config.php` システム固有の設定 `app/etc/env.php`. コマースコードと共有設定をソース管理にチェックし、ビルドサーバーにプッシュします。

また、拡張機能をインストールして、開発システム上のコマースコードをカスタマイズする必要があります。

開発システム上で、以下の手順を実行します。

1. 管理者で設定します。

1. 以下を使用： `magento app:config:dump` コマンドを使用して、設定をファイルシステムに書き込みます。

   - `app/etc/config.php` は共有設定で、すべての設定が含まれます _例外_ 機密設定およびシステム固有の設定。 このファイルはソース管理下にある必要があります。
   - `app/etc/env.php` は、特定のシステムに固有の設定（ホスト名やポート番号など）を含む、システム固有の設定です。 このファイルは _not_ ソース管理下にある。

1. 変更したコードと共有設定をソース管理に追加します。

1. 開発中に生成された php コードと静的アセットファイルを削除するには、次のコマンドを実行します。

   ```bash
   rm -r var/view_preprocessed/*
   rm -r pub/static/*/*
   rm -r generated/*/*
   ```

アセットをクリアするコマンドを実行すると、Commerce は作業ファイルを生成します。

>[!WARNING]
>
>上記の方法に注意してください。 の削除 `.htacces`s ファイルを `generated` または `pub` フォルダーが原因で問題が発生する場合があります。

### システムの構築

ビルドシステムは、コードをコンパイルし、Commerce に登録されたテーマの静的ビューファイルを生成します。 Commerce データベースへの接続は必要ありません。必要なのは Commerce コードベースのみです。

ビルドシステム上で、以下の操作を行います。

1. ソース管理から共有設定ファイルを取り出します。
1. 以下を使用： `magento setup:di:compile` コードをコンパイルするためのコマンド。
1. 以下を使用： `magento setup:static-content:deploy -f` コマンドを使用して、静的なファイルビューファイルを更新します。
1. ソース管理への更新を確認します。

>[!INFO]
>
>詳しくは、 [静的ビューファイルの展開戦略](../cli/static-view-file-strategy.md).

### 本番システム

実稼動システム（つまりライブストア）で、生成されたアセットとコードの更新をソース管理から取り込み、コマンドラインまたは環境変数を使用してシステム固有の機密設定を指定します。

本番システムで、以下の手順を実行します。

1. メンテナンスモードを開始します。
1. ソース管理からコードと設定の更新をプルします。
1. Adobe Commerceを使用する場合は、キューワーカーを停止します。
1. 以下を使用： `magento app:config:import` コマンドを使用して、実稼働システムで設定の変更を読み込みます。
1. データベーススキーマを変更したコンポーネントをインストールした場合は、を実行します。 `magento setup:upgrade --keep-generated` をクリックします。
1. システム固有の設定を行うには、 `magento config:set` コマンドまたは環境変数。
1. 機密設定を設定するには、 `magento config:sensitive:set` コマンドまたは環境変数。
1. クリーン ( 別名： _フラッシュ_) キャッシュに書き込まれます。
1. メンテナンスモードを終了します。

## 設定管理コマンド

設定の管理に役立つ次のコマンドを提供しています。

- [`magento app:config:dump`](../cli/export-configuration.md) 管理設定を次の場所に書き込む `config.php` および `env.php` （機密設定を除く）
- [`magento config:set`](../cli/set-configuration-values.md) ：本番システムのシステム固有の設定の値を設定します。

   オプションの `--lock` オプションを使用して管理でオプションをロックします（つまり、設定を編集不可にします）。 設定が既にロックされている場合は、 `--lock` オプションを使用して設定を変更できます。

- [`magento config:sensitive:set`](../cli/set-configuration-values.md) ：本番システムの機密設定の値を設定します。
- [`magento app:config:import`](../cli/import-configuration.md) 設定変更を読み込む `config.php` および `env.php` を本番システムに追加します。

## 設定管理の例

このセクションでは、設定の管理例を示し、 `config.php` および `env.php`.

### デフォルトのロケールの変更

このセクションでは、 `config.php` デフォルトの重み付け単位を変更する場合は、**ストア** /設定/ **設定** /一般/ **一般** > **ロケールオプション**) をクリックします。

管理者に変更を加えた後、を実行します。 `bin/magento app:config:dump` 値を書き込む `config.php`. 値が `general` 配列の下 `locale` 次のスニペットとして `config.php` 表示：

```php
'general' =>
    array (
        'locale' =>
        array (
            'code' => 'en_US',
            'timezone' => 'America/Chicago',
            'weight_unit' => 'kgs'
        )
    )
```

### いくつかの設定を変更

このセクションでは、次の設定変更について説明します。

- Web サイト、ストア、ストア表示 (**ストア** /設定/ **すべてのストア**)
- デフォルトの E メールドメインの変更 (**ストア** /設定/ **設定** /顧客 > **顧客設定**)
- PayPal API ユーザー名と API パスワードの設定 (**ストア** /設定/ **設定** > 販売 > **支払い方法** > **PayPal** > **必要な PayPal 設定**)

管理者に変更を加えた後、を実行します。 `bin/magento app:config:dump` を使用します。 今回は、すべての変更が `config.php`;実際、このファイルに書き込まれるのは、次のスニペットが示すように、web サイト、ストア、ストアビューのみです。

### config.php

`config.php` 次を含む：

- Web サイト、ストア、ストアの表示を変更します。
- システム固有以外の検索エンジン設定
- 機密性の低い PayPal 設定
- 以下から除外された機密設定を通知するコメント `config.php`

`websites` 配列：

```php
      'new' =>
      array (
        'website_id' => '2',
        'code' => 'new',
        'name' => 'New website',
        'sort_order' => '0',
        'default_group_id' => '2',
        'is_default' => '0',
      ),
```

`groups` 配列：

```php
      2 =>
      array (
        'group_id' => '2',
        'website_id' => '2',
        'code' => 'newstore',
        'name' => 'New store',
        'root_category_id' => '2',
        'default_store_id' => '2',
      ),
```

`stores` 配列：

```php
     'newview' =>
      array (
        'store_id' => '2',
        'code' => 'newview',
        'website_id' => '2',
        'group_id' => '2',
        'name' => 'New store view',
        'sort_order' => '0',
        'is_active' => '1',
      ),
```

`payment` 配列：

```php
      'payment' =>
      array (
        'paypal_express' =>
        array (
          'active' => '0',
          'in_context' => '0',
          'title' => 'PayPal Express Checkout',
          'sort_order' => NULL,
          'payment_action' => 'Authorization',
          'visible_on_product' => '1',
          'visible_on_cart' => '1',
          'allowspecific' => '0',
          'verify_peer' => '1',
          'line_items_enabled' => '1',
          'transfer_shipping_options' => '0',
          'solution_type' => 'Mark',
          'require_billing_address' => '0',
          'allow_ba_signup' => 'never',
          'skip_order_review_step' => '1',
        ),
```

### env.php

デフォルトの E メールドメインのシステム固有の設定は、 `app/etc/env.php`.

PayPal 設定は、 `bin/magento app:config:dump` コマンドは機密設定を書き込みません。 次のコマンドを使用して、実稼動システムで PayPal 設定を設定する必要があります。

```bash
bin/magento config:sensitive:set paypal/wpp/api_username <username>
```

```bash
bin/magento config:sensitive:set paypal/wpp/api_password <password>
```
