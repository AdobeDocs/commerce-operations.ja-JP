---
title: ACSD-63244：レンダリングやコンソールエラーを含む、管理パネルのJavaScript [!DNL Google Maps]  問題を解決します
description: ACSD-63244 パッチは、レンダリングと繰り返しの「Uncaught TypeError this」に関する問題など、管理パネルの複数のJavaScriptの問題を修正し  [!DNL Google Maps]  す。ブラウザーコンソールの各エラーが関数エラーではありません（_e）。
feature: Admin Workspace
role: Admin, Developer
exl-id: 1985c845-219e-4af4-8f70-62dd57722494
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# ACSD-63244:[!DNL Google Maps] レンダリングやコンソールエラーなど、管理パネルのJavaScriptの問題を解決します

ACSD-63244 パッチは、ブラウザーコンソールでの [!DNL Google Maps] レンダリングや繰り返し `Uncaught TypeError: this._each is not a function` エラーの問題など、管理パネルに表示される複数のJavaScriptの問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 で使用できます。パッチ ID は ACSD-63244 です。 この問題はAdobe Commerce 2.4.8 で修正される予定だったことに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4、2.4.4-p9、2.4.6-p7、2.4.7

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

* ブラウザーコンソールに `Uncaught TypeError: this._each is not a function` エラーが表示され、管理 UI 機能が中断されます。
* JavaScript エラーにより、[!DNL Google Maps] が正しくレンダリングされません。

<u> 再現手順 </u>:

1. Adobe Commerce管理 UI を読み込みます。
1. ブラウザーコンソールを開き、次のスクリプトを実行します。

   ```
   Object.values([] || {}).forEach((function(e) {  
   e("dd")  
   }));  
   ```

<u> 期待される結果 </u>:

デフォルトの JS ライブラリで使用できるJavaScript関数は、エラーなく正しく実行されます。

<u> 実際の結果 </u>:

JavaScript エラーは、ブラウザーコンソールに表示されます。

```
Uncaught TypeError: this._each is not a function
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
