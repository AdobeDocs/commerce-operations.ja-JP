---
title: ACSD-45049：お客様の「必須」属性設定が、管理者のweb サイトスコープに従って機能しない
description: Adminのweb サイト スコープに従って、お客様の"[!UICONTROL Is required]"属性が適切に上書きされないAdobe Commerceの問題を修正するには、ACSD-45049 パッチを適用します。
feature: Attributes, Customers
role: Admin, Developer
exl-id: 368af877-a3ec-431f-8f41-5d51354be571
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-45049：お客様&#x200B;*[!UICONTROL Is required]*&#x200B;の属性設定が、管理者のweb サイト スコープに従って機能しない

ACSD-45049 パッチは、Adminのweb サイト スコープに従って、顧客&#x200B;*[!UICONTROL Is required]*&#x200B;属性設定が正しく機能しない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/usage.md) 1.1.50がインストールされている場合に利用できます。 パッチ IDはACSD-45049です。 この問題は、Adobe Commerce 2.4.6で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.4.4 - 2.4.4-p7および2.4.5 - 2.4.5-p9

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

お客様&#x200B;*[!UICONTROL Is required]*&#x200B;の属性設定が、Adminのweb サイト スコープに従って正しく機能しません。

<u>複製する手順</u>:

1. 2つのweb サイトを作成する：
1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer attribute]**&#x200B;を開きます。
1. 新しい属性を作成し、**[!UICONTROL Is value required]** = *No*&#x200B;と設定します。
1. 既定のWeb サイトに切り替え、**[!UICONTROL Is value required]** = *はい*&#x200B;と変更します。 他のweb サイトにはデフォルト値があります。
1. デフォルト以外のweb サイトの場合は、管理者から新しい顧客を作成します。

<u>期待される結果</u>:

デフォルト以外のweb サイトでは、属性は必要ありません。

<u>実際の結果</u>:

* Adminで顧客を作成する際に、デフォルト以外のweb サイトに対しては、属性が必要です。
* ストアフロントで顧客を登録する際に、デフォルト以外のweb サイトに属性は必要ありません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
