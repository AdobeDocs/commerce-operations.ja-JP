---
title: ACSD-51645：拡張機能「Magento_OfflineShipping」が無効になっている場合の新しいカート価格ルールの保存
description: 拡張機能のMagento_OfflineShippingが無効になっている場合に新しい買い物かごの価格規則を保存する際にエラーが発生するAdobe Commerceの問題を修正するには、ACSD-51645 パッチを適用します。
exl-id: ce747ae4-6d2f-41c0-ba75-7da72be359c7
type: Troubleshooting
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-51645：拡張機能「Magento_OfflineShipping」が無効になっている場合の新しいカート価格ルールの保存

ACSD-51645 パッチでは、拡張機能のMagento_OfflineShippingが無効になっている場合に、新しい買い物かごの価格規則を保存する際にエラーが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33がインストールされている場合に利用できます。 パッチ IDはACSD-51645です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

拡張機能`Magento_OfflineShipping`が無効になっている場合、新しいカート価格ルールを保存する際にエラーが発生します。

<u>複製する手順</u>:

1. `Magento_OfflineShipping` モジュールを無効にします。
1. **管理者**&#x200B;にログインします。
1. **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]**&#x200B;に移動します。
1. 新しい&#x200B;**[!UICONTROL Cart Price Rule]**&#x200B;を作成します。
1. 必須フィールドに入力します。
1. **[!UICONTROL Cart Price Rule]**&#x200B;を保存します。

<u>期待される結果</u>:

買い物かごの価格ルールが正常に保存されました。

<u>実際の結果</u>:

次のエラーが発生します。
`report.ERROR: Warning: Undefined array key "simple_free_shipping" in app/code/Magento/SalesRule/Controller/Adminhtml/Promo/Quote/Save.php on line 67 [] []`

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool]  ガイドの](/help/tools/quality-patches-tool/usage.md)>使用状況[!DNL Quality Patches Tool]。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [&#x200B; [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) ガイドの[!UICONTROL Quality Patches Tool]を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) ガイドの「[!DNL Quality Patches Tool] パッチを検索する」を参照してください。
