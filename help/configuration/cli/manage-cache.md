---
title: キャッシュの管理
description: Adobe Commerce CLI コマンドを使用してキャッシュタイプを管理し、キャッシュステータスを表示する方法を説明します。 キャッシュ管理と最適化の手法をご紹介します。
exl-id: bbd76c00-727b-412e-a8e5-1e013a83a29a
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# キャッシュの管理

{{file-system-owner}}

## キャッシュタイプ

Adobe CommerceのCMSを使用すれば、サイトのパフォーマンスを向上させることができます。 このトピックでは、Commerce アプリケーションサーバーにアクセスできるシステム管理者または開発者が、コマンドラインからキャッシュを管理する方法について説明します。

>[!NOTE]
>
>
>Commerce サイト管理者は、Cache Management System ツールを使用して、管理者からキャッシュを管理できます。 _管理者システムガイド_&#x200B;の「[&#x200B; キャッシュ管理](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management)」を参照してください。


## キャッシュステータスの表示

Commerce アプリケーションサーバーのコマンドラインで、`cache:status` Commerce CLI コマンドを使用してキャッシュのステータスを表示します。

```shell
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

サンプルは次のとおりです。

```text
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
>Adobe Commerceでサポートされているデフォルトのキャッシュタイプについて詳しくは、_管理者システムガイド_&#x200B;の[Caches](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#caches)を参照してください。


## キャッシュタイプを有効または無効にする

このコマンドを使用すると、すべてのキャッシュタイプまたは指定したキャッシュタイプのみを有効または無効にできます。 キャッシュタイプを無効にすると、キャッシュをフラッシュせずに変更の結果が表示されるため、開発中に便利です。ただし、キャッシュタイプを無効にすると、パフォーマンスに悪影響を及ぼします。

>[!INFO]
>
>バージョン 2.2以降では、実稼動モードでCommerceを実行している場合にのみ、コマンドラインを使用してキャッシュタイプを有効または無効にすることができます。 Commerceをデベロッパーモードで実行している場合は、コマンドラインまたは手動でキャッシュタイプを有効または無効にできます。 その前に、[&#x200B; ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md)が`<magento_root>/app/etc/env.php`を手動で書き込み可能にする必要があります。

コマンドラインまたは管理者を使用して、キャッシュタイプ（_フラッシュ_&#x200B;または&#x200B;_リフレッシュ_&#x200B;とも呼ばれます）をクリーニングできます。

コマンドオプション：

```shell
bin/magento cache:enable [type] ... [type]
```

```shell
bin/magento cache:disable [type] ... [type]
```

`[type]`を省略すると、すべてのキャッシュタイプを同時に有効または無効にできます。 `type` オプションは、スペース区切りのキャッシュタイプのリストです。

<!-- `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md#bootstrap-parameters) and values. -->

キャッシュタイプとそのステータスを一覧表示するには、次の手順を実行します。

```shell
bin/magento cache:status
```

例えば、フルページキャッシュとDDL キャッシュを無効にするには、次のようにします。

```shell
bin/magento cache:disable db_ddl full_page
```

結果の例：

```text
   Changed cache status:
       db_ddl: 1 -> 0
    full_page: 1 -> 0
```

>[!INFO]
>
>キャッシュタイプを有効にすると、そのキャッシュタイプは自動的にクリアされます。

>[!INFO]
>
>バージョン 2.3.4の時点では、Commerceは取得したシステム EAV属性をすべてキャッシュします。 この方法でEAV属性をキャッシュすると、DBへの挿入/選択リクエストの量が減少するため、パフォーマンスが向上します。 ただし、キャッシュネットワークのサイズも大きくなります。 開発者は、`bin/magento config:set dev/caching/cache_user_defined_attributes 1` コマンドを実行して、カスタム EAV属性をキャッシュできます。 これは、**ストア** >設定&#x200B;**設定** > **詳細** > **開発者** > **キャッシュ設定** > **ユーザー定義属性**&#x200B;から&#x200B;**はい**&#x200B;に設定することで、[開発者モード &#x200B;](../bootstrap/application-modes.md)の管理者から実行することもできます。

## キャッシュの種類のクリーニングとフラッシュ

>[!NOTE]
>
>複数のページキャッシュは同時に無効化でき、これらのエンティティを&#x200B;_&#x200B;**個の編集なしで自動的に**&#x200B;_&#x200B;無効化できます。 例えば、カタログ内の任意の商品が任意のカテゴリに割り当てられている場合、または[!UICONTROL related product rule]が変更された場合などです。

古い項目をキャッシュからパージするには、_clean_&#x200B;または&#x200B;_flush_&#x200B;のキャッシュタイプを実行できます。

- キャッシュタイプをクリーニングすると、有効なCommerce キャッシュタイプのみからすべての項目が削除されます。 つまり、このオプションは、Commerceが使用するキャッシュのみをクリーンアップするため、他のプロセスやアプリケーションには影響しません。

  無効なキャッシュタイプはクリーニングされません。

  >[!TIP]
  >
  >Adobe Commerceのバージョンのアップグレード、Magento Open SourceからAdobe Commerceへのアップグレード、またはAdobe Commerceまたは任意のモジュール用のB2Bのインストール後は、常にキャッシュをクリーニングします。

- キャッシュタイプをフラッシュすると、キャッシュストレージが消去され、同じストレージを使用している他のプロセスアプリケーションに影響を与える可能性があります。

キャッシュのクリーニングを既に試していて、まだ分離できない問題がある場合は、キャッシュの種類をフラッシュします。

コマンドの使用状況：

```shell
   bin/magento cache:clean [type] ... [type]
```

```shell
   bin/magento cache:flush [type] ... [type]
```

ここで、`[type]`はスペースで区切られたキャッシュタイプのリストです。 `[type]`を省略すると、すべてのキャッシュタイプを同時に消去またはフラッシュします。 例えば、すべてのキャッシュタイプをフラッシュするには、と入力します

```shell
   bin/magento cache:flush
```

結果の例：

```text
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
>管理画面でキャッシュタイプをクリーニングおよびフラッシュすることもできます。 **システム** > **ツール** > **キャッシュ管理**&#x200B;に移動します。 **フラッシュキャッシュストレージ**&#x200B;は`bin/magento cache:flush`と同等です。 **フラッシュ Magento キャッシュ**&#x200B;は`bin/magento cache:clean`と同等です。
