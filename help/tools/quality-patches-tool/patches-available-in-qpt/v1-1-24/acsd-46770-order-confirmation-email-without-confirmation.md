---
title: 'ACSD-46770: [!UICONTROL Email Order Confirmation]のチェックを外しても、注文確認メールが送信される'
description: ACSD-46770 パッチを適用して、[!UICONTROL Email Order Confirmation]が選択されていない場合でも注文確認メールが送信されるAdobe Commerceの問題を修正します。
feature: Communications, Orders
role: Admin
exl-id: d25ca121-7551-417c-b598-d8ed3a3da969
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-46770: **[!UICONTROL Email Order Confirmation]**&#x200B;のチェックを外しても、注文確認メールが送信される

ACSD-46770 パッチは、**[!UICONTROL Email Order Confirmation]**&#x200B;が選択されていない場合でも、REST APIを介してゲストユーザーとして注文を配置できる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24がインストールされている場合に利用できます。 パッチ IDはACSD-46770です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

**[!UICONTROL Email Order Confirmation]**&#x200B;が選択されていない場合でも、注文確認メールが送信されます。

<u>複製する手順</u>:

1. 顧客アカウントの作成。
1. **[!UICONTROL Sales]** > **[!UICONTROL Order]**&#x200B;に移動し、**[!UICONTROL Create New Order]**&#x200B;をクリックします。
1. 顧客を選択し、注文に商品を追加し、住所を入力して、配送および支払い方法を選択します。
1. 注文を送信する前に、**[!UICONTROL Email Order confirmation]** チェックボックスの選択を解除します。
1. **[!UICONTROL Submit Order]**&#x200B;をクリックして注文を作成します。

<u>期待される結果</u>:

**[!UICONTROL Email Order Confirmation]**&#x200B;が選択されていない場合、注文確認メールは送信されません。

<u>実際の結果</u>:

未選択の&#x200B;**[!UICONTROL Email Order Confirmation]** チェックボックスに関係なく、注文確認メールが送信されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
