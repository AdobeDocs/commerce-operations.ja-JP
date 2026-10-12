---
title: 手作業による移行が必要なデータ
description: Magento 1からMagento 2へのデータ移行時に手動で移行する必要があるデータとその方法について説明します。
exl-id: 830abd81-4c6d-418b-9da4-b6acd95f5ec8
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 0%
---
# 手作業による移行が必要なデータ

手動で移行する必要があるデータには、次の4つの種類があります。

* メディア

* ストアフロントデザイン

* 管理者ユーザーアカウント

* アクセス制御リスト（ACL）

## メディア

この節では、メディアファイルを手動で移行する方法について説明します。

### データベースに保存されているメディアファイル

>[!WARNING]
>
>Magento 2.4.3では、データベースメディアストレージメソッドは推奨されません。


このセクションは、Magento データベースにメディアファイルを保存する場合にのみ&#x200B;*適用されます。* この手順は、[ データの移行](data.md)の前に実行する必要があります：

1. 管理者としてMagento 1管理パネルにログインします。

1. **システム**/**設定**/詳細/**システム**&#x200B;をクリックします。

1. 右側のペインで、**Storage Configuration for Media**&#x200B;までスクロールします。

1. 「**メディア データベースを選択**」リストから、メディア ストレージ データベースの名前をクリックします。

1. 「**同期**」をクリックします。

次に、Magento 2管理パネルで同じ手順を繰り返します。

### ファイルシステム内のメディアファイル

すべてのメディアファイル （製品、カテゴリ、WYSIWYG エディターなどの画像）は、`<your Magento 1 install dir>/media`から`<your Magento 2 install dir>/pub/media`まで手動でコピーする必要があります。

ただし、Magento 1 `media` フォルダーにある`.htaccess` ファイルは、*not*&#x200B;でコピーしてください。 Magento 2には、保存する必要がある独自の`.htaccess`があります。

## ストアフロントデザイン

* ファイル（CSS、JS、テンプレート、XML レイアウト）のデザインにより、場所と形式が変更された

* データベースに保存されたレイアウト更新。 CMSページ、CMSウィジェット、カテゴリーページ、商品ページで、Magento 1管理者を介して配置

## アクセス制御リスト（ACL）

手動ですべてを再作成する必要があります：

* web サービス API （SOAP、XML-RPC、REST）の資格情報

* 管理ユーザーアカウントを作成し、アクセス権限に関連付ける

>[!NOTE]
>
>`\Migration\Handler\Timezone` ハンドラーを使用して、データベースエンティティのタイムゾーンを調整できます。 詳しくは、[ フォローアップ ](follow-up.md)の節を参照してください。
