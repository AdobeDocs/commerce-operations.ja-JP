---
title: ACSD-52219：ブックマーク表示の切り替えにおける管理者グリッドフィルターの問題を解決
description: ブックマーク表示を頻繁に切り替えると、管理者グリッドの保存されたフィルターが期待どおりに機能しないAdobe Commerceの問題を修正するには、ACSD-52219 パッチを適用します。
feature: Admin Workspace
role: Admin
exl-id: 3f1af6ba-88a0-480c-b16e-c00c655e346f
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-52219：ブックマーク表示の切り替えにおける管理者グリッドフィルターの問題を解決

ACSD-52219 パッチは、ブックマーク表示を頻繁に切り替える際に、管理者グリッドの保存されたフィルターが期待どおりに機能しない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.39がインストールされている場合に利用できます。 パッチ IDはACSD-52219です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ブックマークビューを頻繁に切り替えると、管理者グリッドに保存されたフィルターが意図したとおりに機能しません。

<u>複製する手順</u>:

1. 管理画面の[!DNL Sales Order] グリッドにアクセスします。
1. 2～3個のフィルターを作成します。
1. ビューを切り替えてフィルター設定を確認し、正確に保存されるようにします。
1. Filter1またはFilter2に移動します。
1. ページを更新して、表示されたデータを更新します。
1. 別のビューに切り替えて、フィルターが変更されないことに注意してください。
1. 特定のフィルターが設定されていなくても、デフォルトのビューにフィルターされた結果が表示されるようになりました。

<u>期待される結果</u>:

フィルターは交換されず、元の状態を保持します。

<u>実際の結果</u>:

ビューを修正すると、フィルターが混同され、正しいビューは保存されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
