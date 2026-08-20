---
title: ACSD-50367：顧客アドレスの書き出しがマルチセレクト属性で機能しない
description: ACSD-50367 パッチを適用して、値のない複数選択**の顧客アドレス属性が作成されたときに、顧客アドレスの書き出しが機能しないAdobe Commerce**問題を修正します。
feature: Admin Workspace, Attributes, Data Import/Export, Shipping/Delivery
role: Admin
exl-id: 3f33a590-e7c2-424e-aacd-2df7ab893c3e
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-50367：顧客アドレスの書き出しが機能しない

ACSD-50367 パッチは、値のない複数選択&#x200B;**`Customer Address`**&#x200B;属性が作成された場合に、顧客アドレスの書き出しが機能しない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.30がインストールされている場合に利用できます。 パッチ IDはACSD-50367です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

値のない複数選択&#x200B;**`Customer Address`**&#x200B;属性が作成された場合、顧客アドレスの書き出しは機能しません。

<u>前提条件</u>:

住所を持つ顧客を作成します。

<u>複製する手順</u>:

1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer Addresses]**&#x200B;に複数選択&#x200B;**`Customer Address`**&#x200B;属性を作成します。
1. **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Export]**&#x200B;に移動し、**`Customer Address`** エンティティの種類を選択します。
1. 顧客アドレスをエクスポートします。 何も書き出されていないことがわかります。
1. 複数選択&#x200B;**`Customer Address`**&#x200B;属性を削除し、顧客アドレスを再度書き出します。 今回は、アドレスのCSV ファイルが生成されます。

<u>期待される結果</u>:

顧客アドレスは、複数選択&#x200B;**`Customer Address`**&#x200B;属性を作成するときに、CSV ファイルとしてエクスポートできます。

<u>実際の結果</u>:

複数選択&#x200B;**`Customer Address`**&#x200B;属性を作成する場合、顧客アドレスをCSV ファイルとして書き出すことはできません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
