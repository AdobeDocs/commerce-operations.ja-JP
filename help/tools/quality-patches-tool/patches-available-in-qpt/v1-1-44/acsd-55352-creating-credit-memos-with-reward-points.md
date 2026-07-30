---
title: ACSD-55352：報酬ポイントを使用したクレジットメモの作成
description: ACSD-55352 パッチを適用して、Adobe Commerceの問題を修正します。お客様の報酬ポイントを含む部分的なクレジットメモを作成した後、注文状況が*クローズ*に変わり、クレジットメモのオプションが管理者注文ページから消えます。
feature: Checkout, Orders
role: Admin, Developer
exl-id: bee0c4be-11ec-4dcb-9b3c-7af26676cee9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# ACSD-55352：報酬ポイントを使用したクレジットメモの作成

ACSD-55352 パッチでは、顧客報酬ポイントを含む部分的なクレジットメモを作成した後、注文状況が&#x200B;*クローズ*&#x200B;に変更され、クレジットメモのオプションが管理者注文ページから消える問題が修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44がインストールされている場合に利用できます。 パッチ IDはACSD-55352です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

顧客報酬ポイントを含む部分的なクレジットメモを作成すると、注文状況が&#x200B;*クローズ*&#x200B;に変更され、管理者注文ページからクレジットメモのオプションが表示されなくなります。

<u>複製する手順</u>:

1. Adobe Commerce Adminにログインします。
2. **[!UICONTROL Stores]** > **[!UICONTROL Other Setting]** > **[!UICONTROL Reward Exchange Rates]** > **[!UICONTROL Add New Rate]**&#x200B;に移動します。
3. 2つのレートを追加：
   * *[!UICONTROL First]*:
     * *[!UICONTROL Direction]* = *通貨に対するポイント*
     * *[!UICONTROL Rate]* = *100*
     * *[!UICONTROL Upper Boundary]* = *100*
   * *[!UICONTROL Second]*:
     * *[!UICONTROL Direction]* = *ポイントへの通貨*
     * *[!UICONTROL Rate]* = *100*
     * *[!UICONTROL Upper Boundary]* = *100*
4. 価格が&#x200B;*$100*&#x200B;で、*数量* : *100*&#x200B;のシンプルな商品を作成します。
5. ストアフロントから顧客を作成する。
6. バックエンドに再度移動します：**[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit]** > **[!UICONTROL Reward Points]** > **[!UICONTROL Update Points]** > *100*&#x200B;を追加して、お客様を保存します。
7. ストアフロントに移動し、以前に作成したお客様としてログインします。
8. 商品をカートに追加する条件：*数量* : *10*
9. **[!UICONTROL Checkout]**&#x200B;に移動し、プロンプトが表示されたときに利用可能な&#x200B;*100*&#x200B;の報酬ポイントを使用して、注文を行います。
10. **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice]**&#x200B;に移動して、その注文を発送します。
11. [!UICONTROL Credit Memo]に移動し、*数量から返金*&#x200B;を&#x200B;*8*&#x200B;に更新します。
12. 「**[!UICONTROL Refund Reward Points]**」チェックボックスをオンにし、「**[!UICONTROL Refund offline]**」をクリックします。
13. 注文の残りの2つの商品を[!UICONTROL Credit Memo]を使用して返金してみてください。

<u>期待される結果</u>:

* 管理者は、残りの2つの製品を返すために[!UICONTROL Credit Memo]を作成します。
* 注文ステータスは&#x200B;*完了*&#x200B;です。

<u>実際の結果</u>:

* [!UICONTROL Credit Memo]個を作成できません。
* 注文ステータスは&#x200B;*クローズ*&#x200B;です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
