---
title: ACSD-49389：受け取りの準備が整っていない場合に API から送信される受け取りの準備ができたメール
description: ACSD-49389 パッチを適用すると、注文の受け取りの準備が整っていない場合に、API から受け取り準備完了のメールが送信されるAdobe Commerceの問題が修正されます。
feature: REST, Communications
role: Admin
exl-id: d1bc430a-3021-40d1-9091-db8ed9125619
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-49389：受け取りの準備が整っていない場合に API から送信される受け取りの準備ができたメール

ACSD-49389 パッチは、注文が集荷の準備ができていない場合に、API によって集荷準備完了のメールが送信される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 がインストールされている場合に使用できます。 パッチ ID は ACSD-49389 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがお使いのAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[QPT ランディングページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

注文が受け取り準備ができていない場合、受け取り準備が整ったメールが API から送信されます。

<u> 再現手順 </u>:

1. メソッド *[!UICONTROL In-Store Delivery]* 有効にします。
1. 集荷場所が有効な在庫ソースを作成します。
1. 上記で作成したソースを使用して、メイン web サイトを使用して新しい在庫を作成します。
1. 同じソースを割り当てる商品を作成します。
1. 在庫数量= 1 を設定します。
1. ストアフロントから *[!UICONTROL In-Store Delivery]* メソッドを使用して、手順 4 で作成した製品をチェックアウトします。
1. 注文の請求書を作成します。
1. 製品の数量を *0* に設定して、在庫切れにします。
1. 次の API リクエストを投稿します。

```
{
    "orderIds": [
        1
    ]
}
```

<u> 期待される結果 </u>:

集荷準備完了の E メールは送信されません。

<u> 実際の結果 </u>:

API が返ります *注文は受け取りの準備ができていません* が、受け取りの準備が整ったメールが送信されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの [QPT で使用可能なパッチ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) を参照してください。
