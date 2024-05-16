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

このトピックでは、 [推奨ワークフロー](#recommended-workflow) パイプラインのデプロイメントの場合はおよびの仕組みを理解するのに役立つ例を提供します。

開始する前に、を確認してください [開発、ビルド、実稼動システムの前提条件](../deployment/prerequisites.md).

## 設定管理

開発システムと実稼動システムの設定を同期および維持できるようにするには、次のオーバーライドスキームを使用します。

![設定変数の値の決定方法](../../assets/configuration/override-flow-diagram.png)

次の図に示すように、設定値は次の順序で使用されます。

1. 環境変数が存在する場合は、他のすべての値を上書きします。
1. 共有設定ファイルから `env.php` および `config.php`. の値 `env.php` の値を上書き `config.php`.
1. データベースに格納されている値から。
1. これらのソースに値が存在しない場合は、デフォルト値または NULL が使用されます。

### 共有設定の管理

共有設定は、に保存されます。 `app/etc/config.php`（ソース管理にする必要があります）。

開発環境（またはクラウドインフラストラクチャー上のAdobe Commerce）の管理者で、共有設定を指定します _統合_） システムして、設定をに書き込みます `config.php` の使用 [`magento app:config:dump` コマンド](../cli/export-configuration.md).

### システム固有の設定の管理

システム固有の設定は、次の場所に保存されます。 `app/etc/env.php`、どちらを選択するか _ではない_ ソース管理されていること。

使用している開発（またはクラウドインフラストラクチャ統合のAdobe Commerce）システムの管理者でシステム固有の設定を行い、設定をに書き込みます。 `env.php` の使用 [`magento app:config:dump` コマンド](../cli/export-configuration.md).

また、このコマンドは、機密性の高い設定をに書き込みます。 `env.php`.

### 機密設定の管理

また、機密性の高い設定は、次の場所にも保存されます。 `app/etc/env.php`.

次のいずれかの方法で、機密性の高い設定を管理できます。

- 環境変数
- 機密設定をに保存します。 `env.php` を使用した実稼動システム上 [`magento config:set:sensitive` コマンド](../cli/set-configuration-values.md)

### 設定は管理者でロックされています

内の設定 `config.php` または `env.php` は管理者でロックされています。つまり、これらの設定は管理者で変更できません。
の使用 [`magento config:set` または `magento config:set --lock`](../cli/export-configuration.md#config-cli-config-set) の設定を変更するコマンド `config.php` または `env.php` ファイル。

## Commerce管理者

実稼動モードの場合、管理者に次の動作が表示されます。

- 管理者でキャッシュタイプを有効または無効にすることはできません
- 開発者設定は使用できません（**ストア** > 設定 > **設定** > 詳細 > **開発者**）に含まれます。

   - CSS、JavaScript およびHTMLの縮小
   - CSS と JavaScript の結合
   - サーバーサイドまたはクライアントサイドの LESS コンパイル
   - インライン翻訳
   - 前述のように、での設定はすべて不要です。 `config.php` または `env.php` はロックされており、管理者で編集することはできません。
   - 管理者ロケールは、デプロイされたテーマで使用される言語にのみ変更できます

     次の図は、 **アカウント設定** > **インターフェイス ロケール** 管理者のリストに、デプロイされたロケールが 2 つのみ表示されています。

     ![管理者ロケールは、デプロイされたロケールにのみ変更できます](../../assets/configuration/split-deploy-admin-locale.png)

- Admin を使用して、どのスコープのロケール設定も変更できません。

  実稼動モードに切り替える前に、これらの変更を行うことをお勧めします。

  環境変数または URL を使用してロケールを設定することもできます `config:set` パスを指定した CLI コマンド `general/locale/code`.

## Cron のインストールと削除

バージョン 2.2 では初めて、cron ジョブを設定する際に以下を提供します [`magento cron:install` コマンド](../cli/configure-cron-jobs.md). このコマンドは、コマンドを実行するユーザーとして crontab を設定します。

また、次を使用して crontab を削除できます `magento cron:remove` コマンド。

## 推奨されるパイプラインデプロイメントワークフロー

次の図は、パイプラインデプロイメントを使用して設定を管理することをお勧めする方法を示しています。

![推奨されるパイプラインデプロイメントワークフロー](../../assets/configuration/split-deploy-workflow.png)

### 開発システム

開発システムでは、管理者で設定を変更して、共有設定を生成します。 `app/etc/config.php` システム固有の設定 `app/etc/env.php`. Commerce コードと共有設定がソース管理にあることを確認し、ビルドサーバーにプッシュします。

また、開発環境に拡張機能をインストールし、Commerce コードをカスタマイズする必要もあります。

開発システム上：

1. 管理者で設定を指定します。

1. の使用 `magento app:config:dump` ファイルシステムに設定を書き込むコマンド。

   - `app/etc/config.php` は共有設定です。ここには、すべての設定が含まれます _例外_ 機密性の高いシステム固有の設定。 このファイルはソース管理されている必要があります。
   - `app/etc/env.php` はシステム固有の設定です。システム固有の設定には、特定のシステムに固有の設定（ホスト名やポート番号など）が含まれます。 このファイルは、 _ではない_ ソース管理されていること。

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
>上記のアプローチに注意してください。 の削除 `.htacces`内のファイル `generated` または `pub` フォルダーが原因で問題が発生する可能性があります。

### システムを構築

ビルドシステムは、コードをコンパイルして、Commerceに登録されたテーマの静的ビューファイルを生成します。 Commerce データベースへの接続は不要で、Commerce コードベースのみが必要です。

お使いのビルドシステムで、次の操作を行います。

1. ソース管理から共有設定ファイルを取り出します。
1. の使用 `magento setup:di:compile` コードをコンパイルするコマンド。
1. の使用 `magento setup:static-content:deploy -f` 静的ファイル表示ファイルを更新するコマンド。
1. ソース管理に対する更新を確認します。

>[!INFO]
>
>参照： [静的ビューファイルのデプロイメント戦略](../cli/static-view-file-strategy.md).

### 生産システム

実稼動システム（ライブストア）では、生成されたアセットとコードの更新をソース管理から取り込み、コマンドラインまたは環境変数を使用して、システム固有の機密構成設定を設定します。

実稼動システムで、次の操作を行います。

1. メンテナンスモードを開始します。
1. ソース管理からコードおよび設定のアップデートを取り込みます。
1. Adobe Commerceを使用している場合は、キューワーカーを停止します。
1. の使用 `magento app:config:import` 実稼動システムに設定変更を読み込むためのコマンド。
1. データベーススキーマを変更したコンポーネントをインストールした場合は、次を実行します `magento setup:upgrade --keep-generated` 生成された静的ファイルを保持して、データベーススキーマおよびデータを更新します。
1. システム固有の設定を行うには、次のいずれかを使用します `magento config:set` コマンドまたは環境変数。
1. 機密設定を設定するには、次のいずれかを使用します `magento config:sensitive:set` コマンドまたは環境変数。
1. クリーン（別名 _フラッシュ_）キャッシュです。
1. メンテナンスモードを終了します。

## 設定管理コマンド

設定の管理に役立つ次のコマンドを提供します。

- [`magento app:config:dump`](../cli/export-configuration.md) 管理設定をに書き込むには `config.php` および `env.php` （機密設定を除く）
- [`magento config:set`](../cli/set-configuration-values.md) 実稼働システムでシステム固有の設定の値を設定します。

  オプションのを使用 `--lock` 管理者でオプションをロックする（つまり、設定を編集不可にする）オプション。 設定が既にロックされている場合は、 `--lock` 設定を変更するオプション。

- [`magento config:sensitive:set`](../cli/set-configuration-values.md) 本番システム上で機密設定の値を設定します。
- [`magento app:config:import`](../cli/import-configuration.md) から設定変更を読み込むには `config.php` および `env.php` 実稼動システムに追加します。

## 設定管理の例

この節では、設定の管理例を示して、への変更の加え方を確認できます `config.php` および `env.php`.

### デフォルトのロケールの変更

この節では、に対して行われた変更を示します `config.php` 管理者（**ストア** > 設定 > **設定** > 一般 > **一般** > **ロケールオプション**）に設定します。

管理者で変更を行った後、を実行します `bin/magento app:config:dump` 値を書き込む `config.php`. 値はに書き込まれます。 `general` の下の配列 `locale` 次のコードのスニペットとして `config.php` 表示：

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

- Web サイト、ストア、ストア表示の追加（**ストア** > 設定 > **すべてのストア**）
- デフォルトのメールドメインの変更（**ストア** > 設定 > **設定** > お客様 > **顧客設定**）
- PayPal API ユーザー名と API パスワードの設定（**ストア** > 設定 > **設定** > 売上 > **支払い方法** > **PayPal** > **必須の PayPal 設定**）

管理者で変更を行った後、を実行します `bin/magento app:config:dump` 開発システム上。 今回は、すべての変更がに書き込まれるわけではありません `config.php`実際、次のスニペットのように、web サイト、ストア、ストア表示のみがファイルに書き込まれます。

### config.php

`config.php` 含む：

- Web サイト、ストア、ストア表示の変更。
- システム固有ではない検索エンジンの設定
- 非機密の PayPal 設定
- 除外された機密設定を通知するコメント `config.php`

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

メールドメインに固有のデフォルトの設定は、に書き込まれます。 `app/etc/env.php`.

PayPal の設定はどちらのファイルにも書き込まれません。その理由は `bin/magento app:config:dump` コマンドは機密性の高い設定を書き込まない。 次のコマンドを使用して、実稼動システムで PayPal 設定を指定する必要があります。

```bash
bin/magento config:sensitive:set paypal/wpp/api_username <username>
```

```bash
bin/magento config:sensitive:set paypal/wpp/api_password <password>
```
