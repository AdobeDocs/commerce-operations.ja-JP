---
title: 'ACSD-57045: URLの書き換えにより、[!UICONTROL Website Root]の後に無限ページループが発生する（[!UICONTROL Hierarchy]からチェックを外す）'
description: ACSD-57045 パッチを適用して、[!UICONTROL Website Root]が[!UICONTROL Hierarchy]からオフにした後にURLの書き換えが無限ページループを引き起こすAdobe Commerceの問題を修正します。
feature: CMS
role: Admin, Developer
exl-id: 7beaee40-a392-4644-917e-c507e79bddcc
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 0%

---

# ACSD-57045: URLの書き換えにより、[!UICONTROL Website Root]の後に無限ページループが発生する（[!UICONTROL Hierarchy]からチェックを外す）

ACSD-57045 パッチは、**[!UICONTROL Website Root]**&#x200B;が&#x200B;**[!UICONTROL Hierarchy]**&#x200B;からオフにされた後にURLの書き換えが無限ページループを引き起こす問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49がインストールされている場合に利用できます。 パッチ IDはACSD-57045です。 この問題は、Adobe Commerce 2.5.0で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

URLの書き換えにより、**[!UICONTROL Website Root]**&#x200B;が&#x200B;**[!UICONTROL Hierarchy]**&#x200B;から選択解除された後、無限ページループが発生します。

<u>複製する手順</u>:

1. *Test-Parent*&#x200B;という名前のCMS ページを作成します。
1. *Test-Child*&#x200B;という名前のページを作成し、**[!UICONTROL Hierarchy]** セクションで、**[!UICONTROL Website Root]** > **[!UICONTROL Parent]**&#x200B;を選択して保存します。
1. **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]**&#x200B;に移動します。
1. 次の2つの新しい書き換えがあります。
   * *cms/page/view/page_id/ID_NUMBER_FOR_PAGE*&#x200B;を指す&#x200B;*Test-Parent*&#x200B;へのリクエストパス
   * *cms/page/view/page_id/ID_NUMBER_FOR_PAGE*&#x200B;を指す&#x200B;*Test-Child*&#x200B;へのリクエストパス
1. ストアフロントにアクセスし、URLに&#x200B;*test-child*&#x200B;を追加します。 子ページが表示されます。
1. 同じことを行いますが、*test-parent/test-child/*&#x200B;をURLに追加して、同じページを表示します。
1. **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]**&#x200B;に移動し、**[!UICONTROL Add URL Rewrite]**&#x200B;を選択します。 次の設定を選択します。
   * 種類：*カスタム*
   * 要求パス：*test-parent/test-child*
   * ターゲットパス：*test-child*
   * リダイレクトの種類：*Permanent （301）*
1. *test-parent/test-child* パスにアクセスすると、*test-child*&#x200B;にリダイレクトされます。
1. 子ページを編集します（**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** >子を選択し、**[!UICONTROL Edit]**&#x200B;を選択）。
1. **[!UICONTROL Hierarchy]** セクションで、*テスト親*&#x200B;を選択したままにしますが、**[!UICONTROL Website Root]**&#x200B;の選択を解除して保存します。
1. **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]**&#x200B;に移動し、*cms/page/view/page_id* リダイレクトの元の&#x200B;*test-child*&#x200B;が見つからず、その時点で&#x200B;*test-child*&#x200B;から&#x200B;*test-parent/test-child*&#x200B;を指すパスに置き換えられることに注意してください。
1. ストアフロントにアクセスし、*Test-Child* ページにアクセスしてみてください。

<u>期待される結果</u>:

*テスト子* ページが開きます。

<u>実際の結果</u>:

*テスト子* ページが開いていません。 ブラウザーは&#x200B;*test-parent/test-child* ページを無限ループで開こうとします。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
