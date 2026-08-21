---
title: 'ACSD-50895: [!DNL Google Analytics] 4 GTMが設定されていない場合、 [!DNL Google Analytics] 3 GTM タグは実行されません'
description: ACSD-50895 パッチを適用して、 [!DNL Google Analytics] 4 GTMが設定されていない場合、 [!DNL Google Analytics] 3 GTM タグが実行されないAdobe Commerceの問題を修正します。
role: Admin
exl-id: 871e2ca1-dc10-435c-9325-62f5b9b673ad
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-50895: [!DNL Google Analytics] 4 GTMが設定されていない場合、[!DNL Google Analytics] 3 GTM タグは実行されません

ACSD-50895 パッチは、[!DNL Google Analytics] 4 GTMが設定されていない場合、[!DNL Google Analytics] 3 GTM タグが実行されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.33がインストールされている場合に利用できます。 パッチ IDはACSD-50895です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!DNL Google Analytics] 4 GTMが設定されていない場合、[!DNL Google Analytics] 3 GTM タグは実行されません。

<u>複製する手順</u>:

1. 管理者ユーザーとしてログインします。
1. **管理者** > **Store** > **Configuration** > **Sales** > **Google API** > **Google Analytics**&#x200B;で&#x200B;**[!DNL Google Analytics 3]**&#x200B;と&#x200B;**[!DNL Google Tag Manager]**&#x200B;を有効にします。
1. **[!DNL Google Analytics 4]**&#x200B;と&#x200B;**[!DNL Google Tag Manager]**&#x200B;を有効にしないでください。
1. ストアフロントで商品ページを開きます。

<u>期待される結果</u>:

GTM タグは、**[!DNL Google Analytics]** 3 GTMのみが有効な場合に実行されます。

<u>実際の結果</u>:

**[!DNL Google Analytics]** 4 GTMが無効になっている場合、GTM タグは実行されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
