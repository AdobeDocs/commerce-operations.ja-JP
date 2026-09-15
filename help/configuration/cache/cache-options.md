---
title: キャッシュバックエンドオプションとストレージリファレンス
description: ファイルシステム、Redis、Valkey、データベースストレージなど、Adobe Commerceのキャッシュバックエンドオプションについて説明します。 Zend ベース（RemoteSynchronizedCache）およびSymfony Cache オプションを見つけます。
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
badgePaas: label="オンプレミス" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce オンプレミス プロジェクトにのみ適用されます。"
autotag-review: '2026-06-22T18:37:32.504Z'
TQID: 'https://experienceleague.adobe.com/m7eUBNrt8UF43iJq9Tpl0Y1WcmR-dlt7Z4PoHvXVNnA'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 23f63c896760992da9b0d30b756a37de2117f6b8
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%
---
# キャッシュバックエンドオプションとストレージリファレンス

>[!NOTE]
>
>このページでは、オンプレミス `app/etc/env.php`の設定について説明します。
>
>[!DNL Adobe Commerce on Cloud] プロジェクトの場合、`ece-tools` パッケージは、`.magento.env.yaml`のデプロイ変数設定に基づいて、デプロイ時に結果の`app/etc/env.php`設定を生成します。 `env.php` ファイルは編集できません。  ValkeyおよびRedis サービス設定](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration)および[変数のデプロイ ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy)に関する[ ベストプラクティスを参照してください。

Commerce アプリケーションでは、低レベルのキャッシュフロントエンドとバックエンドを使用して、キャッシュストレージへのアクセスを提供します。 Commerceは、複数のキャッシングバックエンドと戦略をサポートしており、それぞれ異なるユースケースに適しています。 このページでは、使用可能なバックエンドとその違いについて説明します。

>[!NOTE]
>
>[Varnish](config-varnish-install.md)は、オンプレミスのデプロイメントのHTTP レベルでフルページ キャッシュを処理します。 [Fastly サービス ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly)は、クラウドのデプロイメントに対して処理します。 どちらのソリューションも低レベルのキャッシュバックエンドを使用しません。

## バックエンドキャッシュオプション

次の表に、使用可能なバックエンドキャッシュの概要を示します。

| バックエンド | 説明 | 設定ガイド |
| ------- | ----------- | ------------------- |
| ファイルシステム | デフォルト： キャッシュデータを`var/cache/`の下のファイルに保存します。 設定は必要ありません。 | 該当なし |
| Redis | 高性能なキャッシュを実現するインメモリデータストア。 | [ デフォルトのキャッシュにRedisを使用](redis-pg-cache.md) |
| バルキー | オープンソースのRedis互換の代替手段。 | [既定のキャッシュにValkeyを使用](valkey-pg-cache.md) |
| データベース | データベースに裏打ちされたカスタムキャッシュエンジン | [ カスタムキャッシュエンジンの作成](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching){target="_blank"} （Adobe Developer ドキュメント） |

>[!IMPORTANT]
>
>Redis キャッシュは、Adobe Commerce 2.4.9、または2.4.5-p16、2.4.6-p14、2.4.7-p9、および2.4.8-p4以降のパッチリリースではサポートされていません。 これらのバージョンのいずれかにアップグレードする場合は、Valkeyを設定し、キャッシュ設定を更新して使用します。 [!DNL Adobe Commerce on-premises]については、[Valkeyの設定](config-valkey.md)を参照してください。

## バックエンドおよびL2のキャッシュ実装 {#implementation-approaches}

Commerceは、ダイレクトキャッシュのバックエンドとL2 キャッシュをサポートしています。 ダイレクトバックエンドでは、キャッシュストレージが選択されます。 L2 キャッシュでは、リモートストレージの前にローカルキャッシュレイヤーが追加されます。

### ダイレクトキャッシュバックエンド

次の表は、`<Commerce-install-dir>/app/etc/env.php`のキャッシュバックエンド設定値をまとめたものです。 L2 キャッシュを有効にしません。

| Commerce版 | バックエンド | 設定値 |
| ---------------- | ------- | -------------------- |
| 2.4.8以前（サポートされている場合） | ファイル | デフォルト： 設定は必要ありません |
| 2.4.8以前（サポートされている場合） | Redis | `Magento\Framework\Cache\Backend\Redis` |
| 2.4.8以前（サポートされている場合） | バルキー | `Magento\Framework\Cache\Backend\Valkey` |
| 2.4.9以降、およびサポートされているバックポート | ファイル | `file` |
| 2.4.9以降、およびサポートされているバックポート | バルキー | `valkey` |

正確なパッチレベルのサポートについては、[必要システム構成](../../installation/system-requirements.md)を参照してください。

>[!TAB Zend ベースのキャッシュ （2.4.8以前） ]

#### バックエンド例

オンプレミスのデプロイメントの場合、次の例では、`<Commerce-install-dir>/app/etc/env.php`でダイレクトキャッシュバックエンドを設定します。 L2 キャッシュを有効にしません。 デプロイメント中に結果の`app/etc/env.php`設定を生成するために`ece-tools` パッケージを使用する[!DNL Adobe Commerce on Cloud] デプロイメントでは、これらの例を使用しないでください。

>[!BEGINTABS]

>[!TAB Redis]

Redisがサポートされているリリースでのみ、完全なRedis クラス名を使用します。

```php?start_inline=1
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379',
            ],
        ],
    ],
],
```

>[!TAB Valkey]

```php?start_inline=1
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379',
            ],
        ],
    ],
],
```

>[!ENDTABS]

## L2 キャッシュ

L2 （2 レベル）キャッシュでは、各web ノードのローカルキャッシュ層が共有リモートキャッシュストレージの前に追加され、Commerceとリモートキャッシュ間のネットワークトラフィックが削減されます。 実装オプション、バージョンサポート、および設定手順については、[L2 キャッシュ設定](level-two-cache.md)を参照してください。

クラウドプロジェクトの場合、[ デプロイ変数](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy){target="_blank"}で説明されているデプロイメント変数を使用してL2 キャッシュを設定します。

- [デフォルトのキャッシュにRedisを使用](redis-pg-cache.md)
- [デフォルトのキャッシュにValkeyを使用](valkey-pg-cache.md)
- [L2 キャッシュ設定](level-two-cache.md)
