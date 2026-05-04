---
title: 'ACSD-63244:  [!DNL Google Maps]  レンダリングとコンソールのエラーを含む管理パネル JavaScriptの問題を解決します'
description: ACSD-63244 パッチでは、管理パネルの複数のJavaScriptの問題を修正します。これには、 [!DNL Google Maps]  レンダリングと繰り返し発生する「Uncaught TypeError this._each is not a function」エラーがブラウザーコンソールで発生する問題が含まれます。
feature: Admin Workspace
role: Admin, Developer
exl-id: 1985c845-219e-4af4-8f70-62dd57722494
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-63244: [!DNL Google Maps]のレンダリングエラーやコンソールエラーなど、管理パネル JavaScriptの問題を解決する

ACSD-63244 パッチは、ブラウザーコンソールでの[!DNL Google Maps]のレンダリングと`Uncaught TypeError: this._each is not a function`の繰り返しエラーに関する問題など、管理パネルの複数のJavaScriptの問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56で利用できます。 パッチ IDはACSD-63244です。 この問題は、Adobe Commerce 2.4.8で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方式） 2.4.4、2.4.4-p9、2.4.6-p7、2.4.7

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

* ブラウザーコンソールに`Uncaught TypeError: this._each is not a function` エラーが表示され、Admin UI機能が中断されます。
* JavaScript エラーにより、[!DNL Google Maps]が正しくレンダリングされません。

<u>複製する手順</u>:

1. Adobe Commerce管理UIを読み込みます。
1. ブラウザーコンソールを開き、次のスクリプトを実行します。

   ```text
   Object.values([] || {}).forEach((function(e) {  
   e("dd")  
   }));  
   ```

<u>期待される結果</u>:

デフォルトのJS ライブラリで使用可能なJavaScript関数は、エラーなしで正しく実行されます。

<u>実際の結果</u>:

JavaScript エラーがブラウザーコンソールに表示されます。

```text
Uncaught TypeError: this._each is not a function
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
