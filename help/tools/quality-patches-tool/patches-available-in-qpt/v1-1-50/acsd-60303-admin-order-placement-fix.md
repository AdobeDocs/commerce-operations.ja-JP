---
title: 「ACSD-60303:HTMLの縮小が有効な状態で、管理者の注文の配置の問題が解決されました」
description: HTMLの縮小が有効になっている場合に管理者から注文できないAdobe Commerceの問題を修正するために、ACSD-60303 パッチを適用してください。
feature: Orders
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-60303:HTMLの縮小が有効な状態で、管理者の注文の配置に関する問題が解決されました

ACSD-60303 パッチは、HTMLの縮小が有効になっている場合に、管理者から注文できない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50 がインストールされている場合に使用できます。 パッチ ID は ACSD-60303 です。 この問題は 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p8

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p9 - 2.4.4-p10、2.4.5-p8 - 2.4.5-p9、2.4.6-p6 - 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

HTMLの縮小が有効になっている場合、管理パネルから注文することはできません。

<u> 再現手順 </u>:

1. HTMLの縮小を有効にします。
1. **[!UICONTROL Application Mode]** を *[!UICONTROL Production]* に設定します。
1. 管理パネルから注文を作成します。

<u> 期待される結果 </u>:

注文が正常に完了しました。

<u> 実際の結果 </u>:

注文は作成されず、次のエラーが記録されます。

`report.CRITICAL: ParseError: syntax error, unexpected token "<<" in var/view_preprocessed/pub/static/vendor/magento/module-gift-wrapping/view/adminhtml/templates/order/create/info.phtml:1`

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
