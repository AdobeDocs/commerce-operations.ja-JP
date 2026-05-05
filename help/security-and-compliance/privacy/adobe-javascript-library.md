---
title: Adobe Privacy JavaScript Library
description: Adobe Commerceで収集したお客様の個人情報にアクセスして削除するためのカスタムツールの使用方法について説明します。
hide: true
hidefromtoc: true
exl-id: 5080e03b-0a83-405c-a232-b93311e284a3
source-git-commit: f6f690af56df3de737a9f72c2e727b1752bc94b3
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# Adobe Privacy JavaScript Library

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

[Adobe プライバシーJavaScript ライブラリ &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html)は、プライベートデータへのアクセスと削除のプロセスを作成するのに役立つ一連のツールです。

Adobe Commerce データトラッキングサービスは、[一般データ保護規則（GDPR） &#x200B;](gdpr.md)および[&#x200B; カリフォルニア州消費者プライバシー法（CCPA） &#x200B;](ccpa.md)などのプライバシー規制に適用される個人情報を保存できます。

このライブラリは、プライバシーデータリクエストを作成し、各製品の実装に送信し、応答を収集するための統合された機能セットを提供します。 このライブラリを使用して、これらのデータトラッキングサービスによってブラウザーに保存されているデータを取得および削除します。

## インストール

ライブラリファイルをダウンロードするには、次のいずれかの方法を使用します。

- npm: `npm install @adobe/adobe-privacy`
- GitHub: [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

ファイルを用意したら、Adobe Commerce インスタンスにインストールされているカスタムモジュールまたはテーマにファイルを追加する必要があります。 「[&#x200B; カスタム JavaScriptを使用](https://developer.adobe.com/commerce/frontend-core/javascript/custom)」のトピックに記載されている手順に従って、このタスクを実行します。

## 使用状況

AdobePrivacy JS ライブラリには、ブラウザーに保存されているID データを管理するための様々な機能が用意されています。

`retrieveIdentities()`
：サービスからIDの配列と、サービスに見つからないIDの配列を返します

`removeIdentities()`
：ブラウザーからIDを削除し、データが削除されたかどうかを示す`isDeleteClientSide` ブール型プロパティを持つID オブジェクトの配列を返します。

`retrieveThenRemoveIdentities()`
：この関数は、IDの配列を取得してブラウザーから削除するという点で`removeIdentities()`と似ています。

これらの関数の使用方法と例について詳しくは、[公式ライブラリドキュメント &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html)を参照してください。

### 初期化

実装コードでAdobePrivacy JS ライブラリを使用する新しい`AdobePrivacy` オブジェクトをインスタンス化します。

```js
var adobePrivacy = new AdobePrivacy({});
```

コンストラクターは、インスタンス化中にパラメーターを含む設定オブジェクトを受け入れます。
これらの設定パラメーターのリストについては、[公式ライブラリドキュメント &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html)を参照してください。
