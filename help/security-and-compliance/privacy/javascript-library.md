---
title: プライバシー JavaScript ライブラリ
description: カスタムツールを使用して、Adobe Commerceで収集されたお客様の個人情報にアクセスして削除する方法を説明します。
exl-id: bcfea656-2cf0-48ae-9049-d91679166d05
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# プライバシー JavaScript ライブラリ

プライバシー JavaScript ライブラリは、Adobe Commerceで収集された非公開データにアクセスして削除するプロセスを作成するためのツールセットです。

Commerce データトラッキングサービスでは、次のようなプライバシー規制に適用される個人情報を保存できます [EU 一般データ保護規則（GDPR）](gdpr.md) および [カリフォルニア州消費者プライバシー法（CCPA）](ccpa.md).

このライブラリは、プライバシーデータリクエストを作成し、その応答を収集するための一連の機能を提供します。 このライブラリを使用すると、Adobe Commerce データトラッキングサービスによってブラウザーに保存されているデータを取得および削除できます。

>[!NOTE]
>
>次の場合 [Cookie 制限モード](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) を有効にすると、買い物客が同意するまでCommerceは行動データを収集しません。 次の場合 [!UICONTROL **Cookie 制限モード**] が無効の場合、Commerceはデフォルトで行動データを収集します。

## インストール

プライバシー JavaScript ライブラリは、次の CDN の場所で利用できます。 `commerce.adobe.net/magentoprivacy.js`

ファイルを取得したら、Adobe CommerceまたはMagento Open Sourceインスタンスにインストールされたカスタムモジュールまたはテーマにファイルを追加する必要があります。 に記載されている指示に従います [カスタム JavaScript の使用](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) このタスクを実行するトピック。

### 初期化

新しいをインポートしてインスタンス化します。 `MagentoPrivacy` オブジェクトまたは使用 `window` プライバシー JavaScript 関数にアクセスするオブジェクト。

の使用例 `import`:

```js
import MagentoPrivacy from "./MagentoPrivacy"

const magePriv = new MagentoPrivacy()
```

の使用例 `window`:

```js
const magePriv = new window.MagentoPrivacy()
```

## 使用方法

プライバシー JS ライブラリは、ブラウザーに保存された ID データを管理するための様々な機能を提供します。

`retrieveIdentity()`
：ブラウザーのサービスから、ID オブジェクトの JavaScript プロミスを返します。

```js
magePriv.retrieveIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3"}
```

`removeIdentity()`
：ブラウザーのサービスから ID データを削除します。
この関数は、以下を持つ ID オブジェクトの JavaScript プロミスを返します。 `isDeleted` データが削除されたかどうかを示すブール値プロパティ。

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
