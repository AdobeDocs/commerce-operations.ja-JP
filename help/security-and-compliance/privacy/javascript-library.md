---
title: プライバシーJavaScript ライブラリ
description: カスタムツールを使用して、Adobe Commerceで収集されたお客様の個人情報にアクセスして削除する方法を説明します。
exl-id: bcfea656-2cf0-48ae-9049-d91679166d05
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# プライバシーJavaScript ライブラリ

プライバシーJavaScript ライブラリは、Adobe Commerceで収集された非公開データにアクセスして削除するプロセスを作成するためのツールセットです。

Commerceのデータトラッキングサービスでは、[EU 一般データ保護規則（GDPR） ](gdpr.md) および [ カリフォルニア州消費者プライバシー法（CCPA） ](ccpa.md) などのプライバシー規制に適用される個人情報を保存できます。

このライブラリは、プライバシーデータリクエストを作成し、その応答を収集するための一連の機能を提供します。 このライブラリを使用すると、Adobe Commerce データトラッキングサービスによってブラウザーに保存されているデータを取得および削除できます。

>[!NOTE]
>
>[Cookie 制限モード ](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html?lang=ja) が有効になっている場合、Commerceは、買い物客が同意するまで行動データを収集しません。 [!UICONTROL **Cookie 制限モード**] が無効になっている場合、Commerceはデフォルトで行動データを収集します。

## インストール

Privacy JavaScript ライブラリは、次の CDN の場所で利用できます。`commerce.adobe.net/magentoprivacy.js`

ファイルを取得したら、Adobe Commerce インスタンスにインストールされたカスタムモジュールまたはテーマにファイルを追加する必要があります。 このタスクを実行するには、「[ カスタム JavaScriptの使用 ](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) トピックに記載されている手順に従います。

### 初期化

新しい `MagentoPrivacy` オブジェクトをインポートしてインスタンス化するか、`window` オブジェクトを使用して Privacy のJavaScript関数にアクセスします。

`import` の使用例：

```js
import MagentoPrivacy from "./MagentoPrivacy"

const magePriv = new MagentoPrivacy()
```

`window` の使用例：

```js
const magePriv = new window.MagentoPrivacy()
```

## 使用方法

プライバシー JS ライブラリは、ブラウザーに保存された ID データを管理するための様々な機能を提供します。

`retrieveIdentity()`
：ブラウザーのサービスから、ID オブジェクトのJavaScript プロミスを返します。

```js
magePriv.retrieveIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3"}
```

`removeIdentity()`
：ブラウザーのサービスから ID データを削除します。
この関数は、データが削除されたかどうかを示す `isDeleted` のブール値プロパティを持つ ID オブジェクトのJavaScript promise を返します。

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
