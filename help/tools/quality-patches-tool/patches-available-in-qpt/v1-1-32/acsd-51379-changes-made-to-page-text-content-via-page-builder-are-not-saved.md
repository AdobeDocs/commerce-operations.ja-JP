---
title: 'ACSD-51379: [!DNL Page Builder] を介したページのテキストコンテンツへの変更が保存されない'
description: ACSD-51379 パッチを適用して、 [!DNL Page Builder] 経由でページのテキストコンテンツに加えた変更が保存されないAdobe Commerceの問題を修正します。
feature: Page Builder, Page Content
role: Admin
exl-id: 03fc2865-04b6-4330-b80c-8d694baa8c88
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-51379: [!DNL Page Builder]を介したページのテキストコンテンツの変更が保存されない

ACSD-51379 パッチは、[!DNL Page Builder]を介してページのテキストコンテンツに加えられた変更が保存されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.32がインストールされている場合に利用できます。 パッチ IDはACSD-51379です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!DNL Page Builder]を介してページのテキストコンテンツに加えた変更は保存されません。

<u>複製する手順</u>:

1. Adminにログインします。
1. **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**&#x200B;に移動します。
1. **[!UICONTROL Content]** タブに1行と1つのテキスト要素を含むテストページを作成します。
1. ページを保存して、**[!UICONTROL Content]** タブに戻ります。
1. テキストを選択して変更することで、テキストを編集します。

   **注意：**&#x200B;この問題は、エディターをアクティブにせずにテキストを選択して変更した場合にのみ再現可能です。

1. テストページの「**[!UICONTROL Save and Close]**」ボタンをクリックします。
1. もう一度テストページを開き、「**[!UICONTROL Content]**」タブを確認します。

<u>期待される結果</u>:

新しいテキストは、元のテキスト要素と重複したテキスト要素に対して正常に保存されます。

<u>実際の結果</u>:

テキスト要素は正常に複製されますが、新しいテキストは保存されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
