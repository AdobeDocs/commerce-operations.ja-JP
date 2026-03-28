---
title: 認証キーを取得
description: repo.magento.comでAdobe Commerce Composer パッケージにアクセスするための資格情報を取得するには、次の手順に従います。
exl-id: 7ec2a410-d81f-476a-bf6a-f3c61982a734
source-git-commit: 4a4fd51891b7a98529d00d51c94ed10429218726
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# 認証キーを取得

`repo.magento.com` リポジトリは、Adobe CommerceとサードパーティのComposer パッケージが保存され、認証が必要な場所です。 Commerce Marketplace アカウントを使用して、32文字の&#x200B;*認証キー*&#x200B;のペアを生成し、リポジトリにアクセスします。

Adobe Commerce パッケージへのアクセス権限を付与するには、これらのパッケージへのアクセス権が付与されたMAGEIDに関連付けられたキーを使用する必要があります。 MAGEIDは通常、Adobe Commerce アカウントのプライマリ連絡先であり、Adobe Commerce オンクラウドインフラストラクチャプロジェクトのプロジェクトオーナーではない場合があります。

>[!TIP]
>
>[ エラー](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html)が発生した場合、または「[!UICONTROL Access Keys]」セクションが「Marketplace」タブに表示されない場合、パッケージへのアクセス権限がないか、アカウントの未払いの請求書が原因でアクセス権限が期限切れになっている可能性があります。
>
>* アカウントのプライマリ連絡担当者である場合は、アカウントに未払いの請求書がリストされていないことを確認してください。
>* プライマリ担当者から提供されたキーが機能せず、アカウントに未払いの請求書がない場合、プライマリ担当者は[Adobe Commerce サポート ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)に連絡してサポートを受ける必要があります。

認証キーを作成するには：

>[!NOTE]
>
>2022年8月現在、アカウントオーナーはAdobe IDを持ち、そのアカウントがCommerce アカウントにリンクされていることを確認する必要があります。 アカウント所有者がAdobe IDを持っていない場合は、認証キーを生成する前に、アカウントを作成し、Commerce アカウントにリンクする必要があります。[Commerce アカウントを作成してアクセス ](https://experienceleague.adobe.com/en/docs/commerce-admin/start/commerce-account/commerce-account-create#create-a-commerce-account)

1. [Commerce Marketplace](https://commercemarketplace.adobe.com/)にログインします。 アカウントをお持ちでない場合は、**登録**&#x200B;をクリックしてください。

1. ページの右上にあるアカウント名をクリックし、**マイプロファイル**&#x200B;を選択します。

1. 「Marketplace」タブの「**アクセスキー**」をクリックします。

   ![Commerce Marketplaceで安全なアクセスキーを取得](../../assets/installation/cloud_access-key.png)

1. 「**新しいアクセスキーを作成**」をクリックします。 キーの特定の名前（キーを受け取る開発者の名前など）を入力し、**OK**&#x200B;をクリックします。

1. 新しい公開鍵と秘密鍵がアカウントに関連付けられました。これをクリックしてコピーできます。 この情報を保存するか、プロジェクトを操作するときにページを開いたままにします。 **公開鍵**&#x200B;をユーザー名として使用し、**秘密鍵**&#x200B;をパスワードとして使用します。

## 認証キーの管理

認証キーを無効にしたり削除したりすることもできます。 例えば、セキュリティ上の理由から、ユーザーが退社した後にキーを無効にしたり削除したりできます。

* キーを無効にするには：「**無効化**」をクリックします。 これは、キーの使用を一時停止する場合に実行できます。
* 以前に無効にしたキーを有効にするには：「**有効にする**」をクリックします。
* キーを削除するには：「**削除**」をクリックします。

### SSH アクセストークンの管理

SSHを使用してAdobe Commerce リリースをダウンロードするには、ダウンロードアクセストークンを生成する必要があります。 トークンを生成するには：

1. [magento.com アカウント ](https://account.magento.com/customer/account/login)にログインします。
1. ページの上部にある「**マイアカウント**」をクリックします。
1. **アカウント設定**/**アクセス トークンをダウンロード**&#x200B;をクリックします。

   ![ キーにアクセス ](../../assets/installation/connect_keys1.png)

1. 「**新しいトークンを生成**」をクリックして、既存のトークンを置き換えて無効にします。

リリースをダウンロードするには、MAGEIDとトークンを使用する必要があります。 MAGEIDは、アカウントページの左上に表示されます。

例：

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

認証キーを使用して、以下を行います。

* [メタパッケージの取得（インテグレーター、パッケージャー）](../composer.md)
* [GitHub リポジトリのクローンを作成](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository) （開発者限定）
* [モジュールのアップグレードと管理](../../upgrade/modules/upgrade.md)
