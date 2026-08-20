---
title: ACSD-51853：コピーしたテキストスタイルがページビルダーを使用して適用されない
description: ページビルダーの使用時にコピーしたテキストスタイルが適用されないAdobe Commerceの問題を修正するには、ACSD-51853 パッチを適用します。
feature: Page Builder
role: Admin
exl-id: fda5ba6e-4786-473c-a3a2-7356aa20f5ae
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-51853：コピーしたテキストスタイルがページビルダーを使用して適用されない

ACSD-51853 パッチでは、ページビルダーを使用する際にコピーしたテキストスタイルが適用されない問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.34がインストールされている場合に利用できます。 パッチ IDはACSD-51853です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ページビルダーを使用する場合、コピーしたテキストスタイルは適用されません

<u>複製する手順</u>:

1. Adminにログインします。
1. > **コンテンツ** > **ページ** > **任意のページを開く** > **ページビルダーで編集**&#x200B;に移動します。
1. **[!UICONTROL Elements]**&#x200B;から行と&#x200B;*テキスト*&#x200B;をドラッグします。
1. **強化されたコンテンツ**&#x200B;をコピーし、そのテキストを&#x200B;**[!UICONTROL Page Builder]**&#x200B;に貼り付けます。

<u>期待される結果</u>

コピーしたテキストは、すべてのスタイルでペーストされます。

<u>実際の結果</u>

コピーしたテキストはプレーンテキストとしてペーストされ、すべてのスタイルが失われます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
