---
title: 認証キーの取得
description: repo.magento.comでAdobe Commerce Composer パッケージにアクセスするための資格情報を取得するには、次の手順に従います。
exl-id: 7ec2a410-d81f-476a-bf6a-f3c61982a734
source-git-commit: fc63ca58cd2ff7c5ec597751980a39bfbe68aa5f
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# 認証キーの取得

この `repo.magento.com` リポジトリーは、Adobe Commerceおよびサードパーティの Composer パッケージが格納される場所であり、認証が必要です。 Commerce Marketplaceアカウントを使用して、32 文字のペアを生成します *認証キー* をクリックしてリポジトリにアクセスします。

Adobe Commerce パッケージへのアクセス権を付与するには、これらのパッケージへのアクセス権が付与された MAGEID に関連付けられたキーを使用する必要があります。 MAGEID は、通常Adobe Commerce アカウントのプライマリ連絡先となり、Adobe Commerce on cloud インフラストラクチャプロジェクトのプロジェクトオーナーであるとは限りません。

>[!TIP]
>
>次に遭遇した場合： [エラー](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html)、パッケージにアクセスする権限がない、またはアカウントの未払い請求書が原因でアクセス権限が期限切れになっている可能性があります。
>
>* アカウントのプライマリ担当者の場合は、アカウントに未払いの請求書がリストされていないことを確認してください。
>* プライマリ担当者から提供されたキーが機能せず、アカウントに未払いの請求書がない場合は、プライマリ担当者が連絡する必要があります [Adobe Commerce サポート](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) お手伝いさせていただきます。

認証キーを作成するには：

1. にログインします [Commerce Marketplace](https://commercemarketplace.adobe.com/). アカウントがない場合は、 **登録**.

1. ページの右上にあるアカウント名をクリックし、以下を選択します。 **マイプロファイル**.

1. クリック **アクセスキー** 「Marketplace」タブで、次の操作を行います。

   ![Commerce Marketplaceで安全なアクセスキーを入手](../../assets/installation/cloud_access-key.png)

1. クリック **新しいアクセスキーの作成**. キーの特定の名前（キーを受け取る開発者の名前など）を入力し、 **OK**.

1. 新しい公開鍵と秘密鍵がアカウントに関連付けられ、クリックしてコピーできるようになりました。 プロジェクトを操作する際は、この情報を保存するか、ページを開いたままにします。 の使用 **公開鍵** ユーザー名としておよび **秘密鍵** をパスワードとして使用します。

## 認証キーの管理

また、認証キーを無効にしたり削除したりすることもできます。 例えば、組織を離れた後に、セキュリティ上の理由からキーを無効にしたり削除したりできます。

* キーを無効にするには：クリック **無効**. これは、キーの使用を一時停止する場合に実行できます。
* 以前に無効にしたキーを有効にするには：クリックします **Enable （有効）**.
* キーを削除するには：クリックします **削除**.

### SSH アクセストークンの管理

SSH を使用してAdobe Commerce リリースをダウンロードするには、ダウンロードアクセストークンを生成する必要があります。 トークンを生成するには、次の手順に従います。

1. にログイン [magento.com アカウント](https://account.magento.com/customer/account/login).
1. クリック **マイアカウント** ページの上部
1. クリック **アカウント設定** > **アクセストークンのダウンロード**.

   ![キーへのアクセス](../../assets/installation/connect_keys1.png)

1. クリック **新しいトークンの生成** 既存のトークンの置換および無効化

リリースをダウンロードするには、MAGEID とトークンを使用する必要があります。 Mageid はアカウントページの左上に表示されます。

例：

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

認証キーを使用して、次のことを行います。

* [メタパッケージを入手（インテグレーター、パッケージャ）](../composer.md)
* [GitHub リポジトリのクローン](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) （コントリビューション開発者のみ）
* [モジュールのアップグレードと管理](../../upgrade/modules/upgrade.md)
