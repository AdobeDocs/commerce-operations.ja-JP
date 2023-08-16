---
title: モジュール出力を無効にする
description: モジュール出力を無効にする方法を説明します。
exl-id: af556bf5-8454-4d65-8ac8-4a64c108f092
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# モジュール出力を無効にする

デフォルトでは、モジュール出力をビューに書き込めるように、すべてのモジュールが設定されています。 出力をオフにすると、ハード依存関係が原因で無効にできないモジュールを基本的に無効にする方法が提供されます。

例えば、 `Customer` モジュールは次の値に依存します。 `Review` モジュール、つまり `Review` モジュールを無効にすることはできません。 ただし、顧客にレビューを提供したくない場合は、 `Review` モジュール。

>[!INFO]
>
>マーチャントが以前のリリースで管理者を使用してモジュール出力を無効にした場合は、これらの設定を移行するようにシステムを手動で設定する必要があります。

出力無効化は、次のクラスで実行されます。

- [\Magento\Framework\View\Element\AbstractBlock:toHtml](https://github.com/magento/magento2/blob/36097739bbb0b8939ad9a2a0dadee64318153dca/lib/internal/Magento/Framework/View/Element/AbstractBlock.php#L651)
- [\Magento\Backend\Block\Template::isOutputEnabled](https://github.com/magento/magento2/blob/0c786907ffe03d0e2990612eec16ee58b00379c5/app/code/Magento/Backend/Block/Template.php#L96)

>[!WARNING]
>
>モジュール出力を無効にしても、モジュールは無効にはなりません。 モジュールは有効なままで機能しますが、フロントエンドまたはバックエンドでは、ブロック、ページ、フィールドはレンダリングされません。

## パイプラインデプロイメントでのモジュール出力の無効化

コマースアプリケーションの複数のインスタンスを使用して、パイプラインデプロイメントまたはその他のデプロイメントでのモジュール出力を無効にするには、次の手順を実行します。

1. を編集します。 `Backend` モジュールの `config.xml` ファイル。
1. 設定の変更を書き出します。

### を編集します。 `Backend` モジュール `config.xml` ファイル

1. オリジナルをアーカイブ `config.xml` ファイル。
1. 次のような行を `<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml` ファイルの、直下 `<default>` 要素：

   ```xml
   <advanced>
       <modules_disable_output>
           <Magento_Newsletter>1</Magento_Newsletter>
       </modules_disable_output>
   </advanced>
   ```

   ここでは、

   - `<modules_disable_output>` には、モジュールのリストが含まれています。
   - `<Magento_Newsletter></Magento_Newsletter>` 出力を無効にするモジュールを指定します。
   - `1` は、 `Magento_Newsletter` モジュール。

この設定の結果、お客様は新規登録してニュースレターを受け取ることができなくなります。

### 設定の変更を書き出します。

次のコマンドを実行して、設定の変更を書き出します。

```bash
bin/magento app:config:dump
```

結果は `<Magento_install_dir>/app/etc/config.php` ファイル。

次に、キャッシュをクリアして新しい設定を有効にします。

```bash
bin/magento cache:clean config
```

詳しくは、 [設定の書き出し](../cli/export-configuration.md).

## シンプルなデプロイメントでモジュール出力を無効にする

変更を配布する必要がないので、Commerce の単一のインスタンスでモジュール出力を無効にする手順が簡単になります。

1. オリジナルをアーカイブ `<Magento_install_dir>/app/etc/config.php` ファイル。
1. 次を追加： `advanced` および `modules_disable_output` セクションから `config.php` ファイル（存在しない場合）:

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

この例では、 `Magento_Review` モジュールが無効になっており、お客様は製品を確認できなくなりました。
出力を再度有効にするには、値をに設定します。 `0`.
