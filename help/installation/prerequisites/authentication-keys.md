---
title: 認証キーの取得
description: 次の手順に従って、repo.magento.comでAdobe Commerceおよび Composer パッケージにアクセスするための資格情報を取得します。Magento Open Source
exl-id: 7ec2a410-d81f-476a-bf6a-f3c61982a734
source-git-commit: 3d9b7c5352f91308dd315a7195ee2cb1c4b191ee
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---

# 認証キーの取得

The `repo.magento.com` リポジトリは、Adobe CommerceおよびMagento Open Sourceおよびサードパーティ Composer パッケージが格納され、認証が必要な場所です。 Commerce Marketplaceアカウントを使用して、32 文字のペアを生成します。 *認証キー* をクリックして、リポジトリにアクセスします。

Adobe CommerceおよびMagento Open Sourceパッケージへのアクセス権を付与するには、それらのパッケージへのアクセス権を付与された MAGEID に関連付けられたキーを使用する必要があります。 MAGEID は通常、Adobe Commerceアカウントのプライマリ連絡先で、クラウドインフラストラクチャプロジェクトのAdobe Commerceのプロジェクト所有者とは限りません。

>[!TIP]
>
>次に遭遇した場合 [エラー](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html)の場合は、パッケージへのアクセス権限がないか、アカウント上の未処理の請求書が原因でアクセス権限が期限切れになっている可能性があります。
>
>* アカウントのプライマリ連絡先担当者の場合は、アカウントに未処理の請求書が一覧に表示されていないことを確認します。
>* プライマリ連絡先が提供するキーが機能せず、アカウントに未処理の請求書がない場合は、担当者にお問い合わせください。 [Adobe Commerceサポート](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) プライマリ連絡先の MAGEID の使用に関するサポート

認証キーを作成するには：

1. にログインします。 [Commerce Marketplace](https://commercemarketplace.adobe.com/). アカウントがない場合は、 **登録**.

1. ページの右上にあるアカウント名をクリックし、「 」を選択します。 **マイプロファイル**.

1. クリック **アクセスキー** 」と入力します。

   ![セキュリティで保護されたアクセスキーをCommerce Marketplace](../../assets/installation/cloud_access-key.png)

1. クリック **新しいアクセスキーを作成**. キーの特定の名前（例えば、キーを受け取った開発者の名前）を入力し、「 」をクリックします。 **OK**.

1. 新しい公開鍵と秘密鍵がアカウントに関連付けられ、クリックしてコピーできます。 プロジェクトで作業する際は、この情報を保存するか、ページを開いたままにします。 以下を使用します。 **公開鍵** ユーザー名と **秘密鍵** を設定します。

## 認証キーの管理

また、認証キーを無効にしたり削除したりすることもできます。 例えば、誰かが組織を離れた後のセキュリティ上の理由で、キーを無効にしたり削除したりできます。

* キーを無効にするには： **無効にする**. これは、キーの使用を中止する場合に実行できます。
* 以前に無効にしたキーを有効にするには： **有効にする**.
* キーを削除するには： **削除**.

### SSH アクセストークンを管理

SSH を使用してAdobe CommerceおよびMagento Open Sourceリリースをダウンロードするには、ダウンロードアクセストークンを生成する必要があります。 トークンを生成するには：

1. にログインします。 [magento.comアカウント](https://account.magento.com/customer/account/login).
1. クリック **マイアカウント** をクリックします。
1. クリック **アカウント設定** > **ダウンロードアクセストークン**.

   ![キーにアクセス](../../assets/installation/connect_keys1.png)

1. クリック **新規トークンを生成** をクリックして、既存のトークンを置き換えたり、無効にしたりします。

リリースをダウンロードするには、MAGEID とトークンを使用する必要があります。 MAGEID がアカウントページの左上に表示されます。

例：

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

認証キーを使用して、次の操作を実行できます。

* [メタパッケージの取得（インテグレーター、パッケージャー）](../composer.md)
* [GitHub リポジトリのクローン](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) （開発者のみ）
* [モジュールのアップグレードと管理](../../upgrade/modules/upgrade.md)
