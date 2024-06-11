---
source-git-commit: 0709cd6510adce0f513894fdecb2de5ac88d0e87
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 3%

---
# Adobe Commerce技術ドキュメント

ドキュメントチーム以外のAdobeスタッフや、コミュニティからのコントリビューションを歓迎します。

## Adobeオープンソース行動規範

このプロジェクトでは、[アドビオープンソース行動規範](code-of-conduct.md) または [.NET Foundation 行動規範](https://dotnetfoundation.org/code-of-conduct)を採用しています。詳しくは、[投稿](contributing.md)の記事を参照してください。

## Adobeコンテンツへの投稿について

を参照してください。 [Adobeドキュメント投稿者ガイド](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

投稿方法は、投稿者と、投稿したい変更の種類に応じて異なります。

### 軽微な変更

軽微な変更を行う場合は、記事にアクセスして、記事の下部に表示されるフィードバック領域をクリックし、 **詳細なフィードバックオプション**&#x200B;を選択し、 **編集の提案** をクリックして、GitHub の Markdown ソースファイルに移動します。 GitHub UI を使用して更新を行います。 一般を参照してください [Adobeドキュメント投稿者ガイド](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) を参照してください。

このリポジトリのドキュメントおよびコード例について投稿者が送信した軽微な修正や説明は、Adobeの利用規約の対象となります。

### コミュニティメンバーによる大幅な変更または新しい記事

Adobeコミュニティのメンバーが新しい記事を作成したり、大きな変更をコントリビューションしたりする場合は、Git リポジトリーの「イシュー」タブを使用してイシューを送信し、ドキュメントチームとのやり取りを開始してください。 計画に同意したら、公開リポジトリと非公開リポジトリでの作業を組み合わせて新しいコンテンツを取り込むために、従業員と協力する必要があります。

<!--
If you submit a pull request with significant changes to documentation and code examples, you'll see a message in the pull request asking you to submit an online contribution license agreement (CLA). We need you to complete the online form before we can review your pull request.
-->

### Adobe社員からの大きな変化

Adobe Experience Cloud ソリューションの製品チームのテクニカルライター、プログラムマネージャー、または開発者で技術記事の投稿または作成を担当している場合は、プライベートリポジトリ（）を使用する必要があります `https://git.corp.adobe.com/AdobeDocs`.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## ツールと設定

コミュニティのコントリビューターは、基本的な編集を行う場合は GitHub UI を使用し、大きな変更を加える場合はリポジトリをフォークします。

を参照してください。 [Adobeドキュメント投稿者ガイド](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) を参照してください。

## Markdown を使用してトピックを書式設定する方法

このリポジトリ内の記事はすべて、GitHub Flavored Markdown を使用しています。 Markdown について詳しくは、以下を参照してください。

* [Markdown の基本](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
* [Markdown の早見表（印刷用）](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## テンプレート

一部のトピックでは、データファイルとテンプレートを使用して、公開済みコンテンツを生成します。 このアプローチのユースケースを次に示します。

* プログラムで生成された大きなコンテンツセットの公開
* 統合のために、YAML などの機械読み取り可能なファイル形式を必要とする複数のシステム（Site-Wide Analysis Tool など）をまたいで、顧客に単一の情報源を提供する

テンプレート化されたコンテンツの例としては、次のようなものがあります（ただし、これに限定されません）。

* [CLI ツールリファレンス](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html)
* [製品可用性テーブル](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)
* [必要システム構成テーブル](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)

### テンプレートコンテンツの生成

通常、ほとんどのライターは、製品可用性テーブルとシステム要件テーブルにリリースバージョンを追加するだけで済みます。 その他のテンプレート化されたコンテンツのメンテナンスは、すべて専任のチームメンバーが自動化または管理します。 これらの説明は、ほとんどのライターを対象としています。

>**注意：**
>
>* テンプレート化されたコンテンツを生成するには、ターミナルのコマンドラインで作業する必要があります。
>* レンダリングスクリプトを実行するには、Ruby がインストールされている必要があります。 参照： [_jekyll/.ruby-version](_jekyll/.ruby-version) （必要なバージョン用）。

テンプレート化されたコンテンツのファイル構造について詳しくは、次を参照してください。

* `_jekyll`- テンプレート化されたトピックと必要なアセットが含まれます。
* `_jekyll/_data`- テンプレートのレンダリングに使用する、機械で読み取り可能なファイル形式が含まれます。
* `_jekyll/templated` – 液体テンプレート言語を使用するHTMLベースのテンプレートファイルが含まれます
* `help/_includes/templated` – でテンプレート化されたコンテンツ用に生成された出力が含まれます `.md` Experience League トピックでパブリッシュできるようにファイル フォーマットを設定します。レンダリング スクリプトは、生成された出力をこのフォルダに自動的に書き込みます

テンプレート化されたコンテンツを更新するには：

1. テキストエディターで、にあるデータファイルを開きます。 `/jekyll/_data` ディレクトリ。 例：

   * [製品可用性テーブル](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html): `/jekyll/_data/product-availability.yml`
   * [必要システム構成テーブル](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html): `/jekyll/_data/system-requirements.yml`

1. 既存の YAML 構造を使用してエントリを作成します。

   例えば、Adobe Commerceのバージョンを製品可用性テーブルに追加するには、内の各エントリに次のコードを追加します `extensions` および `services` のセクション `/jekyll/_data/product-availability.yml` ファイル（必要に応じてバージョン番号を変更）:

   ```
   support:
      - core: 1.2.3
        version: 4.5.6
   ```

1. に移動します。 `_jekyll` ディレクトリ。

   ```
   cd _jekyll
   ```

1. テンプレート化されたコンテンツを生成し、出力をに書き込む `help/_includes/templated` ディレクトリ。

   ```
   rake render
   ```

   >**注意：** からスクリプトを実行する必要があります。 `_jekyll` ディレクトリ。 このスクリプトを初めて実行する場合は、まずで Ruby の依存関係をインストールする必要があります `bundle install` コマンド。

1. に戻ります。 `root` ディレクトリ。

   ```
   cd ..
   ```

1. 期待されることを確認します。 `help/_includes/templated` ファイルが変更されました。

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
   git add
   git commit -m "_descriptive message of the intended commit_"
   git push
   ```

について詳しくは、Jekyll のドキュメントを参照してください。 [データファイル](https://jekyllrb.com/docs/datafiles), [液体フィルター](https://jekyllrb.com/docs/liquid/filters/)、およびその他の機能。
