---
title: Web web クローラーの設定に関するベストプラクティス
description: 「robots.txt」および「sitemap.xml」ファイルを使用して、Adobe Commerce サイトに関する指示をweb web クローラーに渡す方法について説明します。
role: Developer
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 0%

---


# Web web クローラーの設定に関するベストプラクティス

この記事では、Adobe Commerceで`robots.txt`および`sitemap.xml` ファイルを使用するためのベストプラクティス（設定とセキュリティを含む）について説明します。 これらのファイルは、web web クローラー（通常は検索エンジンロボット）がweb サイト上のページをクロールする方法を指示します。 これらのファイルを設定することで、サイトパフォーマンスと検索エンジンの最適化を向上させることができます。

>[!NOTE]
>
>これらのベストプラクティスは、ネイティブのAdobe Commerce ストアフロントのみを使用するプロジェクトに適用されます。 他のストアフロントソリューション（Adobe Experience Manager、ヘッドレスなど）を使用するAdobe Commerce プロジェクトには適用されません。

## 影響を受ける製品とバージョン

[ サポートされているすべてのバージョン ](../../../release/versions.md) /:

- Adobe Commerce on cloud infrastructure
- Adobe Commerce オンプレミス

## Adobe Commerce on cloud infrastructure

デフォルトのAdobe Commerce プロジェクトには、単一のweb サイト、ストア、ストアビューを含む階層が含まれています。 より複雑な実装を行う場合は、_マルチサイト_&#x200B;のストアフロント用に、追加のweb サイト、ストア、ストアビューを作成できます。

### シングルサイトストアフロント

シングルサイトストアフロント用に`robots.txt`および`sitemap.xml` ファイルを設定する場合は、次のベストプラクティスに従ってください。

- プロジェクトが[`ece-tools`](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/ece-tools-package) バージョン 2002.0.12以降を使用していることを確認してください。
- Admin アプリケーションを使用して、`robots.txt` ファイルにコンテンツを追加します。

  >[!TIP]
  >
  >ストアの自動生成された`robots.txt` ファイルを`<domain.your.project>/robots.txt`で表示します。

- Admin アプリケーションを使用して、`sitemap.xml` ファイルを生成します。

  >[!IMPORTANT]
  >
  >Adobe Commerce クラウドインフラストラクチャプロジェクト上の読み取り専用ファイルシステムのため、ファイルを生成する前に`pub/media` パスを指定する必要があります。

- カスタム Fastly VCL スニペットを使用して、サイトのルートから両方のファイルの`pub/media/`の場所にリダイレクトします。

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
  }
  ```

- Web ブラウザーでファイルを表示して、リダイレクトをテストします。 例：`<domain.your.project>/robots.txt`と`<domain.your.project>/sitemap.xml` リダイレクトを設定したルートパスを使用しており、別のパスを使用していないことを確認してください。

>[!INFO]
>
>詳しい手順については、[ サイトマップと検索エンジンロボットの追加](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure-store/robots-sitemap)を参照してください。


### マルチサイトのストアフロント

Adobe Commerce on cloud infrastructureを1回実装して、複数のストアを設定および実行できます。 「[複数のweb サイトまたはストアを設定する](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure-store/multiple-sites)」を参照してください。

[ シングルサイトストアフロント ](#single-site-storefronts)の`robots.txt`および`sitemap.xml` ファイルを設定する場合と同じベストプラクティスが、2つの重要な違いを伴うマルチサイトストアフロントに適用されます。

- `robots.txt`および`sitemap.xml` ファイル名に、対応するサイトの名前が含まれていることを確認してください。 例：
  - `domaineone_robots.txt`
  - `domaintwo_robots.txt`
  - `domainone_sitemap.xml`
  - `domaintwo_sitemap.xml`

- 少し変更されたカスタム Fastly VCL スニペットを使用して、サイトのルートから、サイト全体の両方のファイルの`pub/media`の場所にリダイレクトします。

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

管理者アプリケーションを使用して、`robots.txt`および`sitemap.xml` ファイルを設定し、ボットが不要なコンテンツをスキャンおよびインデックス作成しないようにします（[検索エンジンロボット ](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)を参照）。

>[!TIP]
>
>オンプレミスのデプロイメントの場合、ファイルの書き込み場所は、Adobe Commerceのインストール方法によって異なります。 インストールに適した`/path/to/commerce/pub/media/`または`/path/to/commerce/media`のいずれかにファイルを書き込みます。

## セキュリティ

`robots.txt` ファイル内の管理者パスを公開しないでください。 管理パスを公開すると、サイトハッキングの脆弱性やデータの損失の可能性があります。 `robots.txt` ファイルから管理者パスを削除します。

`robots.txt` ファイルを編集し、管理パスのすべてのエントリを削除する手順については、[ マーケティングユーザーガイド > SEOおよび検索>検索エンジンロボット ](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)を参照してください。

>[!TIP]
>
>サポートが必要な場合は、[Adobe Commerce サポートチケットを送信してください](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket)。

## 追加情報

- [web サイト、実店舗、店舗表示について](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure-store/best-practices)
- [Web サイトの追加](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/stores#add-websites)
- [Fastlyを使用して、Adobe Commerceサイトの悪意のあるトラフィックをブロックする](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/custom-vcl-snippets/fastly-vcl-blocking)
- [robots.txtで、cloud infrastructure 2.3.x上のAdobe Commerceで404 エラーが発生する](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26885)
