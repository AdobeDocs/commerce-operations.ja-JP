---
title: 「robots.txt」および「sitemap.xml」ファイルの設定に関するベストプラクティス
description: Adobe Commerceサイトに関する手順を Web クローラーに渡す方法について説明します。
role: Developer
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# 設定のベストプラクティス `robots.txt` および `sitemap.xml` ファイル

この記事では、 `robots.txt` および `sitemap.xml` Adobe Commerce内のファイル（設定やセキュリティを含む） これらのファイルは、Web ロボット（通常は検索エンジンロボット）に対し、Web サイト上のページのクロール方法を指示します。 これらのファイルを設定すると、サイトのパフォーマンスと検索エンジンの最適化を向上できます。

>[!NOTE]
>
>これらのベストプラクティスは、ネイティブのAdobe Commerceストアフロントを使用するプロジェクトにのみ適用されます。 他のストアフロントソリューション (Adobe Experience Manager、ヘッドレスなど ) を使用するAdobe Commerceプロジェクトには適用されません。

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure
- Adobe Commerceオンプレミス

## Adobe Commerce an cloud infrastructure

デフォルトのAdobe Commerceプロジェクトには、単一の Web サイト、ストア、ストア表示を含む階層が含まれています。 より複雑な実装の場合、 _マルチサイト_ ストアフロント。

### 単一サイトストアフロント

次のベストプラクティスに従って、 `robots.txt` および `sitemap.xml` 単一サイトストアフロント用のファイル：

- プロジェクトでが使用されていることを確認します。 [`ece-tools`](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) バージョン 2002.0.12 以降。
- 管理アプリケーションを使用して、 `robots.txt` ファイル。

  >[!TIP]
  >
  >自動生成されたを表示 `robots.txt` 次の場所にあなたのストアのファイル `<domain.your.project>/robots.txt`.

- 管理アプリケーションを使用して、 `sitemap.xml` ファイル。

  >[!IMPORTANT]
  >
  >クラウドインフラストラクチャプロジェクト上のAdobe Commerce上の読み取り専用ファイルシステムにより、 `pub/media` パスを使用してファイルを生成します。

- カスタム Fastly VCL スニペットを使用して、サイトのルートからにリダイレクトします。 `pub/media/` 両方のファイルの場所：

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
  }
  ```

- Web ブラウザーでファイルを表示して、リダイレクトをテストします。 例： `<domain.your.project>/robots.txt` および `<domain.your.project>/sitemap.xml`. 別のパスではなく、リダイレクトを設定したルートパスを使用していることを確認してください。

>[!INFO]
>
>詳しくは、 [サイトマップと検索エンジンのロボットの追加](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) を参照してください。


### マルチサイトストアフロント

クラウドインフラストラクチャ上にAdobe Commerceを 1 回実装して、複数のストアを設定して実行できます。 詳しくは、 [複数の Web サイトまたはストアを設定する](https://devdocs.magento.com/cloud/project/project-multi-sites.html).

同じベストプラクティスで `robots.txt` および `sitemap.xml` 次のファイル [単一サイト店舗](#single-site-storefronts) は、次の 2 つの重要な違いを持つマルチサイトストアフロントに適用されます。

- 次を確認します。 `robots.txt` および `sitemap.xml` ファイル名には、対応するサイトの名前が含まれます。 例：
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- 少し変更されたカスタム Fastly VCL スニペットを使用して、サイトのルートからにリダイレクトします。 `pub/media` サイト全体の両方のファイルの場所：

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path == \"/robots.txt\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) { set req.url = \"pub/media/\" re.group.1 \"_robots.txt\"; }} else if ( req.url.path == \"/sitemap.xml\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) {  set req.url = \"pub/media/\" re.group.1 \"_sitemap.xml\"; }}"
  }
  ```

## Adobe Commerceオンプレミス

管理アプリケーションを使用して、 `robots.txt` および `sitemap.xml` 不要なコンテンツのスキャンやインデックス作成を防ぐためのファイル ( [検索エンジンロボット](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)) をクリックします。

>[!TIP]
>
>オンプレミスデプロイメントの場合、ファイルを書き込む場所は、Adobe Commerceのインストール方法によって異なります。 にファイルを書き込みます。 `/path/to/commerce/pub/media/` または `/path/to/commerce/media`インストールに適した方を選択します。

## セキュリティ

で管理パスを公開しない `robots.txt` ファイル。 管理パスが公開されることは、サイトのハッキングに対する脆弱性であり、データが失われる可能性があります。 次の場所から管理者パスを削除： `robots.txt` ファイル。

を編集する手順については、 `robots.txt` ファイルを作成し、管理パスのすべてのエントリを削除します。詳しくは、 [マーケティングユーザーガイド/ SEO および検索/検索エンジンロボット](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>サポートが必要な場合は、 [Adobe Commerceサポートチケットを送信する](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## 追加情報

- [Web サイト、ストア、ストア表示について](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [Web サイトの追加](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [Fastly を使用してAdobe Commerceサイトの悪意のあるトラフィックをブロックします](https://devdocs.magento.com/cloud/cdn/fastly-vcl-blocking.html)
- [robots.txt が、クラウドインフラストラクチャ 2.3.x 上のAdobe Commerceで 404 エラーを返す](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)
