---
title: ACSD-50815：単純な製品の小数点以下桁の数量を新しいバンドル製品オプションに使用できない
description: ACSD-50815 パッチを適用して、シンプルな商品の小数点以下桁の数量を新しい同梱商品オプションに使用できないAdobe Commerceの問題を修正します。
feature: Products
role: Admin
exl-id: 5cd69abe-bd88-497d-9696-804c787b73ef
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-50815：単純な製品の小数点以下桁の数量を新しいバンドル製品オプションに使用できない

ACSD-50815 パッチでは、単純な製品の小数点以下桁の数量を新しいバンドル製品オプションに使用できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.35がインストールされている場合に利用できます。 パッチ IDはACSD-50815です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

シンプルな製品の小数点以下桁は、新しいバンドル製品オプションには使用できません。

<u>複製する手順</u>:

1. 管理者としてログインします。
1. シンプルな新製品を作成。
   * **[!UICONTROL Advanced Inventory]** ウィンドウで、[!UICONTROL Qty Uses Decimal] = [!UICONTROL Yes]と設定します。
   * 単純な製品を保存します。
1. 新しいバンドル製品を作成します。
1. 任意のオプションを追加します。
1. シンプルな製品をこのオプションに追加します。
1. バンドルされた製品オプションで、単純な製品の小数を設定します。 例えば、1.5。

<u>期待される結果</u>:

10進数を設定できます。 エラーは表示されません。

<u>実際の結果</u>:

エラー「*このフィールドに有効な数値を入力してください*」が表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
