---
title: ACSD-60632：注文が試行されるたびに保存されるアドレス
description: ACSD-60632 パッチを適用すると、注文が正常に作成されたかどうかに関係なく、注文の試行のたびに新しいアドレスが保存されるAdobe Commerceの問題が修正されます。
feature: Orders, Products
role: Admin, Developer
exl-id: 9b623a1c-594f-47ed-82b4-d11ba20f3a58
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-60632：注文が試行されるたびに保存されるアドレス

ACSD-60632 パッチは、注文が正常に作成されたかどうかに関係なく、注文の配置が試行されるたびに新しいアドレスが保存される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51 がインストールされている場合に使用できます。 パッチ ID は ACSD-60632 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p8

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p8 - 2.4.7-p2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

注文が正常に作成されるかどうかに関係なく、注文が試行されるたびに新しいアドレスエントリがシステムに保存されます。

<u> 再現手順 </u>:

1. 支払い方法 **[!DNL PayPal Payflow Link]** 有効にする：
   * ローカルマシンでは、システムは実際の IP を持たない [!DNL PayPal Payflow Link] から API 呼び出しを受信できません。
1. シンプルな製品を作成します。
1. 住所のない登録済みの顧客を作成します。
1. 商品を買い物かごに追加します。
1. チェックアウトに進みます。
1. 住所を記入してください。 この手順で最初のアドレスが作成されていることを確認します。
1. *[!UICONTROL Review and Payments]* ページで、「**[!UICONTROL Credit Card (Payflow Link)]**」ラジオボタンを選択します。
1. **[!UICONTROL Continue]** をクリックします。
   * チェックアウトページが *[!UICONTROL Review and Payments]* ステップに戻り、事前入力されたアドレスと期待されるエラーメッセージが表示されます。
1. ラジオボタン *[!UICONTROL Credit Card (Payflow Link)]* 再度選択します。
1. 「**[!UICONTROL Continue]**」をクリックします。

<u> 期待される結果 </u>:

2 回目の注文配置の試行で新しいアドレスが作成されません。

<u> 実際の結果 </u>:

注文を行うたびに、新しい住所が作成されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ja) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [&#x200B; を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja): Search for patches[!DNL Quality Patches Tool]」を参照してください。
