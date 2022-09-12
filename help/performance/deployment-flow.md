---
title: デプロイメントフロー
description: 実稼動環境にAdobe CommerceまたはMagento Open Sourceをデプロイするために必要な手順について説明します。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---


# デプロイメントフロー

この [!DNL Commerce] 実稼動デプロイメントフローは、ストアのパフォーマンスを最大限に高めるのに役立ちます。

## 依存関係をインストール

この `composer.json` および `composer.lock` ファイル管理 [!DNL Commerce] 依存関係を確認し、各パッケージに適切なバージョンをインストールします。 依存関係は、の前にインストールする必要があります [前処理依存性注入手順](#preprocess-dependency-injection-instructions) 更新する予定がある場合 [autoloader](#update-the-autoloader).

をインストールするには [!DNL Commerce] 依存関係：

```bash
composer install --no-dev
```

## 前処理依存関係の挿入手順

DI(Dependency Injection) 命令を前処理してコンパイルする場合、次のMagentoを行います。

* すべての既存の設定を読み取り、処理します
* クラス間の依存関係を分析
* 自動生成されたファイル（プロキシ、ファクトリなどを含む）を
* コンパイル済みのデータと設定をキャッシュに格納し、リクエストの処理に要する時間を最大 25%節約

DI 命令を前処理してコンパイルするには、次の手順に従います。

```bash
bin/magento setup:di:compile
```

## オートローダーの更新

コンパイルが完了したら、 [APCu が有効になっています](../performance/software.md#php-settings) オートローダを更新します。

オートローダーを更新するには：

>[!INFO]
>
>この `-o` オプションは、PSR-0/4 のオートロードを classmap に変換して、より高速なオートローダーを取得します。 この `--apcu` オプションは、APCu を使用して、見つかった/見つからなかったクラスをキャッシュします。

```bash
composer dump-autoload -o --apcu
```

オートローダを更新する場合は、次のコマンドを順番に実行する必要があります。

```bash
composer install --no-dev
```

```bash
bin/magento setup:di:compile
```

```bash
composer dump-autoload -o
```

```bash
bin/magento setup:static-content:deploy
```

## 静的コンテンツのデプロイ

静的コンテンツのデプロイが原因 [!DNL Commerce] 次の操作を実行するには：

* すべての静的リソースを分析
* コンテンツの結合、最小化、バンドルを実行
* テーマデータの読み取りと処理
* テーマのフォールバックを分析
* 処理されたコンテンツとマテリアライズドコンテンツを特定のフォルダーに保存して、さらに使用する

静的コンテンツがデプロイされていない場合、 [!DNL Commerce] は、リストに記載されているすべての操作をその場で実行し、応答時間が大幅に増加します。

様々なオプションを使用して、ストアサイズと達成のニーズに基づいてデプロイメント操作をカスタマイズできます。 最も一般的なのは、コンパクトなデプロイ戦略です。 詳しくは、 [静的ファイルのデプロイメント戦略](../configuration/cli/static-view-file-strategy.md)

静的コンテンツをデプロイするには：

```bash
bin/magento setup:static-content:deploy
```

このコマンドを使用すると、Composer はプロジェクトファイルへのマッピングを再構築して、読み込みを高速化できます。

## 実稼動モードを設定

>[!INFO]
>
>モードを実稼動に設定すると、自動的に実行されます `setup:di:compile` および `setup:static-content:deploy`.

最後に、ストアを実稼動モードに配置する必要があります。 実稼動モードは、ストアのパフォーマンスを最大限に高めるために最適化されています。 また、開発者固有のすべての機能を非アクティブ化します。 これは、 `.htaccess` または `nginx.conf` ファイル：

`SetEnv MAGE_MODE production`

静的コンテンツを展開し、コンテンツをコンパイルして、1 つの CLI コマンドでモードを設定することもできます。

```bash
bin/magento deploy:mode:set production
```

このコマンドはバックグラウンドで実行され、特定の各ステップに追加のオプションを設定することはできません。

## その他の起動前のアクション

これらの手順は推奨されますが、必須ではありません。 実稼働モードでストアを起動する直前に実行できます。 リストには、以下が含まれます。

* データのインデックスを再作成して、インデックス内に一貫性のないデータが存在するのを防ぎます。
* キャッシュをフラッシュして、古いデータや誤ったデータがキャッシュに残らないようにします。
* キャッシュをウォーミングアップします。このキャッシュは、最も人気のある、または重要なストアページを事前に呼び出すので、それらのキャッシュが生成され、保存されます。 この操作は、任意のインターネットクローラーで実行するか、小規模なストアがある場合は手動で実行できます。
