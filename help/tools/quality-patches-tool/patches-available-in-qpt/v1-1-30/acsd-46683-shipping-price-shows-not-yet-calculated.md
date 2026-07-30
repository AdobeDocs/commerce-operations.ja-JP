---
title: ACSD-46683：送料が表示されます*まだ計算されていません*
description: ACSD-46683 パッチを適用して、配送価格が「まだ計算されていません」と表示されるAdobe Commerceの問題を修正します。
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
exl-id: ebd79187-2835-403b-945d-80ac34d6fb9c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# ACSD-46683：送料に&#x200B;*未計算*&#x200B;と表示される

ACSD-46683 パッチは、送料に「*まだ計算されていません*」と表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30がインストールされている場合に利用できます。 パッチ IDはACSD-46683です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

送料には、*未計算*&#x200B;と表示されます。

<u>前提条件</u>:

Adobe Commerce Inventory management（MSI）モジュールがインストールされます。

<u>複製する手順</u>:

1. シンプルな商品を作成し、価格を&#x200B;*$34*&#x200B;に設定します。
1. 送料無料の配送方法を設定します。
1. もう1つ以上の配信方法を設定します。
1. **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]**&#x200B;に移動し、新しいルールを作成します。
   * 名前= *75more*
   * クーポン =なし
   * 優先度= 1
   * 条件：小計が&#x200B;*$75*&#x200B;以上
   * アクション：
     * 出荷金額に適用=はい
     * 後続のルールを破棄=いいえ
     * 送料無料=一致するアイテムを含む出荷の場合
1. 別のカート価格ルールを作成：
   * 名前= *35off*
   * 優先度= 0
   * クーポン =特定のクーポン
   * クーポンコード = 35 オフ
   * アクション：
     * 適用=製品価格割引の割合
     * 割引額= 35
     * 出荷金額に適用= No
     * 後続のルールを破棄=はい
     * 送料無料=いいえ
1. ストアフロントを開き、3つの商品をカートに追加すると、小計が75 ドルを超えます。
1. ゲストとしてチェックアウトに進みます。
1. 発送手順で、**$0 - 「送料無料**」を選択し、支払い手順に進みます。
1. 支払い手順の[!UICONTROL Order Summary]を確認してください。 *[!UICONTROL $0 - Free Shipping - Free]*&#x200B;が表示されます。
1. クーポンコード *35off*&#x200B;を適用すると、小計が更新され、75 ドル未満になります。
1. 支払い手順で[!UICONTROL Order Summary]を確認してください。

<u>期待される結果</u>:

次のメッセージが表示されます：*選択した配送方法は使用できません。 この注文の別の配送方法を選択してください。*

<u>実際の結果</u>:

送料に「*まだ計算されていません*」と表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
