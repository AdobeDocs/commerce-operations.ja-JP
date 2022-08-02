---
title: キャッシュの管理
description: キャッシュの種類を管理し、キャッシュのステータスを表示します。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '877'
ht-degree: 0%

---


# キャッシュの管理

{{file-system-owner}}

## キャッシュタイプ

Commerce 2 には次のキャッシュタイプがあります。

| キャッシュタイプ「わかりやすい」名前 | キャッシュタイプコード名 | 説明 |
|--- |--- |--- |
| 設定 | config | Commerce は、すべてのモジュールから設定を収集し、結合し、結合結果をキャッシュに保存します。 このキャッシュには、ファイルシステムとデータベースに保存されるストア固有の設定も含まれます。 設定ファイルを変更した後に、このキャッシュタイプをクリーンアップまたはフラッシュします。 |
| レイアウト | レイアウト | コンパイル済みのページレイアウト（すべてのコンポーネントのレイアウトコンポーネント）。 レイアウトファイルを変更した後に、このキャッシュタイプを消去またはフラッシュします。 |
| ブロックHTML出力 | block_html | HTMLのページフラグメントをブロックごとに作成できます。 ビューレイヤを変更した後に、このキャッシュタイプをクリーンアップまたはフラッシュします。 |
| コレクションデータ | コレクション | データベースクエリの結果。 必要に応じて、Commerce はこのキャッシュを自動的にクリーンアップしますが、サードパーティの開発者は任意のデータをキャッシュの任意のセグメントに配置できます。 カスタムモジュールがロジックを使用して Commerce がクリーンアップできないキャッシュエントリが発生する場合は、このキャッシュタイプをクリーンアップまたはフラッシュします。 |
| DDL | db_ddl | データベーススキーマ。 必要に応じて、Commerce はこのキャッシュを自動的にクリーンアップしますが、サードパーティの開発者は任意のデータをキャッシュの任意のセグメントに配置できます。 データベーススキーマにカスタムの変更を加えた後、このキャッシュタイプをクリーンアップまたはフラッシュします。 （つまり、Commerce が自身で作成しない更新です）。 データベーススキーマを自動的に更新する方法の 1 つは、 `magento setup:db-schema:upgrade` コマンドを使用します。 |
| コンパイル済み設定 | compiled_config | コンパイル設定 |
| エンティティ属性値 (EAV) | eav | EAV 属性に関連するメタデータ（例えば、ストアラベル、関連する PHP コードへのリンク、属性レンダリング、検索設定など）。 通常、このキャッシュタイプをクリーンアップまたはフラッシュする必要はありません。 |
| ページキャッシュ | full_page | 生成されたHTMLページ。 必要に応じて、Commerce はこのキャッシュを自動的にクリーンアップしますが、サードパーティの開発者は任意のデータをキャッシュの任意のセグメントに配置できます。 HTML出力に影響するコードレベルを変更した後、このキャッシュタイプをクリーンアップまたはフラッシュします。 キャッシュのパフォーマンスが大幅に向上するので、このキャッシュを有効にしておくことをHTMLしてください。 |
| 反射 | 反射 | Webapi モジュールと顧客モジュールの依存関係を削除します。 |
| 翻訳 | 翻訳 | すべてのモジュールの翻訳をマージした後、マージャーキャッシュが消去されます。 |
| 統合の設定 | config_integration | コンパイル済みの統合。 統合を変更または追加した後に、このキャッシュをクリーンアップまたはフラッシュします。 |
| 統合 API の設定 | config_integration_api | ストアの統合のコンパイル済み統合 API 設定。 |
| Web サービスの設定 | config_webservice | Web API 構造のキャッシュ |
| 顧客通知 | customer_notification | ユーザーインターフェイスに表示される一時的な通知。 |

## キャッシュのステータスの表示

キャッシュのステータスを表示するには、

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

次に例を示します。

```terminal
Current status:
                        config: 1
                        layout: 1
                    block_html: 1
                   collections: 1
                    reflection: 1
                        db_ddl: 1
               compiled_config: 1
                           eav: 1
         customer_notification: 1
                     full_page: 1
            config_integration: 1
        config_integration_api: 1
                   target_rule: 1
             config_webservice: 1
                     translate: 1
```

## キャッシュタイプの有効化または無効化

このコマンドを使用すると、すべてのキャッシュタイプまたは指定したキャッシュタイプのみを有効または無効にできます。 キャッシュタイプを無効化すると、変更結果がキャッシュをフラッシュしなくても表示されるので、開発時に役立ちます。ただし、キャッシュタイプを無効にすると、パフォーマンスに悪影響を与えます。

>[!INFO]
>
>バージョン 2.2 以降では、実稼働モードでのコマースの実行中に、コマンドラインを使用してのみキャッシュタイプを有効または無効にできます。 コマースを開発者モードで実行している場合は、コマンドラインを使用して、または手動でキャッシュタイプを有効または無効にできます。 その前に、手動で `<magento_root>/app/etc/env.php` 書き込み可能な [ファイルシステム所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-system-perms.html).

クリーンアップ ( _フラッシュ_ または _更新_) キャッシュタイプを作成する場合は、コマンドラインまたは管理者を使用します。

コマンドオプション：

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

省略する場合 `[type]` すべてのキャッシュタイプを同時に有効または無効にします。 この `type` オプションは、スペースで区切られたキャッシュタイプのリストです。

<!-- `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md#bootstrap-parameters) and values. -->

キャッシュのタイプとステータスをリストするには：

```bash
bin/magento cache:status
```

例えば、ページ全体のキャッシュと DDL キャッシュを無効にするには、次のようにします。

```bash
bin/magento cache:disable db_ddl full_page
```

サンプル結果：

```terminal
   Changed cache status:
       db_ddl: 1 -> 0
    full_page: 1 -> 0
```

>[!INFO]
>
>キャッシュタイプを有効にすると、そのキャッシュタイプが自動的にクリアされます。

>[!INFO]
>
>バージョン 2.3.4 以降、Commerce はすべてのシステム EAV 属性を取得時にキャッシュします。 この方法で EAV 属性をキャッシュすると、DB への挿入/選択要求の量が少なくなるので、パフォーマンスが向上します。 ただし、キャッシュのネットワークサイズも増加します。 開発者は、 `bin/magento config:set dev/caching/cache_user_defined_attributes 1` コマンドを使用します。 これは、 [開発者モード](../bootstrap/application-modes.md) 設定によって **ストア** /設定 **設定** > **詳細** > **開発者** > **キャッシュ設定** > **ユーザー定義属性をキャッシュ** から **はい**.

## キャッシュタイプのクリーンアップとフラッシュ

キャッシュから古い項目をパージするには、次の手順を実行します。 _清潔な_ または _フラッシュ_ キャッシュタイプ：

- キャッシュタイプをクリーニングすると、有効なコマースキャッシュタイプのみからすべての項目が削除されます。 つまり、このオプションは、Commerce が使用するキャッシュのみをクリーンアップするので、他のプロセスやアプリケーションには影響しません。

   無効なキャッシュタイプはクリーンアップされません。

   >[!TIP]
   >
   >Magento Open SourceまたはAdobe Commerceのバージョンをアップグレードした後、Magento Open SourceからAdobe Commerceにアップグレードした後、またはAdobe Commerceまたは任意のモジュール用に B2B をインストールした後は、常にキャッシュをクリーンアップします。

- キャッシュタイプをフラッシュすると、キャッシュストレージがパージされます。同じストレージを使用している他のプロセスアプリケーションに影響を与える可能性があります。

既にキャッシュのクリーニングを試みていて、分離できない問題が解決しない場合は、キャッシュタイプをフラッシュします。

コマンドの使用：

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

ここで、 `[type]` は、スペースで区切られたキャッシュタイプのリストです。 省略 `[type]` すべてのキャッシュタイプを同時にクリーンまたはフラッシュします。 例えば、すべてのキャッシュタイプをフラッシュするには、次のように入力します。

```bash
   bin/magento cache:flush
```

サンプル結果：

```terminal
   Flushed cache types:
   config
   layout
   block_html
   collections
   reflection
   db_ddl
   compiled_config
   eav
   customer_notification
   config_integration
   config_integration_api
   full_page
   config_webservice
   translate
```

>[!TIP]
>
>また、管理者でキャッシュタイプをクリーンアップし、フラッシュすることもできます。 に移動します。 **システム** > **ツール** > **キャッシュ管理**. **キャッシュストレージをフラッシュ** はと同じです。 `bin/magento cache:flush`. **フラッシュMagentoキャッシュ** はと同じです。 `bin/magento cache:clean`.
