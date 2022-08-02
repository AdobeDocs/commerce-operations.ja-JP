---
title: 検索ストップワードの設定
description: CSV ファイルを使用してAdobe Commerceのストップワードを管理する方法を説明します。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---


# 検索ストップワードの設定

一般に _ストップワード_ は、検索エンジンがテキストを処理した後で除外する一般的な単語です。 元々、ディスク容量とメモリが非常に限られていた場合、キロバイトを節約すると、パフォーマンスが大幅に向上しました。 したがって、検索エンジンは、特定の単語を無視し、インデックスを小さく保つことで、パフォーマンスを向上させました。

現在はストレージが増えていますが、パフォーマンスは依然として重要です。 Elasticsearchや OpenSearch は、他の検索エンジンと同様に、現在もストップワードを使用してパフォーマンスを向上させています。

ストップワードは、 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` ディレクトリまたは `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/` ディレクトリに格納されます。

OpenSearch とのストップワードの使用Elasticsearchについて詳しくは、次のリソースを参照してください。

- [ストップワード：パフォーマンスと精度](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [ストップワードの賛否両論](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [ストップワードの使用](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [ストップワードとパフォーマンス](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## ストップワードの設定

ストップワードは、 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` ディレクトリ。 Adobe CommerceとMagento Open Sourceには、デフォルトのロケールのストップワードを含む 1 つの CSV ファイルと、追加のファイルが付属しています。 `stopwords.csv`：別の CSV ファイルで表されないロケールのストップワードを含む

ストップワードファイルのデフォルトの有効期間 [キャッシュ](https://glossary.magento.com/cache) は 15 分です。

### 既存のロケールのストップワードを編集

**ストップワードを編集するには**:

1. Commerce サーバーにログインするか、 [ファイルシステム所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. テキストエディターを使用して、 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` ディレクトリ。

   CSV ファイルは命名規則を使用します `stopwords_<locale_code>.csv`. 例えば、ドイツ語のストップワードファイルの名前はです。 `stopwords_de_DE.csv`.

1. ファイル内の単語の追加、単語の削除、単語の変更を行います。

   （ファイル内の各ストップワードは、新しい行で開始されます。）

1. 変更を保存し、テキストエディターを終了します。
1. 設定キャッシュをクリーンアップします。

   - 管理者： **システム** /ツール/ **キャッシュ管理**. を選択します。 **設定** チェックボックスをオンにし、上のリストから「 **更新**. クリック **送信** 」をクリックしてアクションを完了します。

   - コマンドライン：ファイルシステムの所有者として、次のコマンドを入力します。

      ```bash
      php <magento_root>/bin/magento cache:clean config
      ```

1. 検索結果を確認するには、 [店頭](https://glossary.magento.com/storefront).

### 新しいロケールのストップワードを作成

**ロケールのストップワードを追加するには**:

1. Commerce サーバーにログインするか、 [ファイルシステム所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

1. テキストエディタを使用して、という名前のストップワードファイルを作成します。 `stopwords_<locale_code>.csv` 内 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` ディレクトリ。

   例えば、イタリア語ロケールのストップワードを作成するには、ファイルに名前を付けます `stopwords_it_IT.csv`.

1. ストップワードファイルで、各ストップワードが別々の行にあることを確認します。
1. 変更を保存し、テキストエディターを終了します。
1. 同じディレクトリで、を開きます。 `esconfig.xml` をクリックします。
1. 行を `esconfig.xml` 次のように指定します。

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   例えば、イタリア語のストップワードファイルを追加するには、次の行を追加します。

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. 変更をに保存します。 `esconfig.xml` をクリックし、テキストエディタを終了します。
1. 設定キャッシュをクリーンアップします。

   - 管理者： **システム** /ツール/ **キャッシュ管理**. を選択します。 **設定** チェックボックスをオンにし、上のリストから「 **更新**. クリック **送信** 」をクリックしてアクションを完了します。

   - コマンドライン：ファイルシステムの所有者として、次のコマンドを入力します。

      ```bash
      php <magento_root>/bin/magento magento cache:clean config
      ```

1. ストアフロントで用語を検索して、結果を確認します。

## ストップワードディレクトリを変更

この項では、次のいずれかのデフォルトのストップワードディレクトリをオプションで変更する方法について説明します。

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

場所は、Commerce ソフトウェアのインストール方法によって異なります。 Magento2 GitHub リポジトリを複製した場合、パスは `app/code`. 圧縮されたアーカイブまたはメタパッケージをインストールした場合、パスは `vendor`.

**ディレクトリを変更するには**:

1. ファイルシステムの所有者として、Elasticsearchを開きます。 `di.xml` をクリックします。

   リポジトリを複製した場合は、次の場所に配置されます。 `app/code/Magento/Elasticsearch/etc/di.xml`

   アーカイブまたはメタパッケージを入手した場合は、次の場所にあります。 `vendor/magento/module-elasticsearch/etc/di.xml`

1. の値を変更 `stopwordsDirectory` を目的のディレクトリに追加します。

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. 変更をに保存します。 `di.xml` をクリックし、テキストエディタを終了します。

## モジュールからディレクトリを変更するには

1. [モジュールの作成](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/module-file-structure.html)
1. モジュール内 `etc/di.xml` 手順を追加します。

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. モジュールで、ディレクトリを作成します。 `etc/stopwords`を作成します。

1. 変更をに保存します。 `di.xml` をクリックし、テキストエディタを終了します。
