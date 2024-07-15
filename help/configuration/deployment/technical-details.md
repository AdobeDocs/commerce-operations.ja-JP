---
title: 技術的詳細
description: パイプラインデプロイメントの技術的な詳細、設定のタイプ、推奨されるワークフローについて説明します。
exl-id: a396d241-f895-4414-92af-3abf3511e62a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1254'
ht-degree: 0%

---

# 技術的詳細

このトピックでは、Commerce 2.2 以降でのパイプラインのデプロイメントに関する技術的実装の詳細について説明します。 改善点は次の領域に分けることができます。

- [設定管理](#configuration-management)
- [管理者における変更](#changes-in-the-admin)
- [Cron のインストールと削除](#install-and-remove-cron)

また、このトピックでは、パイプラインデプロイメントの [ 推奨ワークフロー ](#recommended-workflow) についても説明し、その仕組みを理解するのに役立つ例を示します。

開始する前に、[ 開発、ビルド、実稼動のシステムの前提条件 ](../deployment/prerequisites.md) を確認してください。

## 設定管理

開発システムと実稼動システムの設定を同期および維持できるようにするには、次のオーバーライドスキームを使用します。

![ 設定変数値の決定方法 ](../../assets/configuration/override-flow-diagram.png)

次の図に示すように、設定値は次の順序で使用されます。

1. 環境変数が存在する場合は、他のすべての値を上書きします。
1. 共有設定ファイル `env.php` および `config.php` から。 `env.php` の値は、`config.php` の値を上書きします。
1. データベースに格納されている値から。
1. これらのソースに値が存在しない場合は、デフォルト値または NULL が使用されます。

### 共有設定の管理

共有設定は `app/etc/config.php` に保存され、ソース管理下に置く必要があります。

開発環境（またはクラウドインフラストラクチャー上のAdobe Commerce _integration_）システムの管理者で共有設定を指定し、[`magento app:config:dump` コマンドを使用して設定を `config.php` に書き込みます ](../cli/export-configuration.md)。

### システム固有の設定の管理

システム固有の設定は `app/etc/env.php` に保存されますが、これはソース管理 _にすべきではありません_。

開発（またはクラウドインフラストラクチャ統合のAdobe Commerce）システムの管理者でシステム固有の設定を行い、[`magento app:config:dump` コマンドを使用して設定を `env.php` に書き込みます ](../cli/export-configuration.md)。

また、このコマンドは `env.php` に機密設定を書き込みます。

### 機密設定の管理

機密性の高い設定も `app/etc/env.php` に保存されます。

次のいずれかの方法で、機密性の高い設定を管理できます。

- 環境変数
- [`magento config:set:sensitive` コマンドを使用して、実稼動システムの `env.php` に機密性の高い設定を保存し ](../cli/set-configuration-values.md) す。

### 設定は管理者でロックされています

`config.php` または `env.php` の設定は、管理者でロックされています。つまり、管理者でこれらの設定を変更することはできません。
[`magento config:set` または `magento config:set --lock`](../cli/export-configuration.md#config-cli-config-set) コマンドを使用して、`config.php` または `env.php` ファイルの設定を変更します。

## Commerce管理者

実稼動モードの場合、管理者に次の動作が表示されます。

- 管理者でキャッシュタイプを有効または無効にすることはできません
- 以下を含め、開発者設定は使用できません（**ストア**/設定/**設定**/詳細/**開発者**）。

   - CSS、JavaScriptおよびHTMLの縮小
   - CSS とJavaScriptの結合
   - サーバーサイドまたはクライアントサイドの LESS コンパイル
   - インライン翻訳
   - 前述のように、`config.php` または `env.php` の設定はロックされ、管理者では編集できません。
   - 管理者ロケールは、デプロイされたテーマで使用される言語にのみ変更できます

     次の図は、デプロイされたロケールが 2 つのみ **示されている、管理者の** アカウント設定 **> インターフェイスロケール** リストの例を示しています。

     ![ 管理者ロケールは、デプロイされたロケールにのみ変更できます ](../../assets/configuration/split-deploy-admin-locale.png)

- Admin を使用して、どのスコープのロケール設定も変更できません。

  実稼動モードに切り替える前に、これらの変更を行うことをお勧めします。

  環境変数またはパス `general/locale/code` を指定した `config:set` CLI コマンドを使用して、ロケールを引き続き設定できます。

## Cron のインストールと削除

バージョン 2.2 では初めて、[`magento cron:install` コマンド ](../cli/configure-cron-jobs.md) を提供して cron ジョブを設定するのに役立ちます。 このコマンドは、コマンドを実行するユーザーとして crontab を設定します。

また、`magento cron:remove` コマンドを使用して crontab を削除することもできます。

## 推奨されるパイプラインデプロイメントワークフロー

次の図は、パイプラインデプロイメントを使用して設定を管理することをお勧めする方法を示しています。

![ 推奨されるパイプラインデプロイメントワークフロー ](../../assets/configuration/split-deploy-workflow.png)

### 開発システム

開発システムでは、管理者で設定を変更して、共有設定 `app/etc/config.php` とシステム固有の設定 `app/etc/env.php` を生成します。 Commerce コードと共有設定がソース管理にあることを確認し、ビルドサーバーにプッシュします。

また、開発環境に拡張機能をインストールし、Commerce コードをカスタマイズする必要もあります。

開発システム上：

1. 管理者で設定を指定します。

1. `magento app:config:dump` コマンドを使用して、設定をファイルシステムに書き込みます。

   - `app/etc/config.php` は共有設定で、すべての設定 _機密を除く_ とシステム固有の設定が含まれています。 このファイルはソース管理されている必要があります。
   - `app/etc/env.php` はシステム固有の設定で、特定のシステムに固有の設定（ホスト名やポート番号など）が含まれます。 このファイルはソース管理 _にすべきではありません_。

1. 変更したコードと共有設定をソース管理に追加します。

1. 開発時に生成された php コードと静的アセットファイルを削除するには、次のコマンドを実行します。

   ```bash
   rm -r var/view_preprocessed/*
   rm -r pub/static/*/*
   rm -r generated/*/*
   ```

アセットをクリアするコマンドを実行すると、Commerceによって作業ファイルが生成されます。

>[!WARNING]
>
>上記のアプローチに注意してください。 `generated` または `pub` フォルダー内の `.htacces` のファイルを削除すると、問題が発生する可能性があります。

### システムを構築

ビルドシステムは、コードをコンパイルして、Commerceに登録されたテーマの静的ビューファイルを生成します。 Commerce データベースへの接続は不要で、Commerce コードベースのみが必要です。

お使いのビルドシステムで、次の操作を行います。

1. ソース管理から共有設定ファイルを取り出します。
1. `magento setup:di:compile` コマンドを使用してコードをコンパイルします。
1. `magento setup:static-content:deploy -f` コマンドを使用して、静的ファイル表示ファイルを更新します。
1. ソース管理に対する更新を確認します。

>[!INFO]
>
>[ 静的ビューファイルのデプロイメント方法 ](../cli/static-view-file-strategy.md) を参照してください。

### 生産システム

実稼動システム（ライブストア）では、生成されたアセットとコードの更新をソース管理から取り込み、コマンドラインまたは環境変数を使用して、システム固有の機密構成設定を設定します。

実稼動システムで、次の操作を行います。

1. メンテナンスモードを開始します。
1. ソース管理からコードおよび設定のアップデートを取り込みます。
1. Adobe Commerceを使用している場合は、キューワーカーを停止します。
1. `magento app:config:import` コマンドを使用して、実稼動システムに設定変更を読み込みます。
1. データベーススキーマを変更したコンポーネントをインストールした場合は、`magento setup:upgrade --keep-generated` を実行して、生成された静的ファイルを保持しながらデータベーススキーマとデータを更新します。
1. システム固有の設定を行うには、`magento config:set` コマンドまたは環境変数を使用します。
1. 重要な設定を指定するには、`magento config:sensitive:set` コマンドまたは環境変数を使用します。
1. キャッシュをクリーンアップ（「_フラッシュ_」とも呼ばれます）します。
1. メンテナンスモードを終了します。

## 設定管理コマンド

設定の管理に役立つ次のコマンドを提供します。

- `config.php` および `env.php` に管理者構成設定を書き込むことがで [`magento app:config:dump`](../cli/export-configuration.md) ない（機密設定を除く）
- 実稼動システムでシステム固有の設定の値を設定で [`magento config:set`](../cli/set-configuration-values.md) ます。

  オプションの `--lock` オプションを使用して、管理画面でオプションをロックします（つまり、設定を編集不可にします）。 設定が既にロックされている場合は、`--lock` のオプションを使用して設定を変更します。

- 実稼動システムで機密設定の値を設定で [`magento config:sensitive:set`](../cli/set-configuration-values.md) ます。
- `config.php` および `env.php` から実稼動システムに設定変更を読み込むことがで [`magento app:config:import`](../cli/import-configuration.md) ません。

## 設定管理の例

この節では、設定の管理例を示して、`config.php` および `env.php` に対する変更の加え方を確認できます。

### デフォルトのロケールの変更

このセクションには、管理（**ストア**/設定/**設定**/一般/**一般**/**ロケールオプション**）を使用してデフォルトの重み付け単位を変更した場合に `config.php` に加えられた変更が表示されます。

管理者で変更を行った後、`bin/magento app:config:dump` を実行して値を `config.php` に書き込みます。 この値は、次に示すように、`locale` の下の `general` 配列に書き込ま `config.php` ます。

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

### 複数の設定の変更

この節では、次の設定変更の実行について説明します。

- Web サイト、ストア、ストア表示の追加（**ストア**/設定/**すべてのストア**）
- デフォルトのメールドメインの変更（**ストア**/設定/**設定**/顧客/**顧客設定**）
- PayPal API ユーザー名および API パスワードの設定（**ストア**/設定/**設定**/販売/**支払い方法**/**PayPal**/**PayPal 必須設定**）

管理者で変更を行った後、開発システムで `bin/magento app:config:dump` を実行します。 今度は、すべての変更が `config.php` に書き込まれるわけではありません。実際には、次のスニペットのように、web サイト、ストア、ストア表示のみがファイルに書き込まれます。

### config.php

`config.php` には次が含まれます。

- Web サイト、ストア、ストア表示の変更。
- システム固有ではない検索エンジンの設定
- 非機密の PayPal 設定
- `config.php` から除外された機密設定を通知するコメント

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

メールドメインに固有のデフォルトの設定は、`app/etc/env.php` に書き込まれます。

PayPal の設定は、どちらのファイルにも書き込まれません。これは、`bin/magento app:config:dump` コマンドでは重要な設定は書き込まれないからです。 次のコマンドを使用して、実稼動システムで PayPal 設定を指定する必要があります。

```bash
bin/magento config:sensitive:set paypal/wpp/api_username <username>
```

```bash
bin/magento config:sensitive:set paypal/wpp/api_password <password>
```
