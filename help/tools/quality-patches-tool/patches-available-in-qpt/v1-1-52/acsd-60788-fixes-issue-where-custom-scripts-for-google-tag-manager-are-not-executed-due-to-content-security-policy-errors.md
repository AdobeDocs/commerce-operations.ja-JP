---
title: 'ACSD-60788: CSP エラーが原因で [!DNL Google Tag Manager] のカスタムスクリプトが実行されない'
description: コンテンツセキュリティポリシー（CSP）エラーが原因で [!DNL Google Tag Manager] のカスタムスクリプトが実行されないAdobe Commerceの問題を修正するには、ACSD-60788 パッチを適用します。
feature: Security
role: Admin, Developer
exl-id: 3392da76-86cb-4357-8658-c95d914a5829
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-60788: コンテンツセキュリティポリシーエラーにより、[!DNL Google Tag Manager]のカスタムスクリプトが実行されない

ACSD-60788 パッチは、コンテンツセキュリティポリシーエラーが原因で[!DNL Google Tag Manager]のカスタムスクリプトが実行されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52がインストールされている場合に利用できます。 パッチ IDはACSD-60788です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

コンテンツセキュリティポリシー（CSP）エラーが発生したため、[!DNL Google Tag Manager]のカスタムスクリプトは実行されません。

<u>複製する手順</u>:

1. *[!DNL Google Tag Manager]*&#x200B;変数を設定します。
1. *[!DNL Google Tag Manager]* カスタム HTML タグを設定します。
1. 最初のタグに次のJavaScript コードを配置します。

   ```xml
   <script nonce="{{gtmNonce}}">
   console.log("Nonce from simple JS {{gtmNonce}}");
   </script>
   ```

1. *GTM*&#x200B;を設定した後、キャッシュをフラッシュします。
1. ブラウザーで開発者コンソールを開きます。
1. ホームページを開きます。

<u>期待される結果</u>:

ブラウザーの開発コンソールに、シンプルなJS （ランダムな文字） *の* Nonceが表示されます。

<u>実際の結果</u>:

ブラウザーの開発コンソールに、単純なJS undefined *の* Nonceが表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
