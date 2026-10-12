---
title: 構成設定の書き出し
description: 設定ダンプを使用してAdobe Commerceの設定をファイルに書き出す方法について説明します。 パイプラインのデプロイメントと設定管理。
exl-id: db680f5e-547a-48f3-b017-d77b8cb07bfd
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%
---
# 構成設定の書き出し

Commerce 2.2以降[ パイプライン デプロイメントモデル ](../deployment/technical-details.md)では、システム間で一貫した設定を維持できます。 開発システムの管理者で設定を行った後、次のコマンドを使用して、これらの設定を設定ファイルに書き出します。

```shell
bin/magento app:config:dump {config-types}
```

_config_ types_は、ダンプする設定タイプのスペース区切りリストです。 使用可能なタイプは、`scopes`、`system`、`themes`、`i18n`です。 設定タイプが指定されていない場合、コマンドはすべてのシステム設定情報をダンプします。

次の例では、スコープとテーマのみをダンプします。

```shell
bin/magento app:config:dump scopes themes
```

コマンド実行の結果、次の設定ファイルが更新されます。

- `app/etc/config.php`

  これは、すべてのCommerce インスタンスの共有設定ファイルです。
  これをソース管理に含めることで、開発、ビルド、実稼動の各システム間で共有することができます。

  [config.php参照](../reference/config-reference-configphp.md)を参照してください。

- `app/etc/env.php`

  これは環境固有の設定ファイルです。
  個々の環境に対する機密性の高いシステム固有の設定が含まれています。

  このファイルをソース管理に含めるには、_しないでください_。

  [env.php参照](../reference/config-reference-envphp.md)を参照してください。

## 機密設定またはシステム固有の設定

`env.php`に書き込まれた機密設定を設定するには、[`bin/magento config:sensitive:set`](set-configuration-values.md#set-values) コマンドを使用します。

構成値は、モジュールの[`di.xml`](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings#how-to-specify-values-as-sensitive-or-system-specific) ファイルで[`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php)を参照することで、機密性の高い値またはシステム固有の値として指定されます。

`config_types`を使用する際に追加のシステム設定をエクスポートするには、[`bin/magento config:set`](set-configuration-values.md#set-values) コマンドの使用を検討してください。
