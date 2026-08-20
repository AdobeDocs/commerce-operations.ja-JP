---
title: ACSD-65202：マイアカウントページに、他のストアビューからの最近の注文が表示されない
description: 同じストア内の他のストアビューからの最近の注文がマイアカウントページに表示されないAdobe Commerceの問題を修正するには、ACSD-65202 パッチを適用します。
feature: Orders, User Account
role: Admin, Developer
type: Troubleshooting
exl-id: 031f12f2-1b70-4cbc-92a0-8eb561e34067
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# ACSD-65202: [!UICONTROL My Account] ページに、他のストアビューからの最近注文が表示されない

ACSD-65202 パッチは、同じストア内の他のストアビューからの最近の注文が&#x200B;**[!UICONTROL My Account]** ページに表示されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65がインストールされている場合に利用できます。 パッチ IDはACSD-65202です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p12

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

顧客アカウントページ（セクション **[!UICONTROL My Account]**）に移動すると、最近の注文が別のストアビューに表示されません。 ただし、注文履歴（セクション *[!UICONTROL My Orders]*）に移動すると、両方のストアビューにすべての注文が表示されます。

<u>複製する手順</u>:

1. Adobe Commerceをインストールします。
1. *管理者* パネルで、新しいストアビューを作成し、そのコードを&#x200B;*second*&#x200B;と入力して、ビューを識別します。
1. シンプルな商品を作成し、インデックスを再作成。
1. 顧客アカウントを作成し、コードが&#x200B;*default*&#x200B;のデフォルトストアビューで注文します。
1. **[!UICONTROL My Orders]** ページに移動し、両方のストアビューに順序が表示されていることを確認します。例：
1. デフォルト：https://localhost/pub/default/sales/order/history/
1. 2つ目：https://localhost/pub/second/sales/order/history/

1. 両方のストアビューで&#x200B;**[!UICONTROL My Account]** ページに移動します。
1. デフォルト：https://localhost/pub/default/customer/account/
1. 2つ目：https://localhost/pub/second/customer/account/

<u>期待される結果</u>:

両方のストアビューの注文は、「注文」ページで確認できます。 同じストアですが、異なるストアビューです。

<u>実際の結果</u>:

動作に一貫性がありません。 2番目のストアビューには注文は表示されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
