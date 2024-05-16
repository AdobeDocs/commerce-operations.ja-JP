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

この記事では、を使用する際のベストプラクティスを説明します `robots.txt` および `sitemap.xml` Adobe Commerceのファイル（設定およびセキュリティを含む）。 これらのファイルは、web クローラー（通常は検索エンジンロボット）が web サイト上のページをクロールする方法を指示します。 これらのファイルを設定すると、サイトのパフォーマンスと検索エンジンの最適化を向上させることができます。

>[!NOTE]
>
>これらのベストプラクティスは、ネイティブのAdobe Commerce ストアフロントを使用するプロジェクトにのみ当てはまります。 他のストアフロントソリューション（Adobe Experience Manager、ヘッドレスなど）を使用するAdobe Commerce プロジェクトには適用されません。

## 影響を受ける製品とバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) （件中）:

- クラウドインフラストラクチャー上のAdobe Commerce
- Adobe Commerce オンプレミス

## クラウドインフラストラクチャー上のAdobe Commerce

デフォルトのAdobe Commerce プロジェクトには、1 つの web サイト、ストア、ストアビューを含む階層が含まれています。 より複雑な実装の場合は、の追加の web サイト、ストア、ストア表示を作成できます。 _マルチサイト_ ストアフロント。

### 単一サイトのストアフロント

を設定する際は、次のベストプラクティスに従います `robots.txt` および `sitemap.xml` 単一サイトのストアフロントのファイル：

- プロジェクトでを使用していることを確認します。 [`ece-tools`](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) バージョン 2002.0.12 以降。
- 管理アプリケーションを使用したのコンテンツを `robots.txt` ファイル。

  >[!TIP]
  >
  >自動生成されたを表示 `robots.txt` ストアのファイル（） `<domain.your.project>/robots.txt`.

- Admin アプリケーションを使用して、 `sitemap.xml` ファイル。

  >[!IMPORTANT]
  >
  >クラウドインフラストラクチャプロジェクト上のAdobe Commerceの読み取り専用ファイルシステムにより、次を指定する必要があります `pub/media` ファイルを生成する前のパス。

- カスタム Fastly VCL スニペットを使用して、サイトのルートからにリダイレクトします `pub/media/` 両方のファイルの場所：

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
  }
  ```

- Web ブラウザーでファイルを表示して、リダイレクトをテストします。 例： `<domain.your.project>/robots.txt` および `<domain.your.project>/sitemap.xml`. リダイレクトを設定したルートパスを使用しており、別のパスを使用していないことを確認してください。

>[!INFO]
>
>参照： [サイトマップと検索エンジンロボットを追加](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) 詳しい手順については、を参照してください。


### マルチサイトのストアフロント

クラウドインフラストラクチャー上にAdobe Commerceを 1 つ実装するだけで、複数のストアを設定して実行できます。 参照： [複数の web サイトまたはストアを設定](https://devdocs.magento.com/cloud/project/project-multi-sites.html).

の設定に関する同じベストプラクティス `robots.txt` および `sitemap.xml` のファイル [単一サイトのストアフロント](#single-site-storefronts) は、次の 2 つの重要な違いがあり、マルチサイトのストアフロントに適用されます。

- 次のことを確認します `robots.txt` および `sitemap.xml` ファイル名には、対応するサイトの名前が含まれます。 例：
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- 少し変更したカスタム Fastly VCL スニペットを使用して、サイトのルートからにリダイレクトします `pub/media` サイト全体での両方のファイルの場所：

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

Admin アプリケーションを使用して、 `robots.txt` および `sitemap.xml` ボットが不要なコンテンツのスキャンやインデックス作成を行わないようにするファイル（ [検索エンジンロボット](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)）に設定します。

>[!TIP]
>
>オンプレミス環境の場合、ファイルを書き込む場所は、Adobe Commerceのインストール方法によって異なります。 ファイルをに書き込みます。 `/path/to/commerce/pub/media/` または `/path/to/commerce/media`（インストールに適した方）。

## セキュリティ

管理パスをユーザーに公開しない `robots.txt` ファイル。 管理者パスを公開すると、サイトハッキングの脆弱性が生じ、データが失われる可能性があります。 からの管理者パスの削除 `robots.txt` ファイル。

を編集する手順は、次のとおりです `robots.txt` 管理パスのすべてのエントリをファイルに保存して削除します。詳しくは、以下を参照してください [マーケティングユーザーガイド / SEO と検索/検索エンジンロボット](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>サポートが必要な場合は、 [Adobe Commerce サポートチケットを送信](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## 追加情報

- [Web サイト、ストア、ストア表示について](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [Web サイトの追加](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [Fastly を使用して、Adobe Commerce サイトの悪意のあるトラフィックをブロックする](https://devdocs.magento.com/cloud/cdn/fastly-vcl-blocking.html)
- [robots.txt で、cloud infrastructure 2.3.x のAdobe Commerceに 404 エラーが発生する](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)
