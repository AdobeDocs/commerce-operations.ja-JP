---
title: キャッシュフロントエンドとタイプの設定
description: キャッシュフロントエンドを定義し、Adobe Commerceのキャッシュタイプに関連付ける方法について説明します。 env.phpの設定構文を確認します。
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
product_v2:
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
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
source-wordcount: '471'
ht-degree: 0%
---
# キャッシュフロントエンドとタイプの設定

キャッシュフロントエンドは、Commerce キャッシュタイプをキャッシュストレージに接続します。 複数のフロントエンドを定義し、各フロントエンドに特定のキャッシュタイプを割り当てることができます。

>[!BEGINSHADEBOX]

次の関係を使用して、キャッシュタイプがデータを保存する場所を決定します。

キャッシュタイプ→キャッシュフロントエンド→キャッシュバックエンド

>[!ENDSHADEBOX]

Commerce キャッシュ アーキテクチャの概要については、[&#x200B; キャッシュの概要と設定オプション &#x200B;](caching-overview.md)を参照してください。

>[!NOTE]
>
>クラウドインフラストラクチャ上のAdobe Commerceの場合は、クラウドガイドに記載されている[&#x200B; クラウドのデプロイメント設定](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/configure-env-yaml)を使用します。 `app/etc/env.php`を直接編集しないでください。 デプロイメントツールはこのファイルを生成し、手動での変更を上書きできます。

## デフォルトのフロントエンドを使用する

Commerceには、すべてのキャッシュタイプで使用できるデフォルトのフロントエンドが用意されています。

ほとんどの場合、カスタムフロントエンドを定義する必要はありません。 すべてのキャッシュタイプで同じバックエンドオプションとバックエンドオプションを使用できる場合は、デフォルトのフロントエンドを使用し、バックエンドを設定します。 バックエンド固有の設定については、[&#x200B; キャッシュバックエンドオプション &#x200B;](cache-options.md)を参照してください。

2.4.9より前のAdobe Commerce バージョンの場合、デフォルトのフロントエンドでは、従来のZend ベースのキャッシュ実装が使用されます。 `Magento\Framework\Cache\Core` フロントエンドは`Zend_Cache_Core`を拡張しています。 Adobe Commerce 2.4.9以降では、最新のSymfonyの実装を使用しています。 バージョン固有のガイダンスについては、[&#x200B; キャッシュバックエンドオプション &#x200B;](cache-options.md)を参照してください。

## カスタムフロントエンドを定義する

1つ以上のキャッシュタイプで、デフォルトのフロントエンドとは異なるバックエンド設定が必要な場合は、カスタムキャッシュフロントエンドを使用します。

オンプレミスのデプロイメントの場合、`app/etc/env.php`でフロントエンドを定義します。 次に、1つ以上のキャッシュタイプを割り当てます。

```php?start_inline=1
'cache' => [
    'frontend' => [
        '<frontend-id>' => [
            'backend' => '<backend-type>',
            'backend_options' => [
                // Backend-specific options
            ],
        ],
    ],
    'type' => [
        '<cache-type-id>' => [
            'frontend' => '<frontend-id>',
        ],
    ],
],
```

どこで：

- `<frontend-id>`は、`default`や`page_cache`など、フロントエンドの一意の識別子です。
- `<backend-type>`は、フロントエンドで使用されるバックエンドを識別します。 サポートされる値は、Adobe Commerce リリースと選択したバックエンドによって異なります。
- `backend_options`には、選択したバックエンドのオプションが含まれています。
- `<cache-type-id>`は、`config`、`layout`、`block_html`、`full_page`などのCommerce キャッシュの種類です。


バックエンドタイプ、サポートされているオプション、リリース固有の設定例については、[&#x200B; キャッシュバックエンドオプション &#x200B;](cache-options.md)を参照してください。

## フロントエンドへのキャッシュタイプの割り当て

`type`設定は、キャッシュタイプをフロントエンドにマッピングします。

```php?start_inline=1
'type' => [
    'full_page' => [
        'frontend' => 'page_cache',
    ],
],
```

どこで：

- `<frontend_type>` – 低レベルのフロントエンド キャッシュ タイプ。 `Zend_Cache_Core`と互換性のあるクラス名を指定してください。
省略した場合は、[Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php)が使用されます。

- `<frontend_option>`、`<frontend_option_value>` — Commerce フレームワークが作成時に自動化配列としてフロントエンドキャッシュに渡すオプションの名前と値。

- `<backend_type>` – 下位レベルのバックエンド キャッシュの種類。 次を指定できます。
  - **Symfony Cache （2.4.9以降、推奨）**: `valkey`や`file`などの簡略化された名前
  - **Zend ベース**: `Zend_Cache_Backend_Interface`を実装する`Zend_Cache_Backend`と互換性のある完全なクラス名

- `<backend_option>`、`<backend_option_value>` — Commerce フレームワークが作成時にバックエンドキャッシュに連想配列として渡すオプションの名前と値。

>[!NOTE]
>
>Zend ベースのクラス名と`valkey`や`file`などのSymfony Cache簡略名などのバックエンドの値フォーマットについては、[&#x200B; キャッシュバックエンドオプション &#x200B;](cache-options.md)を参照してください。

>[!MORELIKETHIS]
>
>- パフォーマンス最適化のための[L2 キャッシュ設定](level-two-cache.md)
>- [&#x200B; キャッシュの管理](../cli/manage-cache.md)
