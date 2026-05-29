---
title: ACSD-62475：買い物かごでのギフトカードの結合問題を修正しました
description: ACSD-62475 パッチを適用して、異なる詳細を持つギフトカード商品がカート内の1つの行項目に誤って結合されるAdobe Commerceの問題を修正します。
feature: Shopping Cart, Quotes
role: Admin, Developer
exl-id: fc97c3c0-dc1b-4546-aad0-ef3b4b6a3415
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-62475：買い物かごでのギフトカードの結合問題を修正しました

ACSD-62475 パッチでは、異なる詳細を持つギフトカード商品が、誤ってカート内の単一の行項目に結合される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56がインストールされている場合に利用できます。 パッチ IDはACSD-62475です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ユニークな送信者または受信者の詳細を含むギフトカード商品が、1つの行の項目に誤ってマージされ、データが不整合します。

<u>複製する手順</u>:

1. 次の設定で[!UICONTROL Gift Card]製品を作成します。
   * **[!UICONTROL Card Type]**: [!UICONTROL Virtual]
   * **[!UICONTROL Amount]**: 10

1. ストアフロントで新しいユーザーを作成し、ログインします。

1. 以下の詳細を記載したギフトカード商品をカートに追加します。
   * **[!UICONTROL Sender Name]**：送信者1
   * **[!UICONTROL Sender Email**]: sender1@test.com
   * **[!UICONTROL Recipient Name**]：受信者1
   * **[!UICONTROL Recipient Email**]: recipient1@test.com


1. ログアウト

1. 同じギフトカード商品をカートに追加し、以下の詳細を記載します。
   * **[!UICONTROL Sender Name]**：送信者2
   * **[!UICONTROL Sender Email**]: sender2@test.com
   * **[!UICONTROL Recipient Name**]：受信者2
   * **[!UICONTROL Recipient Email**]: recipient2@test.com

1. 再度ログインして、カートを確認します。

<u>期待される結果</u>:

両方のギフトカードは、それぞれの詳細を含む2つの別々のラインアイテムとして表示されます。

<u>実際の結果</u>:

ギフトカードは、1行目の項目にマージされ、数量は2で、最初のギフトカードの詳細が保持されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
