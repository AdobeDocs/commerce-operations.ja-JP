---
title: Adobeプライバシー JavaScript ライブラリ
description: Adobe CommerceおよびMagento Open Sourceが収集した顧客の個人情報にアクセスし削除するためのカスタムツールの使用方法を説明します。
hide: true
hidefromtoc: true
exl-id: 5080e03b-0a83-405c-a232-b93311e284a3
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# Adobeプライバシー JavaScript ライブラリ

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

The [Adobeプライバシー JavaScript ライブラリ](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) は、プライベートデータにアクセスして削除するためのプロセスを作成するのに役立つ一連のツールです。

Adobe CommerceおよびMagento Open Sourceデータトラッキングサービスは、 [一般データ保護規則 (GDPR)](gdpr.md) および [カリフォルニア州消費者プライバシー法 (CCPA)](ccpa.md).

このライブラリは、プライバシーデータリクエストを作成し、各製品の実装に送信し、応答を収集するための統合された関数セットを提供します。 このライブラリを使用して、これらのデータトラッキングサービスによってブラウザーに保存されているデータを取得および削除します。

## インストール

次のいずれかの方法を使用して、ライブラリファイルをダウンロードします。

- npm: `npm install @adobe/adobe-privacy`
- GitHub: [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

ファイルを作成したら、Adobe CommerceおよびMagento Open Sourceインスタンスにインストールされているカスタムモジュールまたはテーマに追加する必要があります。 次に示す手順に従います： [カスタム JavaScript を使用](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) このタスクを完了するためのトピックです。

## 使用状況

AdobePrivacy JS ライブラリは、ブラウザーに保存された ID データを管理するための様々な機能を提供します。

`retrieveIdentities()`
：サービスから ID の配列と、サービスで見つからない ID の配列を戻します

`removeIdentities()`
:ID をブラウザーから削除し、ID オブジェクトの配列を `isDeleteClientSide` データが削除されたかどうかを示す boolean プロパティです。

`retrieveThenRemoveIdentities()`
：この関数は、に似ています。 `removeIdentities()` では、id の配列を取得し、ブラウザーから削除します。

これらの関数の詳細と使用例については、 [公式ライブラリドキュメント](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html).

### 初期化

新しいのインスタンス化 `AdobePrivacy` オブジェクトを使用して、実装コードで AdobePrivacy JS Library を使用します。

```js
var adobePrivacy = new AdobePrivacy({});
```

このコンストラクタは、インスタンス化中にパラメーターを持つ設定オブジェクトを受け入れます。
詳しくは、 [公式ライブラリドキュメント](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) を参照してください。
