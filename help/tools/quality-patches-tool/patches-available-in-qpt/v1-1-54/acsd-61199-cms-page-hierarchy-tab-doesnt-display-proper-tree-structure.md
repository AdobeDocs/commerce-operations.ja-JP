---
title: 「ACSD-61199:CMS ページの「[!UICONTROL Hierarchy]」タブに適切なツリー構造が表示されない」
description: CMS ページを既存の*[!UICONTROL Hierarchy]*で編集する際に、CMS ページの*[!UICONTROL Hierarchy]* タブに適切なツリー構造が表示されないAdobe Commerceの問題を修正するため、ACSD-61199 パッチを適用してください。
feature: Page Content
role: Admin, Developer
exl-id: f541d001-9680-431a-9a62-816c2d10b6d5
source-git-commit: 5568b2f574c7e90e641513c3c0ea4574648770ac
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-61199:CMSページの「[!UICONTROL Hierarchy]」タブに適切なツリー構造が表示されない

ACSD-61199 パッチでは、既存の *[!UICONTROL Hierarchy]* を使用してCMS ページを編集すると、CMS ページの「*[!UICONTROL Hierarchy]*」タブに適切なツリー構造が表示されない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 がインストールされている場合に使用できます。 パッチ ID は ACSD-61199 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

既存の *[!UICONTROL Hierarchy]* を使用してCMSページを編集すると、CMSページの「*[!UICONTROL Hierarchy]*」タブに適切なツリー構造が表示されない。

<u> 再現手順 </u>:

1. **[!UICONTROL Admin]**/**[!UICONTROL Content]**/**[!UICONTROL Pages]** に移動します。
1. 新しい **[!UICONTROL CMS page]** を作成します。 これは *[!UICONTROL Hierarchy]* の web サイトのルートに追加されます。
1. ページを保存します
1. **[!UICONTROL Admin]**/**[!UICONTROL Content]**/**[!UICONTROL Hierarchy]** に移動します。
1. その他の既存のページを *[!UICONTROL Hierarchy]* に追加します。
1. *[!UICONTROL Hierarchy]* を保存します。
1. **[!UICONTROL Admin]**/**[!UICONTROL Content]**/**[!UICONTROL Pages]** に移動します。
1. 既存のページを編集し、*[!UICONTROL Hierarchy]* ージを開きます。

<u> 期待される結果 </u>:

*[!UICONTROL Hierarchy]* は、期待どおりに読み込まれます。

<u> 実際の結果 </u>:

*[!UICONTROL Hierarchy]* は「」タブに読み込まれません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

[[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
