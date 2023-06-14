---
source-git-commit: 8b82081057af7d134528988d3f9f7cf53f4d7525
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---
# Adobe Commerce技術ドキュメント

コミュニティやドキュメントチーム以外のAdobe従業員からの投稿を歓迎します。

## Adobeオープンソース行動規範

このプロジェクトでは、 [Adobeオープンソース行動規範](code-of-conduct.md) または [.NET Foundation 行動規範](https://dotnetfoundation.org/code-of-conduct). 詳しくは、 [貢献](contributing.md) 記事。

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

この `_jekyll` ディレクトリには、テンプレート化されたトピックと必要なアセットが含まれています。
Liquid テンプレート言語を使用するテンプレートは、 `_jekyll/templated` ディレクトリをHTMLファイルとして。
この `_jekyll/_data` ディレクトリには、テンプレートのレンダリングに使用されるデータを含むファイルが含まれます。

すべてのテンプレートをレンダリングするには：

1. 次に移動： `_jekyll` ディレクトリ。

   cd_jekyll

1. レンダリングスクリプトを実行します。

```
_scripts/render
```

> **注意：** スクリプトを `_jekyll` ディレクトリ。
> **注意：** このスクリプトを実行するには、Ruby がインストールされている必要があります。

スクリプトはレンダリングを実行し、レンダリングされたテンプレートを `help/_includes/templated` ディレクトリ。

詳しくは、ジキルのドキュメントを参照してください。 [データファイル](https://jekyllrb.com/docs/datafiles), [液体フィルター](https://jekyllrb.com/docs/liquid/filters/)、およびその他の機能。
