---
title: 検索ストップワードの設定
description: CSV ファイルを使用してAdobe Commerceのストップワードを管理する方法について説明します。
feature: Configuration, Search
exl-id: 75320868-9939-4a6e-8dbb-73ca68c9f0ee
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 0%

---

# 検索ストップワードの設定

一般的に、_ストップワード_&#x200B;は、検索エンジンがテキストを処理した後に除外する一般的な単語です。 もともと、ディスク容量とメモリが非常に限られていたときは、1 キロバイトの節約ごとにパフォーマンスが大幅に向上しました。 そのため、検索エンジンは、特定の単語を無視し、インデックスを小さく保つことで、パフォーマンスの向上を実現しました。

今日はストレージの容量が増えていますが、パフォーマンスはまだ重要です。 ElasticsearchとOpenSearchは、ほかの検索エンジンと同様に、パフォーマンスを向上させるためにストップワードを使用しています。

Commerce ソフトウェアのインストール方法に応じて、`<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` ディレクトリまたは`<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/` ディレクトリにあるCSV ファイルを使用して、ストップワードを管理する必要があります。

ElasticsearchとOpenSearchでのストップワードの使用方法について詳しくは、次の資料を参照してください。

- [ストップワード：パフォーマンスと精度](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [ストップワードの長所と短所](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [ストップワードの使用](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [ストップワードとパフォーマンス](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## ストップワードの設定

ストップワードは`<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` ディレクトリにあります。 Adobe Commerceには、デフォルトのロケールのストップワードを含む1つのCSV ファイルと、別のCSV ファイルで表されないロケールのストップワードを含む追加のファイル `stopwords.csv`が付属しています。

ストップワードファイルキャッシュのデフォルトの有効期間は15分です。

### 既存のロケールのストップワードの編集

**ストップワードを編集するには**:

1. Commerce サーバーにログインするか、[ ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md)に切り替えます。
1. テキストエディターを使用して、`<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` ディレクトリでストップワードファイルを開きます。

   CSV ファイルでは、命名規則`stopwords_<locale_code>.csv`が使用されます。 例えば、ドイツ語のストップワードファイルの名前は`stopwords_de_DE.csv`です。

1. ファイル内の単語の追加、単語の削除、または単語の変更。

   （ファイル内の各ストップワードは新しい行から始まります）。

1. 変更を保存し、テキストエディターを終了します。
1. 設定キャッシュをクリーニングします。

   - 管理者：**システム** > ツール > **キャッシュ管理**。 「**設定**」チェックボックスを選択し、その上のリストから「**更新**」をクリックします。 「**送信**」をクリックして、アクションを完了します。

   - コマンドライン：ファイルシステムの所有者として、次のコマンドを入力します。

     ```shell
     php <magento_root>/bin/magento cache:clean config
     ```

1. ストアフロントで条件を検索して、結果を確認します。

### 新しいロケールのストップワードの作成

**ロケールのストップワードを追加するには**:

1. Commerce サーバーにログインするか、[ ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md)に切り替えます。

1. テキストエディターを使用して、`<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` ディレクトリに`stopwords_<locale_code>.csv`という名前のストップワードファイルを作成します。

   例えば、イタリア語ロケールのストップワードを作成するには、ファイルに`stopwords_it_IT.csv`という名前を付けます。

1. ストップワードファイルでは、各ストップワードが別々の行にあることを確認します。
1. 変更を保存し、テキストエディターを終了します。
1. 同じディレクトリで、テキストエディターで`esconfig.xml`を開きます。
1. 次のように`esconfig.xml`に行を追加します。

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   例えば、イタリア語のストップワードファイルを追加するには、次の行を追加します。

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. 変更を`esconfig.xml`に保存し、テキストエディターを終了します。
1. 設定キャッシュをクリーニングします。

   - 管理者：**システム** > ツール > **キャッシュ管理**。 「**設定**」チェックボックスを選択し、その上のリストから「**更新**」をクリックします。 「**送信**」をクリックして、アクションを完了します。

   - コマンドライン：ファイルシステムの所有者として、次のコマンドを入力します。

     ```shell
     php <magento_root>/bin/magento magento cache:clean config
     ```

1. ストアフロントで条件を検索して、結果を確認します。

## ストップワードディレクトリの変更

この節では、オプションでデフォルトのストップワードディレクトリを次のいずれかから変更する方法について説明します。

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

場所は、Commerce ソフトウェアのインストール方法によって異なります。 Magento 2 GitHub リポジトリをクローンした場合、パスは`app/code`の下にあります。 圧縮アーカイブまたはメタパッケージをインストールした場合、パスは`vendor`未満です。

**ディレクトリを変更するには**:

1. ファイルシステムの所有者として、テキストエディターでElasticsearch `di.xml`を開きます。

   リポジトリを複製した場合、リポジトリは`app/code/Magento/Elasticsearch/etc/di.xml`にあります

   アーカイブまたはメタパッケージを取得した場合、そのアーカイブは`vendor/magento/module-elasticsearch/etc/di.xml`にあります

1. `stopwordsDirectory`の値を目的のディレクトリに変更します。

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. 変更を`di.xml`に保存して、テキストエディターを終了します。

## モジュールからディレクトリを変更するには

1. [モジュールの作成](https://developer.adobe.com/commerce/php/development/build/component-file-structure/)
1. モジュール `etc/di.xml`で、次の手順を追加します。

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. モジュールで、対応するCSV ファイルを含むディレクトリ `etc/stopwords`を作成します。

1. 変更を`di.xml`に保存して、テキストエディターを終了します。
