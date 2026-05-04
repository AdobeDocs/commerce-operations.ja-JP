---
title: モジュール出力を無効にする
description: 依存関係を削除せずにAdobe Commerceでモジュール出力を無効にする方法を説明します。 設定手順とユースケースをご紹介します。
exl-id: af556bf5-8454-4d65-8ac8-4a64c108f092
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# モジュール出力を無効にする

デフォルトでは、すべてのモジュールは、モジュール出力がビューに書き込まれるように設定されています。 出力をオフにすると、ハード依存関係によって無効にできないモジュールを実質的に無効にすることができます。

例えば、`Customer` モジュールは`Review` モジュールに依存しているため、`Review` モジュールを無効にすることはできません。 ただし、お客様がレビューを提供しない場合は、`Review` モジュールの出力をオフにすることができます。

>[!INFO]
>
>以前のリリースで管理者を使用してモジュール出力を無効にした場合、これらの設定を移行するようにシステムを手動で設定する必要があります。

出力の無効化は、次のクラスで実行されます。

- [\Magento\Framework\View\Element\AbstractBlock::toHtml](https://github.com/magento/magento2/blob/36097739bbb0b8939ad9a2a0dadee64318153dca/lib/internal/Magento/Framework/View/Element/AbstractBlock.php#L651)
- [\Magento\Backend\Block\Template::isOutputEnabled](https://github.com/magento/magento2/blob/0c786907ffe03d0e2990612eec16ee58b00379c5/app/code/Magento/Backend/Block/Template.php#L96)

>[!WARNING]
>
>モジュール出力を無効にしても、モジュールは無効になりません。 モジュールは引き続き有効で動作しますが、フロントエンドまたはバックエンドではブロック、ページ、フィールドはレンダリングされません。

## パイプラインデプロイメントでのモジュール出力の無効化

パイプラインのデプロイメントまたはその他のデプロイメントで、Commerce アプリケーションの複数のインスタンスを使用してモジュール出力を無効にするには：

1. `Backend` モジュールの`config.xml` ファイルを編集します。
1. 設定の変更を書き出します。

### `Backend` モジュール `config.xml` ファイルを編集

1. 元の`config.xml` ファイルをアーカイブします。
1. `<default>`要素の直下にある`<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml` ファイルに、次のような行を追加します。

   ```xml
   <advanced>
       <modules_disable_output>
           <Magento_Newsletter>1</Magento_Newsletter>
       </modules_disable_output>
   </advanced>
   ```

   こちら：

   - `<modules_disable_output>`にはモジュールのリストが含まれています。
   - `<Magento_Newsletter></Magento_Newsletter>`は、出力を無効にするモジュールを指定します。
   - `1`は、`Magento_Newsletter` モジュールの出力を無効にするフラグです。

この設定のサンプル結果として、お客様はニュースレターの受信に登録できなくなります。

### 設定の変更を書き出す

次のコマンドを実行して、設定の変更を書き出します。

```shell
bin/magento app:config:dump
```

結果は`<Magento_install_dir>/app/etc/config.php` ファイルに書き込まれます。

次に、キャッシュをクリアして、新しい設定を有効にします。

```shell
bin/magento cache:clean config
```

[設定のエクスポート ](../cli/export-configuration.md)を参照してください。

## シンプルなデプロイメントでモジュール出力を無効にする

Commerceの1つのインスタンスでモジュール出力を無効にする手順は、変更を配布する必要がないため簡単です。

1. 元の`<Magento_install_dir>/app/etc/config.php` ファイルをアーカイブします。
1. `advanced`と`modules_disable_output` セクションを`config.php` ファイルに追加します（存在しない場合）。

   ```php
   'system' =>
     array (
       'websites' =>
       array (
         'base' =>
         array (
           'advanced' =>
           array (
             'modules_disable_output' =>
             array (
               'Magento_Review' => '1',
             ),
           ),
         ),
       ),
     ),
   ```

この例では、`Magento_Review` モジュールの出力が無効になっており、お客様は製品をレビューできなくなります。

### モジュール出力を再度有効にする

出力を再度有効にするには、モジュールの値を`0`に設定するか、`config.php` ファイルから行/モジュールを削除します。
