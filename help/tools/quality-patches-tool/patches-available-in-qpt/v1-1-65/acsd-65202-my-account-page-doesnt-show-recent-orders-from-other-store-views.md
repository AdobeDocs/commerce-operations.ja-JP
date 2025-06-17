---
title: 'ACSD-65202: マイアカウントページに、他のストアビューからの最近の注文が表示されない'
description: ACSD-65202 パッチを適用すると、マイアカウント ページに同じストア内の他のストアビューからの最近の注文が表示されないAdobe Commerceの問題を修正できます。
feature: Orders, User Account
role: Admin, Developer
source-git-commit: 0af6ab4ef15e8aa56354886b341b70a080662eae
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---


# ACSD-65202:[!UICONTROL My Account] ページに他のストア ビューからの最近の注文が表示されない

ACSD-65202 パッチにより、**[!UICONTROL My Account]** ページに同じストア内の他のストアビューからの最近の注文が表示されない問題が修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 がインストールされている場合に使用できます。 パッチ ID は ACSD-65202 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p12

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

顧客アカウントページ（セクション **[!UICONTROL My Account]**）に移動すると、別のストア表示に最近の注文が表示されません。 ただし、注文履歴（セクション *[!UICONTROL My Orders]*）に移動すると、両方のストアビューにすべての注文が表示されます。

<u> 再現手順 </u>:

1. Adobe Commerceをインストールします。
1. *管理* パネルで、新しいストアビューを作成し、そのコードを *second* として入力して、ビューを識別します。
1. シンプルな製品を作成して、インデックスを再作成します。
1. 顧客アカウントを作成し、デフォルトのストア表示でコードを *デフォルト* して注文します。
1. **[!UICONTROL My Orders]** ページに移動し、両方のストア表示に注文が表示されていることを確認します。次に例を示します。
1. デフォルト：https://localhost/pub/default/sales/order/history/
1. 2 番目：https://localhost/pub/second/sales/order/history/

1. 両方のストア表示で **[!UICONTROL My Account]** ページに移動します。
1. デフォルト：https://localhost/pub/default/customer/account/
1. 2 番目：https://localhost/pub/second/customer/account/

<u> 期待される結果 </u>:

注文は、両方のストア表示の注文ページで確認できます。 同じ店舗で、単に別の店舗ビューです。

<u> 実際の結果 </u>:

動作が一貫していません。 注文は 2 番目のストア表示には表示されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
