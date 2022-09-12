---
title: 認証キーの取得
description: repo.magento.com でAdobe CommerceおよびMagento Open Sourceコンポーザーパッケージにアクセスするための資格情報を取得するには、次の手順に従います。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---


# 認証キーの取得

この `repo.magento.com` リポジトリは、Adobe CommerceおよびMagento Open Sourceおよびサードパーティ Composer パッケージが格納され、認証が必要な場所です。 Commerce Marketplaceアカウントを使用して、32 文字のペアを生成します *認証キー* をクリックして、リポジトリにアクセスします。

>[!NOTE]
>
>Adobe CommerceおよびMagento Open Sourceパッケージへのアクセス権を付与するには、それらのパッケージへのアクセス権を付与された MAGEID に関連付けられたキーを使用する必要があります。 MAGEID は通常、 **請求連絡先** Adobe Commerceアカウント上で、常に **プロジェクト所有者** Adobe Commerce on cloud infrastructure プロジェクトの 次の場合に [エラー](https://support.magento.com/hc/en-us/articles/360040296392)の場合は、パッケージへのアクセス権限がないか、アカウント上の未処理の請求書が原因でアクセス権限が期限切れになっている可能性があります。 連絡先 [Adobe Commerceサポート](https://support.magento.com/hc/en-us) を参照してください。

認証キーを作成するには：

1. にログインします。 [Commerce Marketplace](https://marketplace.magento.com). アカウントがない場合は、 **登録**.
1. ページの右上にあるアカウント名をクリックし、「 」を選択します。 **マイプロファイル**.

1. クリック **アクセスキー** 」と入力します。

   ![セキュリティで保護されたアクセスキーをCommerce Marketplace](../../assets/installation/cloud_access-key.png)

1. クリック **新しいアクセスキーを作成**. キーの特定の名前（例えば、キーを受け取った開発者の名前）を入力し、「 」をクリックします。 **OK**.

1. 新しい公開鍵と秘密鍵がアカウントに関連付けられ、クリックしてコピーできます。 プロジェクトで作業する際は、この情報を保存するか、ページを開いたままにします。 以下を使用： **公開鍵** ユーザー名と **秘密鍵** を設定します。

## 認証キーの管理

また、認証キーを無効にしたり削除したりすることもできます。 例えば、誰かが組織を離れた後のセキュリティ上の理由で、キーを無効にしたり削除したりできます。

* キーを無効にするには：クリック **無効にする**. これは、キーの使用を中止する場合に実行できます。
* 以前に無効にしたキーを有効にするには：クリック **有効にする**.
* キーを削除するには：クリック **削除**.

### SSH アクセストークンを管理

SSH を使用してAdobe Commerceリリースをダウンロードするには、ダウンロードアクセストークンを生成する必要があります。 トークンを生成するには：

1. にログインします。 [magento.com アカウント](https://account.magento.com/customer/account/login).
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