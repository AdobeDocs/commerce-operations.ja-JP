---
title: キャッシュバックエンドオプションとストレージリファレンス
description: ファイルシステム、Redis、Valkey、データベースストレージなど、Adobe Commerceのキャッシュバックエンドオプションについて説明します。 レガシーかつモダンなアプローチをご紹介します。
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
badgePaas: label="オンプレミス" type="Informative" url="https://experienceleague.adobe.com/ja/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce オンプレミス プロジェクトにのみ適用されます。"
autotag-review: '2026-06-22T18:37:32.504Z'
TQID: 'https://experienceleague.adobe.com/m7eUBNrt8UF43iJq9Tpl0Y1WcmR-dlt7Z4PoHvXVNnA'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 8c5dc151b00fd73e939c32fdc083fb0e8fc41dc8
workflow-type: tm+mt
source-wordcount: 761
ht-degree: 0%

---

# キャッシュバックエンドオプションとストレージリファレンス

>[!NOTE]
>
>このページでは、オンプレミス `app/etc/env.php`の設定について説明します。
>
>[!DNL Adobe Commerce on Cloud] プロジェクトの場合、`ece-tools` パッケージは、`.magento.env.yaml`のデプロイ変数設定に基づいて、デプロイ時に結果の`app/etc/env.php`設定を生成します。 `env.php` ファイルは編集できません。  ValkeyおよびRedis サービス設定[&#128279;](https://experienceleague.adobe.com/ja/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration)および[変数のデプロイ &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy)に関する ベストプラクティスを参照してください。

Commerce アプリケーションでは、低レベルのキャッシュフロントエンドとバックエンドを使用して、キャッシュストレージへのアクセスを提供します。 Commerceは、複数のキャッシングバックエンドと戦略をサポートしており、それぞれ異なるユースケースに適しています。 このページでは、使用可能なバックエンドとその違いについて説明します。

>[!NOTE]
>
>[Varnish](config-varnish-install.md)は、オンプレミスのデプロイメントのHTTP レベルでフルページ キャッシュを処理します。 [Fastly サービス &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/cdn/fastly)は、クラウドのデプロイメントに対して処理します。 どちらのソリューションも低レベルのキャッシュバックエンドを使用しません。

## バックエンドキャッシュオプション

次の表に、使用可能なバックエンドキャッシュの概要を示します。

| バックエンド | 説明 | 設定ガイド |
| ------- | ----------- | ------------------- |
| ファイルシステム | デフォルト： キャッシュデータを`var/cache/`の下のファイルに保存します。 設定は必要ありません。 | 該当なし |
| Redis | 高性能なキャッシュを実現するインメモリデータストア。 | [&#x200B; デフォルトのキャッシュにRedisを使用](redis-pg-cache.md) |
| バルキー | オープンソースのRedis互換の代替手段。 | [既定のキャッシュにValkeyを使用](valkey-pg-cache.md) |
| データベース | データベースに裏打ちされたカスタムキャッシュエンジン | [&#x200B; カスタムキャッシュエンジンの作成](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching){target="_blank"} （Adobe Developer ドキュメント） |

>[!IMPORTANT]
>
>Redis キャッシュは、Adobe Commerce 2.4.9、または2.4.5-p16、2.4.6-p14、2.4.7-p9、および2.4.8-p4以降のパッチリリースではサポートされていません。 これらのバージョンのいずれかにアップグレードする場合は、Valkeyを設定し、キャッシュ設定を更新して使用します。 [!DNL Adobe Commerce on-premises]については、[Valkeyの設定](config-valkey.md)を参照してください。

## バックエンドおよびL2のキャッシュ実装 {#implementation-approaches}

Commerceは、ダイレクトキャッシュのバックエンドとL2 キャッシュをサポートしています。 ダイレクトバックエンドでは、キャッシュストレージが選択されます。 L2 キャッシュでは、リモートストレージの前にローカルキャッシュレイヤーが追加されます。

### ダイレクトキャッシュバックエンド

次のPHPの例では、`<Commerce-install-dir>/app/etc/env.php`のキャッシュバックエンドを設定しています。 L2 キャッシュを有効にしません。

| Commerce版 | 導入 | バックエンド | 設定値 |
| ---------------- | -------------- | ------- | ------------------- |
| 2.4.8以前（サポートされている場合） | レガシー | ファイルシステム （デフォルト） | 設定は必要ありません |
| 2.4.8以前（サポートされている場合） | レガシー | Redis | `Magento\Framework\Cache\Backend\Redis` |
| 2.4.8以前（サポートされている場合） | レガシー | バルキー | `Magento\Framework\Cache\Backend\Valkey` |
| 2.4.9以降、およびサポートされているバックポート | 最新のSymfony キャッシュ | ファイルシステム （デフォルト） | `file` |
| 2.4.9以降、およびサポートされているバックポート | 最新のSymfony キャッシュ | バルキー | `valkey` |

正確なパッチレベルのサポートについては、[必要システム構成](../../installation/system-requirements.md)を参照してください。

>[!NOTE]
>
>最新の実装では`redis` タイプ名を受け入れますが、RedisはValkeyが必要な正式にサポートされているキャッシュサービスではありません。 代わりに`valkey`を使用してください。

#### 従来のZend ベースのバックエンドの例

オンプレミスのデプロイメントの場合、次の例では、`<Commerce-install-dir>/app/etc/env.php`でダイレクトキャッシュバックエンドを設定します。 L2 キャッシュを有効にしません。 デプロイメント中に結果の`app/etc/env.php`設定を生成するために`ece-tools` パッケージを使用する[!DNL Adobe Commerce on Cloud] デプロイメントでは、これらの例を使用しないでください。

>[!BEGINTABS]

>[!TAB 従来のバックエンド Redis]

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

>[!TAB 従来のバックエンド Valkey]

従来のValkey バックエンドをサポートするリリースでは、Valkey クラスの完全な名前を使用します。

```php?start_inline=1
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
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

#### 最新のSymfony Cache バックエンド

デフォルトのダイレクトバックエンドはファイルシステムです。 最新の実装でValkeyを使用するには、簡素化された`valkey` バックエンドタイプを使用します。

次の設定例は、最新のSymfony Cache実装でダイレクトデフォルトキャッシュを設定する場合の、Adobe Commerce 2.4.9以降およびValkeyがサポートされているサポート対象のバックポートに対して正しいものです。

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

>[!TIP]
>
>Symfony Cacheの実装は、igbinaryのシリアル化、圧縮、Lua スクリプト、永続接続などのオプションのパフォーマンス機能をサポートしています。 詳しくは、[&#x200B; デフォルトおよびページキャッシュのValkeyの設定](valkey-pg-cache.md)を参照してください。

### L2 キャッシュ実装

L2 （2 レベル）キャッシュでは、各web ノードのローカルキャッシュ層が共有リモートキャッシュストレージの前に追加され、Commerceとリモートキャッシュ間のネットワークトラフィックが削減されます。

| Commerce版 | L2の実装 | リモートバックエンド |
| ---------------- | ------------------ | --------------- |
| 2.4.9より前（サポートされている場合） | RemoteSynchronizedCache | RedisまたはValkey （Commerce リリースとパッチレベルのサポート行列に応じて） |
| 2.4.9以降 | symfony_l2 | バルキー |

オンプレミス設定については、[L2 キャッシュ設定](level-two-cache.md)を参照してください。

クラウドプロジェクトの場合、[&#x200B; デプロイ変数](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy){target="_blank"}で説明されているデプロイメント変数を使用してL2 キャッシュを設定します。

#### L2 キャッシュ設定

- **[!DNL Adobe Commerce on-premises]**&#x200B;設定の詳細については、[L2 キャッシュ設定](level-two-cache.md)を参照してください。

- **[!DNL Adobe Commerce on Cloud]**&#x200B;の場合、`app/etc/env.php`を直接編集するのではなく、適切なデプロイメント変数を使用してL2 キャッシュを設定します。 _Adobe Commerce on Cloud_ ドキュメントの[変数のデプロイ &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy){target="_blank"}を参照してください。
