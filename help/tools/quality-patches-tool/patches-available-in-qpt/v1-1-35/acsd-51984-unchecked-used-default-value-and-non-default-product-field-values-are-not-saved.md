---
title: ACSD-51984:2番目のweb サイト、ストア、ストアビューでは、チェックされていない[!UICONTROL Use Default Value]およびデフォルト以外の製品フィールド値が保存されない
description: ACSD-51984 パッチを適用して、チェックされていない[!UICONTROL Use Default Value]とデフォルト以外の製品フィールド値が2番目のweb サイト、ストア、ストアビューに保存されないAdobe Commerceの問題を修正します。
feature: Products
role: Admin
exl-id: 51a810fa-d416-4b37-b5bd-66eed9fe4626
type: Troubleshooting
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# ACSD-51984：チェックされていない&#x200B;*[!UICONTROL Use Default Value]*&#x200B;とデフォルト以外の製品フィールド値が保存されない

>[!NOTE]
>
>このパッチは古く、1.1.39 QPT リリースで追加された[ACSD-54776](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-39/acsd-54776-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) パッチに置き換えられました。

ACSD-51984 パッチは、チェックされていない&#x200B;**[!UICONTROL Use Default Value]**&#x200B;およびデフォルト以外の製品フィールド値が、2番目のweb サイト、ストア、ストアビューに保存されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.35がインストールされている場合に利用できます。 パッチ IDはACSD-51984です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

オフになっている&#x200B;*[!UICONTROL Use Default Value]*&#x200B;およびデフォルト以外の製品フィールド値は、2番目のweb サイト、ストア、ストアビューには保存されません。

<u>複製する手順</u>:

1. バックエンドに移動し、**[!UICONTROL Stores]** > **[!UICONTROL All Stores]**&#x200B;に移動して、新しいweb サイト、ストア、ストアビューを作成します。
1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;に移動し、シンプルな製品を作成して保存し、両方のweb サイト（**[!UICONTROL Product in Websites]**&#x200B;から）に製品を割り当てます。
1. スコープを手順2から新しく作成したストアビューに変更します。
1. **[!UICONTROL Search Engine Optimization]**&#x200B;に移動し、**[!UICONTROL Use Default Value]**、[!UICONTROL Meta Title]、[!UICONTROL Meta Keywords]の[!UICONTROL Meta Description] チェックボックスのチェックを外します。
1. フィールド *[!UICONTROL Meta Title]*、*[!UICONTROL Meta Keywords]*&#x200B;および&#x200B;*[!UICONTROL Meta Description]*&#x200B;からテキストを削除し、**[!UICONTROL Save]**&#x200B;をクリックします。
1. もう一度&#x200B;**[!UICONTROL Search Engine Optimization]**&#x200B;に移動します。

<u>期待される結果</u>

フィールドとチェックボックスの値が保存されます。

<u>実際の結果</u>

フィールドとチェックボックスの値は保存されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool]  ガイドの](/help/tools/quality-patches-tool/usage.md)>使用状況[!DNL Quality Patches Tool]。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [&#x200B; [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) ガイドの[!UICONTROL Quality Patches Tool]を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) ガイドの「[!DNL Quality Patches Tool] パッチを検索する」を参照してください。
