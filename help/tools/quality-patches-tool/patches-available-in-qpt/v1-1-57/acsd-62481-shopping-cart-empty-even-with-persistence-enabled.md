---
title: ACSD-62481:[!UICONTROL Persistence] が有効になっている場合でも、買い物かごは空のままです
description: チェックアウト時にログインポップアップを使用すると永続的な買い物かご機能が失敗するAdobe Commerceの問題を修正するために、ACSD-62481 パッチを適用してください。
feature: Shopping Cart, Checkout
role: Admin, Developer
exl-id: 79fb3161-f56e-45f3-9933-cf95703f1554
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-62481:*[!UICONTROL Persistence]* が有効になっている場合でも、買い物かごは空のままです

ACSD-62481 パッチでは、チェックアウト時にログインポップアップを使用すると、*[!UICONTROL Remember Me]* のチェックボックスが表示されず、永続的な買い物かご機能が失敗し、ログアウト後に製品が買い物かごから消える問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 がインストールされている場合に使用できます。 パッチ ID は ACSD-62481 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

チェックアウト時にログインポップアップを使用すると、*[!UICONTROL Remember Me]* のチェックボックスがないので、永続的な買い物かご機能が失敗します。 これにより、製品がサインアウト後に買い物かごから消えます。

<u> 再現手順 </u>:

1. 管理者で、guest アカウントと永続的な買い物かごの設定を次のように設定します。

   * **[!UICONTROL Stores]**/**[!UICONTROL Settings]**/**[!UICONTROL Configuration]**/**[!UICONTROL Sales]**/**[!UICONTROL Checkout]**/**[!UICONTROL Checkout Options]** に移動し、「*[!UICONTROL Allow Guest Checkout]*」を「*いいえ*」に設定します。

      * 「**[!UICONTROL Save Config]**」をクリックします。

   * **[!UICONTROL Stores]**/**[!UICONTROL Settings]**/**[!UICONTROL Configuration]**/**[!UICONTROL Customers]**/**[!UICONTROL Persistent Shopping Cart]**/**[!UICONTROL General Options]** に移動し、「*[!UICONTROL Enable Persistence]*」を「*はい*」に設定します。
   * その他の設定はすべてデフォルトのままにしますが、*[!UICONTROL Clear Persistence on Sign Out]* を *いいえ* に変更します。

      * 「**[!UICONTROL Save Config]**」をクリックします。

1. **[!UICONTROL Catalog]**/**[!UICONTROL Products]**/**[!UICONTROL Add product]** に移動して、カタログに簡単な製品を追加します。

   * 必要最小限の詳細を入力し、在庫があることを確認します。

1. フロントエンドで、メインフォームフ `(../customer/account/create/)` ールドを使用して顧客アカウントを作成し、ログアウトします。
1. 製品をゲストとして買い物かごに追加します。
1. 右上のアイコンでミニカートを開き、「**[!UICONTROL View and Edit Cart]**」をクリックします。
1. チェックアウトに進みます。
1. 表示されるポップアップダイアログから新しい顧客アカウントにログインし、ログアウトします。

<u> 期待される結果 </u>:

買い物かごには、以前にログインしたユーザーの製品が保持されます。

<u> 実際の結果 </u>:

* カートは空です。
* ポップアップログインダイアログに「*[!UICONTROL Remember Me]*」オプションが表示されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* Adobe Commerce on Cloud Infrastructure: アップグレードとパッチ > Commerce on Cloud Infrastructure ガイドのパッチの適用

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
