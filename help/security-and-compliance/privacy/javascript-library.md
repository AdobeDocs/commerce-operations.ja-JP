---
title: プライバシー JavaScript ライブラリ
description: Adobe CommerceおよびMagento Open Sourceが収集した顧客の個人情報にアクセスし削除するためのカスタムツールの使用方法を説明します。
source-git-commit: 1a608e8a5986026d5a187dc8cbd358fed2db5d9e
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---


<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# プライバシー JavaScript ライブラリ

プライバシー JavaScript ライブラリは、Adobe CommerceおよびMagento Open Sourceが収集したプライベートデータにアクセスし削除するプロセスを作成するのに役立つ一連のツールです。

コマースデータトラッキングサービスは、 [一般データ保護規則 (GDPR)](gdpr.md) および [カリフォルニア州消費者プライバシー法 (CCPA)](ccpa.md).

このライブラリは、プライバシーデータリクエストを作成し、その応答を収集するための一連の関数を提供します。 このライブラリを使用して、Adobe CommerceおよびMagento Open Sourceデータトラッキングサービスによってブラウザーに保存されているデータを取得および削除します。

>[!NOTE]
>
>If [Cookie 制限モード](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) が有効になっている場合、Commerce は買い物客が同意するまで行動データを収集しません。 If [!UICONTROL **Cookie 制限モード**] が無効の場合、Commerce はデフォルトで行動データを収集します。

## インストール

プライバシー JavaScript ライブラリは、次の CDN の場所で利用できます。 `commerce.adobe.net/magentoprivacy.js`

ファイルを作成したら、Adobe CommerceまたはMagento Open Sourceインスタンスにインストールされているカスタムモジュールまたはテーマに追加する必要があります。 次に示す手順に従います： [カスタム JavaScript を使用](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) このタスクを完了するためのトピックです。

### 初期化

新しいをインポートしてインスタンス化する `MagentoPrivacy` オブジェクトまたは `window` オブジェクトを使用して、Privacy JavaScript 関数にアクセスします。

使用例 `import`:

```js
import MagentoPrivacy from "./MagentoPrivacy"

const magePriv = new MagentoPrivacy()
```

使用例 `window`:

```js
const magePriv = new window.MagentoPrivacy()
```

## 使用状況

プライバシー JS ライブラリは、ブラウザーに保存された ID データを管理するための様々な関数を提供します。

`retrieveIdentity()`
:ブラウザーのサービスから ID オブジェクトの JavaScript プロミスを返します。

```js
magePriv.retrieveIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3"}
```

`removeIdentity()`
:ブラウザーのサービスから ID データを削除します。
この関数は、 `isDeleted` データが削除されたかどうかを示す boolean プロパティです。

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
