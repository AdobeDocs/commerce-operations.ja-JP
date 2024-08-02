---
source-git-commit: a6086afc0a1f099b62014ad61098a5a1dc9d4675
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 3%

---
# Adobe Commerce技術ドキュメント

ドキュメントチーム以外のAdobeスタッフや、コミュニティからのコントリビューションを歓迎します。

## Adobe オープン Source行動規範

このプロジェクトでは、[アドビオープンソース行動規範](code-of-conduct.md) または [.NET Foundation 行動規範](https://dotnetfoundation.org/code-of-conduct)を採用しています。詳しくは、[投稿](contributing.md)の記事を参照してください。

## Adobeコンテンツへの投稿について

[Adobeドキュメント投稿者ガイドを参照してください ](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html)。

投稿方法は、投稿者と、投稿したい変更の種類に応じて異なります。

### 軽微な変更

軽微な変更をコントリビューションする場合は、記事にアクセスして記事の下部に表示されるフィードバックエリアをクリックし、**詳細なフィードバックオプション** をクリックします。次に、**編集の提案** をクリックして、GitHub の Markdown ソースファイルに移動します。 GitHub UI を使用して更新を行います。 一般的な [Adobeドキュメント投稿者ガイド ](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) を参照してください。

このリポジトリのドキュメントおよびコード例について投稿者が送信した軽微な修正や説明は、Adobeの利用規約の対象となります。

### コミュニティメンバーによる大幅な変更または新しい記事

Adobeコミュニティのメンバーが新しい記事を作成したり、大きな変更をコントリビューションしたりする場合は、Git リポジトリーの「イシュー」タブを使用してイシューを送信し、ドキュメントチームとのやり取りを開始してください。 計画に同意したら、公開リポジトリと非公開リポジトリでの作業を組み合わせて新しいコンテンツを取り込むために、従業員と協力する必要があります。

<!--
If you submit a pull request with significant changes to documentation and code examples, you'll see a message in the pull request asking you to submit an online contribution license agreement (CLA). We need you to complete the online form before we can review your pull request.
-->

### Adobe社員からの大きな変化

Adobe Experience Cloud ソリューションの製品チームのテクニカルライター、プログラムマネージャー、または開発者で技術記事の投稿または作成を担当している場合は、`https://git.corp.adobe.com/AdobeDocs` のプライベートリポジトリを使用する必要があります。

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## ツールと設定

コミュニティのコントリビューターは、基本的な編集を行う場合は GitHub UI を使用し、大きな変更を加える場合はリポジトリをフォークします。

詳しくは、[Adobeドキュメント投稿者ガイド ](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) を参照してください。

## Markdown を使用してトピックを書式設定する方法

このリポジトリ内の記事はすべて、GitHub Flavored Markdown を使用しています。 Markdown について詳しくは、以下を参照してください。

* [Markdown の基本 ](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
* [ 印刷用 Markdown チートシート ](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## テンプレート

一部のトピックでは、データファイルとテンプレートを使用して、公開済みコンテンツを生成します。 このアプローチのユースケースを次に示します。

* プログラムで生成された大きなコンテンツセットの公開
* 統合のために、YAML などの機械読み取り可能なファイル形式を必要とする複数のシステム（Site-Wide Analysis Tool など）をまたいで、顧客に単一の情報源を提供する

テンプレート化されたコンテンツの例としては、次のようなものがあります（ただし、これに限定されません）。

* [CLI ツールリファレンス ](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html)
* [ 製品可用性テーブル ](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)
* [ 必要システム構成テーブル ](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)

### テンプレートコンテンツの生成

通常、ほとんどのライターは、製品可用性テーブルとシステム要件テーブルにリリースバージョンを追加するだけで済みます。 その他のテンプレート化されたコンテンツのメンテナンスは、すべて専任のチームメンバーが自動化または管理します。 これらの説明は、ほとんどのライターを対象としています。

>**メモ：**
>
>* テンプレート化されたコンテンツを生成するには、ターミナルのコマンドラインで作業する必要があります。
>* レンダリングスクリプトを実行するには、Ruby がインストールされている必要があります。 必要なバージョンについては [_jekyll/.ruby-version](_jekyll/.ruby-version) を参照してください。

テンプレート化されたコンテンツのファイル構造について詳しくは、次を参照してください。

* `_jekyll` - テンプレート化されたトピックと必要なアセットが含まれます
* `_jekyll/_data` - テンプレートのレンダリングに使用される機械読み取り可能なファイル形式が含まれます
* `_jekyll/templated` – 液体テンプレート言語を使用するHTMLベースのテンプレートファイルが含まれます
* `help/_includes/templated` - テンプレート化されたコンテンツの生成された出力 `.md` ファイル・フォーマットで含み、Experience League・トピックで公開できるようにします。レンダリング・スクリプトによって、生成された出力がこのディレクトリに自動的に書き込まれます

テンプレート化されたコンテンツを更新するには：

1. テキストエディターで、`/jekyll/_data` ディレクトリにあるデータファイルを開きます。 例：

   * [ 製品可用性テーブル ](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html): `/jekyll/_data/product-availability.yml`
   * [ 必要システム構成テーブル ](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html): `/jekyll/_data/system-requirements.yml`

1. 既存の YAML 構造を使用してエントリを作成します。

   例えば、Adobe Commerceのバージョンを製品稼動テーブルに追加するには、`/jekyll/_data/product-availability.yml` ファイルの「`extensions`」セクションと「`services`」セクションの各エントリに次のコードを追加します（必要に応じてバージョン番号を変更します）。

   ```
   support:
      - core: 1.2.3
        version: 4.5.6
   ```

1. `_jekyll` ディレクトリに移動します。

   ```
   cd _jekyll
   ```

1. テンプレート化されたコンテンツを生成し、出力を `help/_includes/templated` ディレクトリに書き込みます。

   ```
   rake render
   ```

   >**注意：** スクリプトは `_jekyll` ディレクトリから実行する必要があります。 スクリプトを初めて実行する場合は、`bundle install` コマンドを使用して Ruby の依存関係をインストールする必要があります。

1. `root` ディレクトリに戻ります。

   ```
   cd ..
   ```

1. 期待される `help/_includes/templated` ファイルが変更されたことを確認します。

   ```
   git status
   ```

   次のような出力が表示されます。

   ```
   modified:   _data/product-availability.yml
   modified:   help/_includes/templated/product-availability-extensions.md
   ```

1. 変更をプッシュします。

   ```
   git add .
   git commit -m "descriptive message of the intended commit"
   git push
   ```

[ データファイル ](https://jekyllrb.com/docs/datafiles)、[ 液体フィルター ](https://jekyllrb.com/docs/liquid/filters/) およびその他の機能について詳しくは、Jekyll のドキュメントを参照してください。
