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

Commerce 2.2 以降 [パイプラインデプロイメントモデル](../deployment/technical-details.md)を使用すると、システム間で一貫した設定を維持できます。 開発システムの管理者で設定を指定した後、次のコマンドを使用してその設定を設定ファイルに書き出します。

```bash
bin/magento app:config:dump {config-types}
```

_config_types_ は、ダンプする設定タイプのスペース区切りリストです。 利用可能なタイプは次のとおりです `scopes`, `system`, `themes`、および `i18n`. 設定タイプが指定されていない場合、コマンドはすべてのシステム設定情報をダンプします。

次の例では、範囲とテーマのみをダンプします。

```bash
bin/magento app:config:dump scopes themes
```

コマンドを実行すると、次の設定ファイルが更新されます。

- `app/etc/config.php`

  これは、すべてのCommerce インスタンス用の共有設定ファイルです。
これをソースコントロールに含めて、開発、ビルド、実稼動の各システム間で共有できるようにします。

  参照： [config.php リファレンス](../reference/config-reference-configphp.md).

- `app/etc/env.php`

  これは環境固有の設定ファイルです。
個々の環境向けの機密性の高いシステム固有の設定が含まれています。

  実行 _ではない_ このファイルをソース管理に含めます。

  参照： [env.php リファレンス](../reference/config-reference-envphp.md).

## 機密またはシステム固有の設定

に書き込まれた機密設定を設定するには `env.php`、を使用します [`bin/magento config:sensitive:set`](set-configuration-values.md#set-values) コマンド。

設定値は、を参照して、機密またはシステム固有のいずれかで指定されます [`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) モジュールの [`di.xml`](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings/#how-to-specify-values-as-sensitive-or-system-specific) ファイル。

使用時に追加のシステム設定をエクスポートするには `config_types`を使用する場合は、の使用を検討してください。 [`bin/magento config:set`](set-configuration-values.md#set-values) コマンド。
