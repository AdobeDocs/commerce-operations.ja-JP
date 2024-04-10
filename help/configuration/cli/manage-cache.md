---
title: キャッシュの管理
description: Commerce CLI を使用して、コマンド ラインからキャッシュ タイプを管理し、キャッシュ ステータスを表示する
exl-id: bbd76c00-727b-412e-a8e5-1e013a83a29a
source-git-commit: 1070291396144f866cadd5e42ebca3e77a484a9b
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# キャッシュの管理

{{file-system-owner}}

## キャッシュタイプ

Adobe Commerceのキャッシュ管理システムを使用すると、サイトのパフォーマンスを向上させることができます。 このトピックでは、Commerce アプリケーション サーバーへのアクセス権を持つシステム管理者または開発者が、コマンド ラインからキャッシュを管理する方法について説明します。

>[!NOTE]
>
>
>コマースサイト管理者は、キャッシュ管理システムツールを使用して、管理者からキャッシュを管理できます。 参照： [キャッシュ管理](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) が含まれる _管理システムガイド_.


## キャッシュステータスの表示

Commerce アプリケーションサーバーのコマンドラインから、 `cache:status` Commerce CLI コマンド。

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
>Adobe Commerceでサポートされるデフォルトのキャッシュタイプについて詳しくは、以下を参照してください [キャッシュ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#caches) が含まれる _管理システムガイド_.


## キャッシュタイプを有効または無効にする

このコマンドを使用すると、すべてのキャッシュ タイプまたは指定したキャッシュ タイプのみを有効または無効にできます。 キャッシュタイプを無効にすると、キャッシュをフラッシュしなくても変更の結果が確認できるので、開発時に便利です。ただし、キャッシュタイプを無効にすると、パフォーマンスに悪影響が出ます。

>[!INFO]
>
>バージョン 2.2 以降では、実稼動モードでコマースを実行する際に、コマンドラインを使用してのみキャッシュタイプを有効または無効にできます。 Commerce を開発者モードで実行している場合は、コマンドラインまたは手動でキャッシュタイプを有効または無効にできます。 その前に、手動で以下を行う必要があります `<magento_root>/app/etc/env.php` によって書き込み可能 [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).

クリーンアップは（以下とも呼ばれます _フラッシュ_ または _更新_）、コマンドラインまたは管理者を使用してタイプをキャッシュします。

コマンドオプション：

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

省略する場合 `[type]` すべてのキャッシュの種類を同時に有効または無効にします。 この `type` オプションは、キャッシュタイプのスペース区切りのリストです。

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

```terminal
   Changed cache status:
       db_ddl: 1 -> 0
    full_page: 1 -> 0
```

>[!INFO]
>
>キャッシュ・タイプを有効にすると、そのキャッシュ・タイプは自動的にクリアされます。

>[!INFO]
>
>バージョン 2.3.4 以降、Commerce は、取得時にすべてのシステム EAV 属性をキャッシュします。 この方法で EAV 属性をキャッシュすると、DB に対する挿入/選択リクエストの量が減少するため、パフォーマンスが向上します。 ただし、キャッシュネットワークのサイズも大きくなります。 開発者は、 `bin/magento config:set dev/caching/cache_user_defined_attributes 1` コマンド。 この操作は、での管理者からも実行できます [開発者モード](../bootstrap/application-modes.md) 設定による **ストア** > 設定 **設定** > **詳細** > **開発者** > **キャッシュ設定** > **ユーザー定義属性をキャッシュする** 対象： **はい**.

## キャッシュタイプのクリーンアップとフラッシュ

>[!NOTE]
>
>複数ページのキャッシュを同時かつ自動的に無効化できる **_なし_** これらのエンティティを編集しています。 例えば、カタログ内のいずれかの製品がどのカテゴリに割り当てられているか、または [!UICONTROL related product rule] が変更されました。

古い項目をキャッシュからパージするには、次の操作を実行します _クリーン_ または _フラッシュ_ キャッシュの種類：

- キャッシュタイプをクリーンアップすると、有効な Commerce キャッシュタイプからのみ、すべての項目が削除されます。 つまり、このオプションは、Commerce が使用するキャッシュのみをクリーンアップするので、他のプロセスやアプリケーションには影響しません。

  無効なキャッシュタイプは消去されません。

  >[!TIP]
  >
  >Magento Open SourceまたはAdobe Commerceのバージョンのアップグレード、Magento Open SourceからAdobe Commerceへのアップグレード、Adobe Commerceまたは任意のモジュール用の B2B のインストールの後は、必ずキャッシュをクリーンアップしてください。

- キャッシュタイプをフラッシュすると、キャッシュストレージがパージされ、同じストレージを使用している他のプロセスアプリケーションに影響を与える可能性があります。

キャッシュのクリーニングを既に試しても、まだ特定できない問題が発生している場合は、キャッシュタイプをフラッシュします。

コマンドの使用法：

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

ここで、 `[type]` は、キャッシュタイプのスペース区切りのリストです。 省略 `[type]` すべてのキャッシュ タイプを同時にクリーンアップまたはフラッシュします。 例えば、すべてのキャッシュタイプをフラッシュするには、と入力します。

```bash
   bin/magento cache:flush
```

結果の例：

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
   graphql_query_resolver_results
   config_webservice
   translate
```

>[!TIP]
>
>また、管理画面でキャッシュタイプのクリーンアップやフラッシュを行うこともできます。 に移動 **システム** > **ツール** > **キャッシュ管理**. **キャッシュストレージをフラッシュ** 次と同じ `bin/magento cache:flush`. **Magentoキャッシュのフラッシュ** 次と同じ `bin/magento cache:clean`.
