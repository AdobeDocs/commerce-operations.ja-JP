---
title: ACSD-65223:B2B発注の手動で選択した条件と契約書がエラーになる
description: チェックアウトに利用条件が必要な場合、[!UICONTROL Purchase Orders]を使用して作成された注文をクレジットカードなどのオンライン支払い方法で完了できないAdobe Commerceの問題を修正するには、ACSD-65223 パッチを適用します。
feature: B2B, Purchase Orders
role: Admin, Developer
exl-id: 5a5d0774-3801-4688-86bd-58a390394cc0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# ACSD-65223:B2B発注の手動で選択した条件と契約書がエラーになる

ACSD-65223 パッチでは、**[!UICONTROL Purchase Orders]**&#x200B;を使用して作成された注文を、チェックアウトに利用条件が必要な場合に、クレジットカードなどのオンライン支払い方法で完了できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64がインストールされている場合に利用できます。 パッチ IDはACSD-65223です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） B2B 1.5.1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） B2B 1.5.1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

注文に利用条件が必要で、[!UICONTROL Purchase Orders]を使用して作成された注文を確定しようとしている場合、クレジットカードなどのオンライン支払い方法を使用して注文を行うことはできません。

<u>複製する手順</u>:

1. シンプルな商品の作成。
1. **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]**&#x200B;に移動し、**[!UICONTROL B2B Features]**&#x200B;を選択します。
1. **[!UICONTROL Enable Company]**&#x200B;と&#x200B;**[!UICONTROL Enable Purchase Orders]**&#x200B;を&#x200B;*はい*&#x200B;に設定します。
1. **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Terms and Conditions]**&#x200B;に移動し、新しい条件を作成します。 **[!UICONTROL Applied]**&#x200B;を&#x200B;*[!UICONTROL Manually]*&#x200B;に設定します。
1. **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]**&#x200B;に移動し、**[!UICONTROL Enable Terms and Conditions]**&#x200B;を&#x200B;*はい*&#x200B;に設定します。
1. **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payment Methods]**&#x200B;に移動し、[!DNL Braintree]を設定します。
1. ストアフロントで会社を作成します。
1. 管理画面で、**[!UICONTROL Customers]** > **[!UICONTROL Companies]**&#x200B;に移動します。
1. 会社を承認し、**[!UICONTROL Purchase Orders]**&#x200B;を許可します。
1. フロントエンドで、アカウントにログインします。
1. カートに商品を追加します。
1. **[!UICONTROL Purchase Order]**&#x200B;を使用して注文します。
1. 顧客ダッシュボードで、「**[!UICONTROL Purchase Orders]**」タブをクリックします。
1. 新しい発注から注文を作成します。 次に、支払い方法としてクレジットカードを選択します。
1. 利用条件に同意する：
1. 注文する。

<u>期待される結果</u>:

チェックアウトに利用条件が必要な場合、承認された発注書でオンライン支払い方法を使用して注文することができます。

<u>実際の結果</u>:

チェックアウトに利用条件が必要な場合、承認された発注書でオンライン支払い方法を使用して注文することはできません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
