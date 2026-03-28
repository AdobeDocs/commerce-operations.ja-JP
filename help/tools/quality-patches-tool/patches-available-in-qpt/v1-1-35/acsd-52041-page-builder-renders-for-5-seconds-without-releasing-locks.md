---
title: 'ACSD-52041: ページビルダーのレンダリングでロックが解除されない'
description: ACSD-52041 パッチを適用して、Page Builderがロックを解除せずに5秒間レンダリングするAdobe Commerceの問題を修正します。
feature: Page Builder
role: Admin, Developer
exl-id: 48a7fc36-e98a-4a4e-bed3-248d7d73f6cb
type: Troubleshooting
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-52041: ページビルダーのレンダリングでロックが解除されない

ACSD-52041 パッチは、ロックを解除せずにページビルダーが5秒間レンダリングされる問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.48がインストールされている場合に利用できます。 パッチ IDはACSD-52041-v2です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.4.4 - 2.4.4-p5、2.4.5 - 2.4.5-p4、および2.4.6 - 2.4.6-p2。



>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。


## イシュー

**[!DNL Page Builder]**&#x200B;は、ロックを解除せずに&#x200B;*5*&#x200B;秒間レンダリングします。

<u>複製する手順</u>:

1. CMSのページ、商品ページ、または&#x200B;**[!DNL Page Builder]**&#x200B;を持つものを編集します。
1. 変更を保存します。
1. ページの保存時間に注目してください。

<u>期待される結果</u>

コンテンツが保存されます。 ブラウザーログにエラーは見つかりませんでした。

<u>実際の結果</u>

通常の保存時間よりも時間がかかります。
コンソールでエラーが発生しました：``Page Builder was rendering for 5 seconds without releasing locks``

## パッチを適用する

バージョン **2.4.4 - 2.4.4-p5、2.4.5 - 2.4.5-p4、および2.4.6 - 2.4.6-p2**&#x200B;に対して個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool]  ガイドの](/help/tools/quality-patches-tool/usage.md)>使用状況[!DNL Quality Patches Tool]。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [ [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) ガイドの[!UICONTROL Quality Patches Tool]を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) ガイドの「[!DNL Quality Patches Tool] パッチを検索する」を参照してください。
