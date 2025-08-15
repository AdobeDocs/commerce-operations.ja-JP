---
title: Adobe プライバシーJavaScript ライブラリ
description: カスタムツールを使用して、Adobe Commerceで収集されたお客様の個人情報にアクセスして削除する方法を説明します。
hide: true
hidefromtoc: true
exl-id: 5080e03b-0a83-405c-a232-b93311e284a3
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Adobe プライバシーJavaScript ライブラリ

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

[Adobe Privacy JavaScript ライブラリ ](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html?lang=ja) は、非公開データへのアクセスおよび削除プロセスを作成するのに役立つ一連のツールです。

Adobe Commerceのデータトラッキングサービスでは、[EU 一般データ保護規則（GDPR） ](gdpr.md) および [ カリフォルニア州消費者プライバシー法（CCPA） ](ccpa.md) などのプライバシー規制に適用される個人情報を保存できます。

このライブラリは、プライバシーデータリクエストの作成、各製品の実装への送信、応答の収集のための統合された機能セットを提供します。 このライブラリを使用して、これらのデータトラッキングサービスによってブラウザーに保存されたデータを取得および削除します。

## インストール

次のいずれかの方法を使用して、ライブラリファイルをダウンロードします。

- npm: `npm install @adobe/adobe-privacy`
- GitHub: [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

ファイルを取得したら、Adobe Commerce インスタンスにインストールされたカスタムモジュールまたはテーマにファイルを追加する必要があります。 このタスクを実行するには、「[ カスタム JavaScriptの使用 ](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) トピックに記載されている手順に従います。

## 使用状況

AdobePrivacy JS ライブラリは、ブラウザーに保存された ID データを管理するための様々な機能を提供します。

`retrieveIdentities()`
：サービスから ID の配列を、サービスで見つからない ID の配列と共に返します

`removeIdentities()`
：ブラウザーから ID を削除し、データが削除されたかどうかを示す `isDeleteClientSide` のブール値プロパティを含む、ID オブジェクトの配列を返します。

`retrieveThenRemoveIdentities()`
：この関数は、ID の配列を取得し、ブラウザーから削除するという点で `removeIdentities()` と似ています。

これらの関数の使用方法と例について詳しくは、[ 公式ライブラリドキュメント ](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html?lang=ja) を参照してください。

### 初期化

新しい `AdobePrivacy` オブジェクトをインスタンス化して、実装コードで AdobePrivacy JS ライブラリを使用します。

```js
var adobePrivacy = new AdobePrivacy({});
```

このコンストラクターは、インスタンス化の際に、パラメーターを含んだ設定オブジェクトを受け入れます。
これらの設定パラメーターのリストについては、[ 公式ライブラリドキュメント ](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html?lang=ja) を参照してください。
