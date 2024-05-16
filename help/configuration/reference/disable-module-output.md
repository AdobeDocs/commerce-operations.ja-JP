---
title: モジュール出力を無効にする
description: モジュール出力を無効にする方法を説明します。
exl-id: af556bf5-8454-4d65-8ac8-4a64c108f092
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# モジュール出力を無効にする

デフォルトでは、すべてのモジュールは、モジュール出力をビューに書き込めるように設定されています。 出力をオフにすると、ハードな依存関係のために無効にできないモジュールを基本的に無効にできます。

例： `Customer` モジュールは以下に依存： `Review` モジュール、その他 `Review` モジュールは無効にできません。 ただし、顧客によるレビューを許可しない場合は、 `Review` モジュール。

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

1. を編集する `Backend` モジュールの `config.xml` ファイル。
1. 設定変更をエクスポートします。

### を編集する `Backend` モジュール `config.xml` ファイル

1. オリジナルをアーカイブ `config.xml` ファイル。
1. 次のような行をに追加します `<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml` ファイル（の直下） `<default>` 要素：

   ```xml
   <advanced>
       <modules_disable_output>
           <Magento_Newsletter>1</Magento_Newsletter>
       </modules_disable_output>
   </advanced>
   ```

   ここで：

   - `<modules_disable_output>` モジュールのリストが含まれます。
   - `<Magento_Newsletter></Magento_Newsletter>` 出力を無効にするモジュールを指定します。
   - `1` は、の出力を無効にするフラグ `Magento_Newsletter` モジュール。

この設定のサンプル結果として、顧客はニュースレターを受信するために新規登録できなくなりました。

### 設定変更のエクスポート

次のコマンドを実行して、設定の変更を書き出します。

```bash
bin/magento app:config:dump
```

結果は、に書き込まれます `<Magento_install_dir>/app/etc/config.php` ファイル。

次に、キャッシュをクリアして新しい設定を有効にします。

```bash
bin/magento cache:clean config
```

参照： [設定のエクスポート](../cli/export-configuration.md).

## シンプルなデプロイメントでのモジュール出力の無効化

変更内容を配布する必要がないので、Commerceの 1 つのインスタンスでモジュール出力を無効にする手順が簡単です。

1. オリジナルをアーカイブ `<Magento_install_dir>/app/etc/config.php` ファイル。
1. を追加 `advanced` および `modules_disable_output` セクションから `config.php` ファイル（存在しない場合）:

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

この例では、 `Magento_Review` モジュールが無効になり、お客様は製品をレビューできなくなりました。
出力を再度有効にするには、値をに設定します `0`.
