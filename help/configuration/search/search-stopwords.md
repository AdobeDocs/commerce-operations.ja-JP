---
title: 検索ストップワードの設定
description: CSV ファイルを使用してAdobe Commerceのストップワードを管理する方法を説明します。
feature: Configuration, Search
exl-id: 75320868-9939-4a6e-8dbb-73ca68c9f0ee
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# 検索ストップワードの設定

一般に、_ストップワード_ は、テキストを処理した後に検索エンジンが除外する一般的な単語です。 当初は、ディスク容量とメモリが非常に制限されていた場合、1 キロバイトの節約はパフォーマンスの大幅な向上を意味しました。 したがって、検索エンジンでは、特定の単語を無視してインデックスを小さく保つことで、パフォーマンスが向上しました。

現在はストレージ容量が増えていますが、パフォーマンスは依然として重要です。 Elasticsearchと OpenSearch は、他の検索エンジンと同様に、パフォーマンスを向上させるためにストップワードを使用します。

Commerce ソフトウェアのインストール方法に応じて、`<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` ディレクトリまたは `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/` ディレクトリにある CSV ファイルを使用してストップワードを管理する必要があります。

Elasticsearchと OpenSearch でストップワードを使用する方法について詳しくは、次のリソースを参照してください。

- [ ストップワード：パフォーマンスと精度の比較 ](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [ ストップワードの長所と短所 ](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [ ストップワードの使用 ](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [ ストップワードとパフォーマンス ](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## ストップワードの設定

ストップワードは `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` ディレクトリにあります。 Adobe Commerceには、デフォルトのロケールのストップワードを含んだ 1 つの CSV ファイルと、別の CSV ファイルで表されないロケールのストップワードを含んだ `stopwords.csv` という追加のファイルが付属しています。

ストップワードファイルキャッシュのデフォルトの有効期間は 15 分です。

### 既存のロケールのストップワードの編集

**ストップワードを編集するには**:

1. Commerce サーバーにログインするか、[ ファイルシステムのオーナー ](../../installation/prerequisites/file-system/overview.md) に切り替えます。
1. テキストエディターを使用して、ストップワードファイルを `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` ディレクトリで開きます。

   CSV ファイルでは、命名規則 `stopwords_<locale_code>.csv` を使用します。 例えば、ドイツ語のストップワードファイルの名前は `stopwords_de_DE.csv` です。

1. ファイル内の単語を追加、削除、または変更します。

   （ファイルの各ストップワードは、新しい行で開始します）。

1. 変更を保存し、テキストエディターを終了します。
1. 設定キャッシュをクリーンアップします。

   - 管理者：**システム**/ツール/**キャッシュ管理**。 「**設定**」チェックボックスを選択し、その上のリストから「**更新**」をクリックします。 「**送信**」をクリックして、アクションを完了します。

   - コマンドライン：ファイルシステムの所有者として、次のコマンドを入力します。

     ```bash
     php <magento_root>/bin/magento cache:clean config
     ```

1. ストアフロントで用語を検索して、結果を確認してください。

### 新しいロケールのストップワードの作成

**ロケールのストップワードを追加するには**:

1. Commerce サーバーにログインするか、[ ファイルシステムのオーナー ](../../installation/prerequisites/file-system/overview.md) に切り替えます。

1. テキストエディターを使用して、`stopwords_<locale_code>.csv` ディレクトリに `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` というストップワードファイルを作成します。

   例えば、イタリア語ロケールのストップワードを作成するには、ファイルに `stopwords_it_IT.csv` という名前を付けます。

1. ストップワードファイルで、各ストップワードが別々の行にあることを確認します。
1. 変更を保存し、テキストエディターを終了します。
1. 同じディレクトリで、テキストエディターで `esconfig.xml` を開きます。
1. に行を次のように追加 `esconfig.xml` ます。

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   例えば、イタリア語のストップワードファイルを追加するには、次の行を追加します。

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. 変更内容を `esconfig.xml` に保存し、テキストエディターを終了します。
1. 設定キャッシュをクリーンアップします。

   - 管理者：**システム**/ツール/**キャッシュ管理**。 「**設定**」チェックボックスを選択し、その上のリストから「**更新**」をクリックします。 「**送信**」をクリックして、アクションを完了します。

   - コマンドライン：ファイルシステムの所有者として、次のコマンドを入力します。

     ```bash
     php <magento_root>/bin/magento magento cache:clean config
     ```

1. ストアフロントで用語を検索して、結果を確認してください。

## ストップワードディレクトリの変更

この節では、デフォルトのストップワードディレクトリをオプションで次のいずれかから変更する方法について説明します。

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

場所は、Commerce ソフトウェアのインストール方法によって異なります。 Magento 2 GitHub リポジトリのクローンを作成した場合、パスは `app/code` の下にあります。 圧縮されたアーカイブまたはメタパッケージをインストールした場合、パスは `vendor` 下になります。

**ディレクトリを変更するには**:

1. ファイルシステムのオーナーとして、Elasticsearch `di.xml` をテキストエディターで開きます。

   リポジトリのクローンを作成した場合は、`app/code/Magento/Elasticsearch/etc/di.xml` にあります。

   アーカイブやメタパッケージを入手した場合は、`vendor/magento/module-elasticsearch/etc/di.xml` にあります。

1. `stopwordsDirectory` の値を目的のディレクトリに変更します。

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. `di.xml` への変更を保存し、テキストエディターを終了します。

## モジュールからディレクトリを変更するには

1. [ モジュールの作成 ](https://developer.adobe.com/commerce/php/development/build/component-file-structure/)
1. モジュールに、手順 `etc/di.xml` 追加します。

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. モジュールで、ディレクトリ `etc/stopwords` を、対応する CSV ファイルと共に作成します。

1. `di.xml` への変更を保存し、テキストエディターを終了します。
