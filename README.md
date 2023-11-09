---
source-git-commit: 2727ddb18995ac2163276a0aa8573161add48971
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 3%

---
# Adobe Commerce技術ドキュメント

コミュニティやドキュメントチーム以外のAdobe従業員からの投稿を歓迎します。

## Adobeオープンソース行動規範

このプロジェクトでは、[アドビオープンソース行動規範](code-of-conduct.md) または [.NET Foundation 行動規範](https://dotnetfoundation.org/code-of-conduct)を採用しています。詳しくは、[投稿](contributing.md)の記事を参照してください。

## Adobeコンテンツへの投稿について

詳しくは、 [Adobeドキュメント寄稿者ガイド](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

投稿方法は、投稿者と、投稿したい変更の種類に応じて異なります。

### 軽微な変更

善意でマイナーな更新を行う場合は、記事にアクセスし、 **編集** 記事の GitHub ソースに移動する記事内のリンク。 その後、GitHub UI を使用して更新をおこないます。 一般 [Adobeドキュメント寄稿者ガイド](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) を参照してください。

このリポジトリのドキュメントおよびコード例について送信したマイナーな修正や説明は、Adobe利用条件の適用を受けます。

### コミュニティメンバーによる大きな変更または新しい記事

Adobeコミュニティのメンバーが新しい記事を作成したり、大きな変更を投稿したりする場合は、Git リポジトリの「Issues」タブを使用して、ドキュメントチームとの会話を開始するための問題を送信してください。 計画に同意したら、公開および非公開リポジトリでの作業を組み合わせて新しいコンテンツを取り込むために、従業員と協力する必要があります。

<!--
If you submit a pull request with significant changes to documentation and code examples, you'll see a message in the pull request asking you to submit an online contribution license agreement (CLA). We need you to complete the online form before we can review your pull request.
-->

### Adobe従業員からの大きな変更

Adobe Experience Cloudソリューションの製品チーム、プログラムマネージャーまたは開発者で、技術記事の投稿や作成が職務となっている場合は、次のプライベートリポジトリを使用する必要があります。 `https://git.corp.adobe.com/AdobeDocs`.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## ツールとセットアップ

コミュニティの投稿者は、GitHub UI を使用して基本的な編集をおこなったり、リポジトリをフォークして大きな貢献をすることができます。

詳しくは、 [Adobeドキュメント寄稿者ガイド](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) 」を参照してください。

## Markdown を使用してトピックをフォーマットする方法

このリポジトリ内の記事はすべて、GitHub 固有の Markdown を使用しています。 Markdown に詳しくない場合は、以下を参照してください。

* [Markdown の基本](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
* [印刷可能な Markdown の早見表](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## テンプレート

一部のトピックでは、データファイルとテンプレートを使用して公開済みコンテンツを生成します。 このアプローチの使用例を次に示します。

* プログラムで生成された大量のコンテンツセットの公開
* 統合のために YAML などの機械で読み取り可能なファイル形式が必要な複数のシステムをまたいだお客様に対して、単一の情報源を提供する（サイト全体分析ツールなど）

テンプレート化されたコンテンツの例を次に示しますが、これらに限定されません。

* [CLI ツールリファレンス](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html)
* [製品の可用性テーブル](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)
* [必要システム構成テーブル](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)

### テンプレートコンテンツを生成

一般に、ほとんどのライターは、製品の可用性と必要システム構成の表にリリースバージョンを追加するだけで済みます。 その他すべてのテンプレートコンテンツのメンテナンスは、専属のチームメンバーが自動化または管理します。 これらの手順は、「ほとんど」のライターを対象としています。

>**注意：**
>
>* テンプレートコンテンツを生成するには、ターミナルのコマンドラインで作業する必要があります。
>* レンダリングスクリプトを実行するには、Ruby がインストールされている必要があります。 詳しくは、 [_jekyll/.ruby-version](_jekyll/.ruby-version) 必要なバージョンの場合。

テンプレートコンテンツのファイル構造については、以下を参照してください。

* `_jekyll` — テンプレート化されたトピックと必要なアセットを含みます。
* `_jekyll/_data` — テンプレートのレンダリングに使用する、マシンが読み取り可能なファイル形式を含みます。
* `_jekyll/templated` — 液体HTML言語を使用するテンプレートファイルを含みます。
* `help/_includes/templated` — テンプレートコンテンツの生成された出力を含みます。 `.md` Experience Leagueトピックにパブリッシュできるようにファイル形式を設定します。レンダリングスクリプトは生成された出力をこのディレクトリに自動的に書き込みます。

テンプレートコンテンツを更新するには：

1. テキストエディターで、 `/jekyll/_data` ディレクトリ。 例：

   * [製品の可用性テーブル](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html): `/jekyll/_data/product-availability.yml`
   * [必要システム構成テーブル](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html): `/jekyll/_data/system-requirements.yml`

1. 既存の YAML 構造を使用してエントリを作成します。

   例えば、Adobe Commerceのバージョンを製品の可用性テーブルに追加するには、 `extensions` および `services` セクション `/jekyll/_data/product-availability.yml` ファイル（必要に応じてバージョン番号を変更）:

   ```
   support:
      - core: 1.2.3
        version: 4.5.6
   ```

1. 次に移動： `_jekyll` ディレクトリ。

   ```
   cd _jekyll
   ```

1. テンプレートコンテンツを生成し、出力を `help/_includes/templated` ディレクトリ。

   ```
   rake render
   ```

   >**注意：** スクリプトを `_jekyll` ディレクトリ。 スクリプトを初めて実行する場合は、Ruby の依存関係を最初に `bundle install` コマンドを使用します。

1. 期待される `help/_includes/templated` ファイルが変更されました。

   ```
   git status
   ```

   次のような出力が表示されます。

   ```
   modified:   _data/product-availability.yml
   modified:   ../help/_includes/templated/product-availability-extensions.md
   ```

詳しくは、ジキルのドキュメントを参照してください。 [データファイル](https://jekyllrb.com/docs/datafiles), [液体フィルター](https://jekyllrb.com/docs/liquid/filters/)、およびその他の機能。
