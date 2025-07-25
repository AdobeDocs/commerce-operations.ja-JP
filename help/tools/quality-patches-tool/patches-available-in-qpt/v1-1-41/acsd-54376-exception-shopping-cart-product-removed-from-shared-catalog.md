---
title: ACSD-54376：商品が [!UICONTROL shared catalog] から削除された際に、買い物かごで例外が発生する
description: ACSD-54376 パッチを適用すると、買い物かごに追加された商品が [!UICONTROL shared catalog] から削除されたときに買い物かごで例外が発生するAdobe Commerceの問題を修正できます。
feature: Shopping Cart, B2B
role: Admin, Developer
exl-id: 59047ccb-d434-46cd-8d2f-ceb0c85a785a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-54376：商品が [!UICONTROL shared catalog] から削除された際に、買い物かごで例外が発生する

ACSD-54376 パッチは、商品が買い物かごに追加された後に [!UICONTROL shared catalog] から削除された場合に、買い物かごで例外が発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.41 がインストールされている場合に使用できます。 パッチ ID は ACSD-54376 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

商品が買い物かごに追加された後に [!UICONTROL shared catalog] から削除されると、買い物かごで例外が発生します。

<u> 再現手順 </u>:

1. B2B とAdobe Commerceをインストールします。
1. [!UICONTROL shared catalog] を有効にします。
1. 製品を作成してデフォルトの [!UICONTROL shared catalog] に割り当てます。
1. ストアフロントから買い物かごに製品を追加します。
1. [!UICONTROL shared catalog] ージから製品を削除します。
1. ミニ買い物かごドロップダウンを使用して、チェックアウトページに移動します。

<u> 期待される結果 </u>:

例外は処理され、表示されません。

<u> 実際の結果 </u>:

未処理の例外がチェックアウトページに表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
