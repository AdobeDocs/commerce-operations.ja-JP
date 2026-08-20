---
title: MDVA-43983:「個別に表示されない」に設定された商品が検索結果に表示される
description: MDVA-43983 パッチは、「個別に表示されない」として設定された製品がカタログの高度な検索結果に表示される問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.14がインストールされている場合に利用できます。 パッチ IDはMDVA-43983です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Catalog Management, Products, Search
role: Admin
exl-id: d494d263-016b-43fd-aa87-0d74eadc4a6a
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---

# MDVA-43983:「個別に表示されない」に設定された商品が検索結果に表示される

MDVA-43983 パッチは、「個別に表示されない」として設定された製品がカタログの高度な検索結果に表示される問題を解決します。 このパッチは、[品質パッチツール（QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.14がインストールされている場合に使用できます。 パッチ IDはMDVA-43983です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.4

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

「個別に表示されない」に設定されている商品は、カタログの高度な検索結果に引き続き表示されます。

<u>複製する手順</u>:

1. ストア所有者&#x200B;**の** カタログ入力タイプを&#x200B;**ドロップダウン**&#x200B;または&#x200B;**ビジュアルスウォッチ** （カラーなど）として使用して属性を作成します。
1. **検索での使用**&#x200B;を&#x200B;**はい**&#x200B;として設定し、**高度な検索で表示**&#x200B;を&#x200B;**はい**&#x200B;として設定します。
1. 属性オプションを追加します。
1. **表示**&#x200B;を&#x200B;**個別に表示されない**&#x200B;として製品を作成します。
1. カラー属性オプションを割り当てます。
1. ストアフロントの&#x200B;**カタログ詳細検索** ページに移動します。
1. 「カラー属性」フィールドから「カラー属性」オプションのみを選択し、残りのフィールドをそのまま空白のままにしておきます。
1. 高度な検索フォームを送信します。
1. 検索結果の検証：

<u>期待される結果</u>:

「個別に表示されない」に設定されている製品は、カタログの高度な検索結果に表示されません。

<u>実際の結果</u>:

「個別に表示されない」に設定されている製品は、カタログの高度な検索結果に表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
