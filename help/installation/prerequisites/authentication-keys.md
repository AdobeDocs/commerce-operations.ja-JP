---
title: 認証キーの取得
description: repo.magento.comでAdobe Commerce Composer パッケージにアクセスするための資格情報を取得するには、次の手順に従います。
exl-id: 7ec2a410-d81f-476a-bf6a-f3c61982a734
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# 認証キーの取得

`repo.magento.com` リポジトリーには、Adobe Commerceとサードパーティの Composer パッケージが格納され、認証が必要です。 Commerce Marketplace アカウントを使用して、32 文字の *認証キー* のペアを生成し、リポジトリにアクセスします。

Adobe Commerce パッケージへのアクセス権を付与するには、これらのパッケージへのアクセス権が付与された MAGEID に関連付けられたキーを使用する必要があります。 MAGEID は、通常Adobe Commerce アカウントのプライマリ連絡先となり、Adobe Commerce on cloud インフラストラクチャプロジェクトのプロジェクトオーナーであるとは限りません。

>[!TIP]
>
>[&#x200B; エラー &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html?lang=ja) が発生した場合や、「Marketplace」タブに「[!UICONTROL Access Keys]」セクションが表示されない場合は、パッケージにアクセスする権限がない可能性があります。または、アカウントの未払い請求書が原因でアクセス権限が期限切れになっている可能性があります。
>
>* アカウントのプライマリ担当者の場合は、アカウントに未払いの請求書がリストされていないことを確認してください。
>* プライマリ担当者が提供したキーが機能せず、アカウントに未払いの請求書がない場合は、プライマリ担当者が [Adobe Commerce サポート &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=ja#submit-ticket) に問い合わせる必要があります。

認証キーを作成するには：

1. [Commerce Marketplace](https://commercemarketplace.adobe.com/) にログインします。 アカウントをお持ちでない場合は、「**登録**」をクリックします。

1. ページ右上のアカウント名をクリックし、「**マイプロファイル**」を選択します。

1. 「Marketplace」タブの **アクセスキー** をクリックします。

   ![Commerce Marketplaceの安全なアクセスキーの取得 &#x200B;](../../assets/installation/cloud_access-key.png)

1. **新しいアクセスキーを作成** をクリックします。 キーの特定の名前（キーを受け取る開発者の名前など）を入力し、[**OK**] をクリックします。

1. 新しい公開鍵と秘密鍵がアカウントに関連付けられ、クリックしてコピーできるようになりました。 プロジェクトを操作する際は、この情報を保存するか、ページを開いたままにします。 ユーザー名として **公開鍵** を使用し、パスワードとして **秘密鍵** を使用します。

## 認証キーの管理

また、認証キーを無効にしたり削除したりすることもできます。 例えば、組織を離れた後に、セキュリティ上の理由からキーを無効にしたり削除したりできます。

* キーを無効にするには：**無効** をクリックします。 これは、キーの使用を一時停止する場合に実行できます。
* 以前に無効にしたキーを有効にするには：**有効** をクリックします。
* キーを削除するには：**削除** をクリックします。

### SSH アクセストークンの管理

SSH を使用してAdobe Commerce リリースをダウンロードするには、ダウンロードアクセストークンを生成する必要があります。 トークンを生成するには、次の手順に従います。

1. [magento.com アカウント &#x200B;](https://account.magento.com/customer/account/login) にログインします。
1. ページ上部の **マイアカウント** をクリックします。
1. **アカウント設定**/**アクセストークンをダウンロード** をクリックします。

   ![&#x200B; キーへのアクセス &#x200B;](../../assets/installation/connect_keys1.png)

1. 「**新しいトークンの生成**」をクリックし、既存のトークンを置き換えて無効にします。

リリースをダウンロードするには、MAGEID とトークンを使用する必要があります。 Mageid はアカウントページの左上に表示されます。

例：

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

認証キーを使用して、次のことを行います。

* [メタパッケージを入手（インテグレーター、パッケージャ）](../composer.md)
* [GitHub リポジトリのクローンを作成 &#x200B;](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository) （投稿開発者のみ）
* [モジュールのアップグレードと管理](../../upgrade/modules/upgrade.md)
