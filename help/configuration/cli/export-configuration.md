---
title: 書き出し設定
description: Adobe Commerceの設定を設定ファイル（設定ダンプとも呼ばれます）にエクスポートします。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# 書き出し設定

Commerce 2.2 以降 [パイプラインデプロイメントモデル](../deployment/technical-details.md)を使用すると、システム間で一貫した設定を維持できます。 開発システムで管理者で設定を構成した後、次のコマンドを使用して、それらの設定を設定ファイルに書き出します。

```bash
bin/magento app:config:dump {config-types}
```

_config_types_ は、ダンプする設定タイプのスペース区切りリストです。 使用可能なタイプは次のとおりです。 `scopes`, `system`, `themes`、および `i18n`. config タイプが指定されていない場合、コマンドはすべてのシステム構成情報をダンプします。

次の例では、スコープとテーマのみをダンプします。

```bash
bin/magento app:config:dump scopes themes
```

コマンドの実行の結果、次の設定ファイルが更新されます。

- `app/etc/config.php`

   これは、すべてのコマースインスタンスの共有設定ファイルです。
これをソース管理に含めて、開発、ビルド、実稼動システム間で共有できるようにします。

   詳しくは、 [config.php リファレンス](../reference/config-reference-configphp.md).

- `app/etc/env.php`

   これは、環境固有の設定ファイルです。
個々の環境に対する機密性の高いシステム固有の設定が含まれています。

   実行 _not_ このファイルをソース管理に含めます。

   詳しくは、 [env.php リファレンス](../reference/config-reference-envphp.md).

## 機密設定またはシステム固有の設定

に書き込まれる機密設定を設定するには `env.php`、 [`bin/magento config:sensitive:set`](set-configuration-values.md#set-values) コマンドを使用します。

設定値は、 [`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) モジュールの [`di.xml`](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings/#how-to-specify-values-as-sensitive-or-system-specific) ファイル。

を使用する際に追加のシステム設定を書き出すには `config_types`を使用する場合は、 [`bin/magento config:set`](set-configuration-values.md#set-values) コマンドを使用します。
