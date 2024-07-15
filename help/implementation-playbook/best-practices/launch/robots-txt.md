---
title: Web クローラーを設定するためのベストプラクティス
description: 「robots.txt」および「sitemap.xml」ファイルを使用して、Adobe Commerce サイトに関する手順を web クローラーに渡す方法を説明します。
role: Developer
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: e1e7ad76b1df8e920ab7f9740fd4be8dc7335954
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---


# Web クローラーを設定するためのベストプラクティス

この記事では、設定やセキュリティなど、Adobe Commerceで `robots.txt` ファイルや `sitemap.xml` ファイルを使用するためのベストプラクティスを説明します。 これらのファイルは、web クローラー（通常は検索エンジンロボット）が web サイト上のページをクロールする方法を指示します。 これらのファイルを設定すると、サイトのパフォーマンスと検索エンジンの最適化を向上させることができます。

>[!NOTE]
>
>これらのベストプラクティスは、ネイティブのAdobe Commerce ストアフロントを使用するプロジェクトにのみ当てはまります。 他のストアフロントソリューション（Adobe Experience Manager、ヘッドレスなど）を使用するAdobe Commerce プロジェクトには適用されません。

## 影響を受ける製品とバージョン

[ サポートされているすべてのバージョン ](../../../release/versions.md):

- クラウドインフラストラクチャー上のAdobe Commerce
- Adobe Commerce オンプレミス

## クラウドインフラストラクチャー上のAdobe Commerce

デフォルトのAdobe Commerce プロジェクトには、1 つの web サイト、ストア、ストアビューを含む階層が含まれています。 より複雑な実装の場合は、_マルチサイト_ ストアフロント用に追加の web サイト、ストア、ストア表示を作成できます。

### 単一サイトのストアフロント

単一サイトのストアフロント用に `robots.txt` ファイルと `sitemap.xml` ファイルを設定する際は、次のベストプラクティスに従います。

- プロジェクトで [`ece-tools`](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) バージョン 2002.0.12 以降が使用されていることを確認します。
- 管理アプリケーションを使用して、`robots.txt` ファイルにコンテンツを追加します。

  >[!TIP]
  >
  >ストアの自動生成された `robots.txt` ファイルを `<domain.your.project>/robots.txt` で表示します。

- Admin アプリケーションを使用して、`sitemap.xml` ファイルを生成します。

  >[!IMPORTANT]
  >
  >クラウドインフラストラクチャプロジェクト上のAdobe Commerceの読み取り専用ファイルシステムがあるので、ファイルを生成する前に `pub/media` パスを指定する必要があります。

- カスタム Fastly VCL スニペットを使用して、サイトのルートから、両方のファイルの `pub/media/` の場所にリダイレクトします。

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
  }
  ```

- Web ブラウザーでファイルを表示して、リダイレクトをテストします。 例えば、`<domain.your.project>/robots.txt` と `<domain.your.project>/sitemap.xml` です。 リダイレクトを設定したルートパスを使用しており、別のパスを使用していないことを確認してください。

>[!INFO]
>
>手順について詳しくは、[ サイトマップと検索エンジンロボットの追加 ](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) を参照してください。


### マルチサイトのストアフロント

クラウドインフラストラクチャー上にAdobe Commerceを 1 つ実装するだけで、複数のストアを設定して実行できます。 [ 複数の web サイトまたはストアの設定 ](https://devdocs.magento.com/cloud/project/project-multi-sites.html) を参照してください。

マルチサイトストアフロントでは、[ シングルサイトストアフロント ](#single-site-storefronts) 用の `robots.txt` ファイルと `sitemap.xml` ファイルの設定に関するベストプラクティスが適用されますが、次の 2 つの重要な違いがあります。

- `robots.txt` と `sitemap.xml` のファイル名に、対応するサイトの名前が含まれていることを確認してください。 例：
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- 少し変更したカスタム Fastly VCL スニペットを使用して、サイトのルートから、サイトをまたいで両方のファイルを `pub/media` の場所にリダイレクトします。

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path == \"/robots.txt\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) { set req.url = \"pub/media/\" re.group.1 \"_robots.txt\"; }} else if ( req.url.path == \"/sitemap.xml\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) {  set req.url = \"pub/media/\" re.group.1 \"_sitemap.xml\"; }}"
  }
  ```

## Adobe Commerce オンプレミス

管理アプリケーションを使用して `robots.txt` ファイルと `sitemap.xml` ファイルを設定し、ボットが不要なコンテンツをスキャンしてインデックスを作成しないようにします（[ 検索エンジンロボット ](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots) を参照）。

>[!TIP]
>
>オンプレミス環境の場合、ファイルを書き込む場所は、Adobe Commerceのインストール方法によって異なります。 インストールに適した `/path/to/commerce/pub/media/` または `/path/to/commerce/media` のどちらかにファイルを書き込みます。

## セキュリティ

`robots.txt` ファイルで管理者パスを公開しないでください。 管理者パスを公開すると、サイトハッキングの脆弱性が生じ、データが失われる可能性があります。 `robots.txt` ファイルから管理者パスを削除します。

`robots.txt` ファイルを編集し、管理パスのすべてのエントリを削除する手順については、[ マーケティングユーザーガイド/SEO と検索/検索エンジンロボット ](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots) を参照してください。

>[!TIP]
>
>サポートが必要な場合は、[Adobe Commerce サポートチケットを送信 ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) してください。

## 追加情報

- [Web サイト、ストア、ストア表示について ](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [Web サイトの追加 ](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [Fastly を使用して、Adobe Commerce サイトの悪意のあるトラフィックをブロックする ](https://devdocs.magento.com/cloud/cdn/fastly-vcl-blocking.html)
- [robots.txt で、cloud infrastructure 2.3.x のAdobe Commerceに 404 エラーが発生する ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)
