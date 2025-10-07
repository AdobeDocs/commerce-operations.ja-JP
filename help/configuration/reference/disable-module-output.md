---
title: モジュール出力を無効にする
description: 依存関係を削除せずにAdobe Commerceでモジュール出力を無効にする方法を説明します。 設定手順とユースケースについて説明します。
exl-id: af556bf5-8454-4d65-8ac8-4a64c108f092
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# モジュール出力を無効にする

デフォルトでは、すべてのモジュールは、モジュール出力をビューに書き込めるように設定されています。 出力をオフにすると、ハードな依存関係のために無効にできないモジュールを基本的に無効にできます。

例えば、`Customer` モジュールは `Review` モジュールに依存するので、`Review` モジュールを無効にすることはできません。 ただし、顧客にレビューを提供させたくない場合は、`Review` モジュールからの出力をオフにできます。

>[!INFO]
>
>以前のリリースで、マーチャントが管理者を使用してモジュール出力を無効にした場合、これらの設定を移行するようにシステムを手動で設定する必要があります。

出力の無効化は、次のクラスで実行されます。

- [\Magento\Framework\View\Element\AbstractBlock::toHtml](https://github.com/magento/magento2/blob/36097739bbb0b8939ad9a2a0dadee64318153dca/lib/internal/Magento/Framework/View/Element/AbstractBlock.php#L651)
- [\Magento\Backend\Block\Template::isOutputEnabled](https://github.com/magento/magento2/blob/0c786907ffe03d0e2990612eec16ee58b00379c5/app/code/Magento/Backend/Block/Template.php#L96)

>[!WARNING]
>
>モジュール出力を無効にしても、モジュールは無効になりません。 モジュールは有効で機能したままですが、フロントエンドやバックエンドではブロック、ページ、フィールドがレンダリングされません。

## パイプラインデプロイメントでのモジュール出力の無効化

Commerce アプリケーションの複数のインスタンスを含む、パイプラインデプロイメントまたはその他のデプロイメントでモジュール出力を無効にするには：

1. `Backend` モジュールの `config.xml` ファイルを編集します。
1. 設定変更をエクスポートします。

### `Backend` module `config.xml` ファイルを編集します。

1. 元の `config.xml` ファイルをアーカイブします。
1. `<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml` 要素の直下に、`<default>` ファイルに次のような行を追加します。

   ```xml
   <advanced>
       <modules_disable_output>
           <Magento_Newsletter>1</Magento_Newsletter>
       </modules_disable_output>
   </advanced>
   ```

   ここで：

   - `<modules_disable_output>` には、モジュールのリストが含まれています。
   - `<Magento_Newsletter></Magento_Newsletter>` 出力を無効にするモジュールを指定します。
   - `1` は、`Magento_Newsletter` モジュールの出力を無効にするフラグです。

この設定のサンプル結果として、顧客はニュースレターを受信するために新規登録できなくなりました。

### 設定変更のエクスポート

次のコマンドを実行して、設定の変更を書き出します。

```bash
bin/magento app:config:dump
```

結果は `<Magento_install_dir>/app/etc/config.php` ファイルに書き込まれます。

次に、キャッシュをクリアして新しい設定を有効にします。

```bash
bin/magento cache:clean config
```

[ 設定の書き出し ](../cli/export-configuration.md) を参照してください。

## シンプルなデプロイメントでのモジュール出力の無効化

変更内容を配布する必要がないので、Commerceの 1 つのインスタンスでモジュール出力を無効にする手順が簡単です。

1. 元の `<Magento_install_dir>/app/etc/config.php` ファイルをアーカイブします。
1. `advanced` セクションと `modules_disable_output` セクションが存在しない場合は、`config.php` ファイルに追加します。

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

この例では、`Magento_Review` モジュールの出力は無効になっており、顧客は製品をレビューできなくなります。

### モジュール出力を再度有効にする

出力を再度有効にするには、モジュールの値を `0` に設定するか、`config.php` ファイルからライン/モジュールを削除します。
