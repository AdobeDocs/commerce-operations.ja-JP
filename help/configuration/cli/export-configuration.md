---
title: 構成設定のエクスポート
description: Adobe Commerce設定を設定ファイル（設定ダンプとも呼ばれます）に書き出します。
exl-id: db680f5e-547a-48f3-b017-d77b8cb07bfd
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# 構成設定のエクスポート

Commerce 2.2 以降 [ パイプラインデプロイメントモデル ](../deployment/technical-details.md) では、システム間で一貫した設定を維持できます。 開発システムの管理者で設定を指定した後、次のコマンドを使用してその設定を設定ファイルに書き出します。

```bash
bin/magento app:config:dump {config-types}
```

_config_types_ は、ダンプする設定タイプのスペース区切りリストです。 使用可能なタイプには、`scopes`、`system`、`themes`、`i18n` などがあります。 設定タイプが指定されていない場合、コマンドはすべてのシステム設定情報をダンプします。

次の例では、範囲とテーマのみをダンプします。

```bash
bin/magento app:config:dump scopes themes
```

コマンドを実行すると、次の設定ファイルが更新されます。

- `app/etc/config.php`

  これは、すべてのCommerce インスタンス用の共有設定ファイルです。
これをソースコントロールに含めて、開発、ビルド、実稼動の各システム間で共有できるようにします。

  [config.php リファレンス ](../reference/config-reference-configphp.md) を参照してください。

- `app/etc/env.php`

  これは環境固有の設定ファイルです。
個々の環境向けの機密性の高いシステム固有の設定が含まれています。

  このファイルをソース管理に含めないでくださ __。

  [env.php リファレンス ](../reference/config-reference-envphp.md) を参照してください。

## 機密またはシステム固有の設定

`env.php` に書き込まれた機密設定を設定するには、[`bin/magento config:sensitive:set`](set-configuration-values.md#set-values) コマンドを使用します。

設定値は、モジュールの [`di.xml`](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings/#how-to-specify-values-as-sensitive-or-system-specific) ファイル内の [`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) を参照することで、機密またはシステム固有として指定されます。

`config_types` を使用する際に追加のシステム設定を書き出すには、[`bin/magento config:set`](set-configuration-values.md#set-values) コマンドの使用を検討してください。
