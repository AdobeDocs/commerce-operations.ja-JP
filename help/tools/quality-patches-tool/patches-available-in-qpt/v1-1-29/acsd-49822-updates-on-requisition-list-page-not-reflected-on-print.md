---
title: ACSD-49822：要求リストページの更新が印刷要求リストに反映されない
description: ACSD-49822 パッチを適用して、購買リストページの更新が印刷購買リストに反映されないAdobe Commerceの問題を修正します。
feature: Admin Workspace, B2B
role: Admin
exl-id: 053b8900-0900-4b7e-ba1b-ad4b88ca3f35
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-49822：要求リストの更新が印刷要求リストに反映されない

ACSD-49822 パッチは、要求リストページの更新が印刷要求リストに反映されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.29がインストールされている場合に利用できます。 パッチ IDはACSD-49822です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

要求リストページの更新は、印刷要求リストには反映されません。

<u>複製する手順</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[B2B機能]**&#x200B;に移動して、要求リストを有効にします。
1. 商品を作成する。
1. 顧客としてログインし、2つの製品を要件リストに追加します。
1. **[!UICONTROL My Account]** > **[!UICONTROL My Requisition Lists]**&#x200B;に移動します。
1. 購買リストの表示。
1. 右上隅の&#x200B;**[!UICONTROL Print]**&#x200B;をクリックします。
1. 印刷ウィンドウと印刷要求リストページを閉じます。
1. リスト内の項目を削除するか、項目の数量を更新して、もう一度印刷してみてください。
1. 印刷ウィンドウでアイテムが更新されないことがわかります。
1. 印刷ウィンドウを閉じます。
1. 商品が購買リストの印刷ページで更新されないことがわかります。

<u>期待される結果</u>:

印刷するリストは、変更が適用された後に更新されます。

<u>実際の結果</u>:

更新は購買リストの印刷ページには反映されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
