---
title: ACSD-47106：会社作成ページの新しいカスタム属性が保存されない
description: 企業作成ページの新しいカスタム属性に値を保存できないAdobe Commerceの問題を修正するには、ACSD-47106 パッチを適用します。
feature: Attributes, B2B, Companies
role: Developer
exl-id: 5835760d-fca1-44ba-aa5e-8797258c7c75
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-47106：会社作成ページの新しいカスタム属性が保存されない

ACSD-47106 パッチは、企業作成ページの新しいカスタム属性に値を保存できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.22がインストールされている場合に利用できます。 パッチ IDはACSD-47106です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

企業作成ページの新しいカスタム属性に値を保存することはできません。

<u>前提条件</u>:

* B2B モジュールがインストールされている。

<u>複製する手順</u>:

1. Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Customer]** > **[!UICONTROL Add New Attribute]**&#x200B;に移動します。
1. 新しい属性を作成：_テスト 01_。
1. Commerce Admin > **[!UICONTROL Customers]** > **[!UICONTROL Companies]** >に移動し、必要なすべての詳細を含む新しい会社を作成します。
1. カスタム属性&#x200B;_テスト 01_&#x200B;に値を追加してみてください。
1. カスタム属性&#x200B;_テスト 01_&#x200B;の値を更新してみてください。

<u>期待される結果</u>:

変更は保存されます。

<u>実際の結果</u>:

変更は保存されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
