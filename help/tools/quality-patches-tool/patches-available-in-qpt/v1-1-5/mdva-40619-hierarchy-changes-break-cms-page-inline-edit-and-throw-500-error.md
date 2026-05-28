---
title: MDVA-40619：階層の変更でCMS ページのインライン編集が機能しなくなり、500 エラーが発生する
description: MDVA-40619 パッチは、CMS ページ階層の変更がCMS ページのインライン編集を壊し、「500 エラー」をスローする問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.5がインストールされている場合に利用できます。 パッチ IDはMDVA-40619です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: CMS
role: Admin
exl-id: 148cb0a5-5a6c-4cfa-bf95-4bafc57beec6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-40619：階層の変更でCMS ページのインライン編集が機能しなくなり、500 エラーが発生する

MDVA-40619 パッチは、CMS ページ階層の変更がCMS ページのインライン編集を壊し、「500 エラー」をスローする問題を解決します。 このパッチは、[品質パッチツール （QPT） &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5がインストールされている場合に使用できます。 パッチ IDはMDVA-40619です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

CMSのページ階層の変更は、CMSのページのインライン編集を解除し、「500 エラー」をスローします。

<u>複製する手順</u>:

1. 管理パネル / **コンテンツ** / **階層**&#x200B;に移動します。
1. 「Default Store View」を選択します。
1. 「親ノード階層を使用」のチェックを外します。
1. ページを手動で選択し、**保存**&#x200B;をクリックします。
1. 次に、**コンテンツ** > **ページ**&#x200B;に移動します。
1. CMSの任意のページをグリッドから編集してみてください。
1. **保存**&#x200B;をクリックします。

<u>期待される結果</u>:

ページが正常に保存されました。

<u>実際の結果</u>:

次のエラーが表示されます。

*サーバーの技術的な問題により、エラーが発生しました。 もう一度試して、今やっていることをやり続けてください。 問題が解決しない場合は、後でもう一度やり直してください。*

`Error: Call to a member function getData() on null in /magento2ee/app/code/Magento/VersionsCms/Controller/Adminhtml/Cms/Page/InlineEdit/Plugin.php:62`

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)で使用可能な パッチ」セクションを参照してください。
