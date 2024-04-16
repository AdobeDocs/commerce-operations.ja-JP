---
title: Adobeプライバシー JavaScript ライブラリ
description: カスタムツールを使用して、Adobe Commerceで収集されたお客様の個人情報にアクセスして削除する方法を説明します。
hide: true
hidefromtoc: true
exl-id: 5080e03b-0a83-405c-a232-b93311e284a3
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Adobeプライバシー JavaScript ライブラリ

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

この [Adobeプライバシー JavaScript ライブラリ](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html) は、非公開データにアクセスして削除するプロセスを作成するのに役立つツールのセットです。

Adobe Commerce データトラッキングサービスでは、次のようなプライバシー規制に適用される個人情報を保存できます [EU 一般データ保護規則（GDPR）](gdpr.md) および [カリフォルニア州消費者プライバシー法（CCPA）](ccpa.md).

このライブラリは、プライバシーデータリクエストの作成、各製品の実装への送信、応答の収集のための統合された機能セットを提供します。 このライブラリを使用して、これらのデータトラッキングサービスによってブラウザーに保存されたデータを取得および削除します。

## インストール

次のいずれかの方法を使用して、ライブラリファイルをダウンロードします。

- npm: `npm install @adobe/adobe-privacy`
- GitHub: [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

ファイルを取得したら、Adobe Commerce インスタンスにインストールされたカスタムモジュールまたはテーマにファイルを追加する必要があります。 に記載されている指示に従います [カスタム JavaScript の使用](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) このタスクを実行するトピック。

## 使用方法

AdobePrivacy JS ライブラリは、ブラウザーに保存された ID データを管理するための様々な機能を提供します。

`retrieveIdentities()`
：サービスから ID の配列を、サービスで見つからない ID の配列と共に返します

`removeIdentities()`
：ブラウザーから ID を削除し、ID オブジェクトの配列をで返します。 `isDeleteClientSide` データが削除されたかどうかを示すブール値プロパティ。

`retrieveThenRemoveIdentities()`
：この関数は次の関数に類似しています `removeIdentities()` その点で、ID の配列を取得し、ブラウザーから削除します。

これらの関数の詳細と使用例については、を参照してください [公式ライブラリドキュメント](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html).

### 初期化

新しいのインスタンス化 `AdobePrivacy` 実装コードで AdobePrivacy JS ライブラリを使用するオブジェクトです。

```js
var adobePrivacy = new AdobePrivacy({});
```

このコンストラクターは、インスタンス化の際に、パラメーターを含んだ設定オブジェクトを受け入れます。
を参照してください。 [公式ライブラリドキュメント](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html) これらの設定パラメーターのリスト。
