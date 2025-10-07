---
title: キャッシュの管理
description: Adobe Commerceの CLI コマンドを使用してキャッシュタイプを管理し、キャッシュステータスを表示する方法について説明します。 キャッシュの管理と最適化の手法について説明します。
exl-id: bbd76c00-727b-412e-a8e5-1e013a83a29a
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---

# キャッシュの管理

{{file-system-owner}}

## キャッシュタイプ

Adobe Commerceのキャッシュ管理システムを使用すると、サイトのパフォーマンスを向上させることができます。 ここでは、Commerce アプリケーションサーバーへのアクセス権を持つシステム管理者または開発者がコマンドラインからキャッシュを管理する方法について説明します。

>[!NOTE]
>
>
>Commerce サイト管理者は、キャッシュ管理システムツールを使用して、管理者からキャッシュを管理できます。 [&#x200B; 管理システムガイド &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-admin/systems/tools/cache-management) の _キャッシュ管理_ を参照してください。


## キャッシュステータスの表示

Commerce アプリケーションサーバーのコマンドラインから、`cache:status` Commerce CLI コマンドを使用してキャッシュのステータスを表示します。

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

次に例を示します。

```
Current status:
                        config: 1
                        layout: 1
                    block_html: 1
                   collections: 1
                    reflection: 1
                        db_ddl: 1
               compiled_config: 1
             webhooks_response: 1
                           eav: 1
         customer_notification: 1
 graphql_query_resolver_result: 1
            config_integration: 1
        config_integration_api: 1
                  admin_ui_sdk: 1
                     full_page: 1
                   target_rule: 1
             config_webservice: 1
                     translate: 1
```

>[!TIP]
>
>Adobe Commerceでサポートされるデフォルトのキャッシュタイプについて詳しくは、『 [&#x200B; 管理システムガイド &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-admin/systems/tools/cache-management#caches) 』の _キャッシュ_ を参照してください。


## キャッシュタイプを有効または無効にする

このコマンドを使用すると、すべてのキャッシュ タイプまたは指定したキャッシュ タイプのみを有効または無効にできます。 キャッシュタイプを無効にすると、キャッシュをフラッシュしなくても変更の結果が確認できるので、開発時に便利です。ただし、キャッシュタイプを無効にすると、パフォーマンスに悪影響が出ます。

>[!INFO]
>
>バージョン 2.2 以降では、Commerceを実稼働モードで実行している場合に、コマンドラインを使用してのみキャッシュタイプを有効または無効にできます。 Commerceを開発者モードで実行している場合は、コマンドラインまたは手動でキャッシュタイプを有効または無効にできます。 その前に、`<magento_root>/app/etc/env.php` ファイルシステムの所有者 [&#x200B; によって手動で &#x200B;](../../installation/prerequisites/file-system/overview.md) を書き込み可能にする必要があります。

コマンドラインまたは Admin を使用して、キャッシュタイプをクリーンアップ（「_フラッシュ_ または _更新_ とも呼ばれます）できます。

コマンドオプション：

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

`[type]` を省略すると、すべてのキャッシュタイプが同時に有効または無効になります。 `type` のオプションは、キャッシュタイプのスペース区切りリストです。

<!-- `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md#bootstrap-parameters) and values. -->

キャッシュのタイプとそのステータスを表示するには：

```bash
bin/magento cache:status
```

例えば、フルページキャッシュと DDL キャッシュを無効にするには、次の手順を実行します。

```bash
bin/magento cache:disable db_ddl full_page
```

結果の例：

```
   Changed cache status:
       db_ddl: 1 -> 0
    full_page: 1 -> 0
```

>[!INFO]
>
>キャッシュ・タイプを有効にすると、そのキャッシュ・タイプは自動的にクリアされます。

>[!INFO]
>
>バージョン 2.3.4 以降、Commerceは、取得時にすべてのシステム EAV 属性をキャッシュします。 この方法で EAV 属性をキャッシュすると、DB に対する挿入/選択リクエストの量が減少するため、パフォーマンスが向上します。 ただし、キャッシュネットワークのサイズも大きくなります。 開発者は、`bin/magento config:set dev/caching/cache_user_defined_attributes 1` コマンドを実行して、カスタム EAV 属性をキャッシュできます。 この操作は、[&#x200B; 開発者モード &#x200B;](../bootstrap/application-modes.md) で **ストア**/設定 **設定**/**詳細**/**開発者**/**キャッシュ設定**/**ユーザー定義属性をキャッシュ** を **はい** に設定して、管理者からも実行できます。

## キャッシュタイプのクリーンアップとフラッシュ

>[!NOTE]
>
>複数のページキャッシュは、これらのエンティティを編集することなく **_同時かつ自動的に_** 無効化できます。 例えば、カタログ内のいずれかの製品が任意のカテゴリに割り当てられたときや、いずれかの [!UICONTROL related product rule] 品が変更されたとき。

古い項目をキャッシュからパージするには、次のキャッシュタイプを _クリーン_ または _フラッシュ_ します。

- キャッシュタイプをクリーンアップすると、有効なCommerce キャッシュタイプからのみ、すべての項目が削除されます。 つまり、このオプションは、Commerceが使用するキャッシュのみをクリーンアップするので、他のプロセスやアプリケーションには影響しません。

  無効なキャッシュタイプは消去されません。

  >[!TIP]
  >
  >Adobe Commerceのバージョンのアップグレード、Magento Open SourceからAdobe Commerceへのアップグレード、Adobe Commerceまたは任意のモジュール用の B2B のインストールの後は、必ずキャッシュをクリーンアップしてください。

- キャッシュタイプをフラッシュすると、キャッシュストレージがパージされ、同じストレージを使用している他のプロセスアプリケーションに影響を与える可能性があります。

キャッシュのクリーニングを既に試しても、まだ特定できない問題が発生している場合は、キャッシュタイプをフラッシュします。

コマンドの使用法：

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

`[type]` は、キャッシュタイプのスペース区切りリストです。 `[type]` を省略すると、すべてのキャッシュタイプが同時にクリーンアップまたはフラッシュされます。 例えば、すべてのキャッシュタイプをフラッシュするには、と入力します。

```bash
   bin/magento cache:flush
```

結果の例：

```
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
   graphql_query_resolver_results
   config_webservice
   translate
```

>[!TIP]
>
>また、管理画面でキャッシュタイプのクリーンアップやフラッシュを行うこともできます。 **システム**/**ツール**/**キャッシュ管理** に移動します。 **フラッシュキャッシュストレージ** は `bin/magento cache:flush` と同等です。 **Magento キャッシュをフラッシュ** は `bin/magento cache:clean` と同等です。
