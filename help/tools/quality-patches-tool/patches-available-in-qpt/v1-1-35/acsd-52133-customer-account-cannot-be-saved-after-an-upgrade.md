---
title: 「ACSD-52133：アップグレード後に顧客アカウントを保存できない」
description: ACSD-52133 パッチを適用すると、アップグレード後にカスタマーアカウントを保存できないAdobe Commerceの問題を修正できます。
feature: Customers, Upgrade
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-52133：アップグレード後に顧客アカウントを保存できない

ACSD-52133 パッチにより、アップグレード後にカスタマーアカウントを保存できない問題が修正されました。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.35 がインストールされている場合に使用できます。 パッチ ID は ACSD-52133 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

アップグレード後に顧客アカウントを保存することはできません。

<u> 再現手順 </u>:

1. Adobe Commerce バージョン 2.4.4 をインストールします。
1. 顧客を作成します。
1. Adobe Commerceを、お客様が既に作成されている以前のバージョンの 2.4.4 から 2.4.6 にアップグレードします。
1. 暗号化キーを次のように設定します `env.php`。

   `d337b914e91ff703b1e94ba4156aadf0`

1. `customer_entity` テーブルの下の任意の顧客について、データベースに以下の値を設定します。

   ```
   -> rp_token as incr4869
   -> rp_token_created_at as "2021-04-29 20:06:14"
   ```

1. **[!UICONTROL Admin]**/**[!UICONTROL Customers]**/**[!UICONTROL All Customers]** に移動します。
1. 上記の値を更新した顧客を編集します。
1. **[!UICONTROL Save Customer]** または **[!UICONTROL Save and Continue Edit]** をクリック

<u> 期待される結果 </u>:

顧客はエラーなしで正常に保存されました。

<u> 実際の結果 </u>:

* 顧客レコードは保存されません。
* *顧客の保存中に問題が発生しました。* というエラーメッセージが管理者に表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
