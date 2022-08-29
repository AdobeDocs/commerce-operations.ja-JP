---
title: 手動での移行が必要なデータ
description: 'Magento1 からMagento2 へのデータ移行中に手動で移行する必要があるデータとその方法について説明します。 '
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# 手動での移行が必要なデータ

手動で移行する必要があるデータは 4 種類あります。

* メディア

* [ストアフロント](https://glossary.magento.com/storefront) デザイン

* [管理者](https://glossary.magento.com/admin) ユーザーアカウント

* アクセス制御リスト (ACL)

## メディア

このセクションでは、メディアファイルを手動で移行する方法について説明します。

### データベースに保存されたメディアファイル

>[!WARNING]
>
>データベースメディアストレージ方法は、Magento2.4.3 以降で非推奨（廃止予定）となりました。


この節は、次の項目に当てはまります。 *のみ* メディア・ファイルをMagento・データベースに格納する場合。 この手順は、次の前に実行する必要があります。 [データの移行](data.md):

1. 管理者としてMagento1 Admin Panel にログインします。

1. クリック **システム** > **設定** /詳細 > **システム**.

1. 右側のウィンドウで、 **メディアのストレージ設定**.

1. 次の **メディアデータベースを選択** リストで、 [メディアストレージ](https://glossary.magento.com/media-storage) データベース。

1. クリック **同期**.

次に、Magento2 管理パネルで同じ手順を繰り返します。

### ファイルシステム内のメディアファイル

すべてのメディアファイル ( 製品、カテゴリ、 [WYSIWYG](https://glossary.magento.com/wysiwyg) エディターなど ) は、 `<your Magento 1 install dir>/media` から `<your Magento 2 install dir>/pub/media`.

ただし、 *not* コピー `.htaccess` Magento1 のファイル `media` フォルダー。 Magento2 には独自の `.htaccess` それは保存するべきです。

## ストアフロントデザイン

* ファイルのデザイン (CSS、JS、テンプレート、 [XML](https://glossary.magento.com/xml) レイアウト ) の場所と形式を変更しました

* [レイアウト](https://glossary.magento.com/layout) データベースに保存された更新。 のMagento1 管理から配置 [CMS](https://glossary.magento.com/cms) ページ、CMS ウィジェット [カテゴリ](https://glossary.magento.com/category) ページと製品ページ

## アクセス制御リスト (ACL)

すべてを手動で再作成する必要があります。

* Web サービス API（SOAP、XML-RPC、および REST）の資格情報

* 管理ユーザーアカウントとアクセス権を関連付けます。

>[!NOTE]
>
>データベースエンティティのタイムゾーンは、 `\Migration\Handler\Timezone` ハンドラ 詳しくは、 [フォローアップ](follow-up.md) 」の節を参照してください。
