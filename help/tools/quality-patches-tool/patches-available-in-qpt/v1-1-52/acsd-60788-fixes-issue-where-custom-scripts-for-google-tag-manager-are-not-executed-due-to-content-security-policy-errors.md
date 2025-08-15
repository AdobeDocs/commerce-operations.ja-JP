---
title: 'ACSD-60788: CSP エラーのため  [!DNL Google Tag Manager]  カスタムスクリプトが実行されない'
description: ACSD-60788 パッチを適用すると、コンテンツセキュリティポリシー（CSP）のエラーが原因で  [!DNL Google Tag Manager]  のカスタムスクリプトが実行されないAdobe Commerceの問題を修正できます。
feature: Security
role: Admin, Developer
exl-id: 3392da76-86cb-4357-8658-c95d914a5829
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-60788: コンテンツセキュリティポリシーエラーにより、[!DNL Google Tag Manager] のカスタムスクリプトが実行されない

ACSD-60788 パッチでは、コンテンツセキュリティポリシーエラーが原因で [!DNL Google Tag Manager] のカスタムスクリプトが実行されない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52 がインストールされている場合に使用できます。 パッチ ID は ACSD-60788 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

コンテンツセキュリティポリシー（CSP）のエラーにより、[!DNL Google Tag Manager] のカスタムスクリプトが実行されません。

<u> 再現手順 </u>:

1. *[!DNL Google Tag Manager]* 変数を設定します。
1. *[!DNL Google Tag Manager]* カスタム HTML タグを設定します。
1. 最初のタグに次のJavaScript コードを配置します。

   ```
   <script nonce="{{gtmNonce}}">
   console.log("Nonce from simple JS {{gtmNonce}}");
   </script>
   ```

1. *GTM* を設定した後で、キャッシュをフラッシュします。
1. ブラウザーで開発者コンソールを開きます。
1. ホームページを開きます。

<u> 期待される結果 </u>:

ブラウザー開発コンソールに *シンプルな JS から Nonce （ランダムな文字）* と表示される。

<u> 実際の結果 </u>:

ブラウザー開発コンソールに *Nonce from simple JS undefined* と表示される。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
