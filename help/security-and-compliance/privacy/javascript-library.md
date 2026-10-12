---
title: Privacy JavaScript Library
description: Adobe Commerceで収集したお客様の個人情報にアクセスして削除するためのカスタムツールの使用方法について説明します。
exl-id: bcfea656-2cf0-48ae-9049-d91679166d05
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
source-wordcount: '287'
ht-degree: 0%
---
<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# Privacy JavaScript Library

Privacy JavaScript Libraryは、Adobe Commerceによって収集されたプライベートデータにアクセスして削除するためのプロセスを構築するのに役立つ一連のツールです。

Commerce データトラッキングサービスは、[一般データ保護規則（GDPR） &#x200B;](gdpr.md)および[&#x200B; カリフォルニア州消費者プライバシー法（CCPA） &#x200B;](ccpa.md)などのプライバシー規制に適用される個人情報を保存できます。

このライブラリは、プライバシーデータリクエストを作成し、その応答を収集するための一連の機能を提供します。 このライブラリを使用すると、Adobe Commerce データトラッキングサービスによってブラウザーに保存されているデータを取得および削除できます。

>[!NOTE]
>
>[Cookie制限モード &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html?lang=ja)が有効になっている場合、買い物客が同意するまでCommerceは行動データを収集しません。 [!UICONTROL **Cookie制限モード**]&#x200B;が無効になっている場合、Commerceはデフォルトで行動データを収集します。

## インストール

Privacy JavaScript ライブラリは、次のCDNの場所で利用できます：`commerce.adobe.net/magentoprivacy.js`

ファイルを用意したら、Adobe Commerce インスタンスにインストールされているカスタムモジュールまたはテーマにファイルを追加する必要があります。 「[&#x200B; カスタム JavaScriptを使用](https://developer.adobe.com/commerce/frontend-core/javascript/custom)」のトピックに記載されている手順に従って、このタスクを実行します。

### 初期化

新しい`MagentoPrivacy` オブジェクトを読み込んでインスタンス化するか、`window` オブジェクトを使用してPrivacy JavaScript関数にアクセスします。

`import`を使用する例：

```js
import MagentoPrivacy from "./MagentoPrivacy"

const magePriv = new MagentoPrivacy()
```

`window`を使用する例：

```js
const magePriv = new window.MagentoPrivacy()
```

## 使用状況

プライバシーJS ライブラリには、ブラウザーに保存されているID データを管理するための様々な機能が用意されています。

`retrieveIdentity()`
：ブラウザーのサービスからID オブジェクトのJavaScript Promiseを返します。

```js
magePriv.retrieveIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3"}
```

`removeIdentity()`
：ブラウザーのサービスからID データを削除します。
この関数は、データが削除されたかどうかを示す`isDeleted` ブール値プロパティを持つID オブジェクトに対するJavaScript Promiseを返します。

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
