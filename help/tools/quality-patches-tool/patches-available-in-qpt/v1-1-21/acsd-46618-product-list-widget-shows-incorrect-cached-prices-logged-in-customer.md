---
title: ACSD-46618：製品リストウィジェットに、ログインした顧客に対して正しくないキャッシュ価格が表示される
description: ログインしているお客様の商品リストウィジェットに誤ったキャッシュ価格が表示されるAdobe Commerceの問題を修正するために、パッチを適用します。
feature: Cache, Orders, Products
role: Admin
exl-id: fa350f84-2fe5-474b-b4fd-d6c1e8bb0f95
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-46618：製品リストウィジェットに、ログインした顧客に対して正しくないキャッシュ価格が表示される

ACSD-46618 パッチを使用すると、ログインしている顧客の製品リストウィジェットに誤ったキャッシュ価格が表示される問題を解決できます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html?lang=ja) 1.1.21 がインストールされている場合に使用できます。 パッチ ID は ACSD-46618 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.5

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ACSD-46618 パッチを使用すると、ログインしている顧客の製品リストウィジェットに誤ったキャッシュ価格が表示される問題を解決できます。

<u> 再現手順 </u>:

1. Adobe Commerce管理者で、「**[!UICONTROL Stores]**」を選択してから「**[!UICONTROL Configuration]**」を選択し、「**[!UICONTROL Sales]**」を展開して「**[!UICONTROL Tax]**」を選択します。 税金設定を更新して、税金を含む価格と税金を除外する価格を表示します。
1. **[!UICONTROL Enable Cross Border Trade]** = _はい_ を設定します。
1. 米国にのみ適用される税務処理基準を作成します。
1. 複数の製品を含むホームページにウィジェットを追加します。
1. 米国住所と米国以外の住所を持つ 2 つの顧客を作成します。
1. ストアフロントから米国の顧客を使用してログインします。 ページがキャッシュされていることを確認します。
1. ホームページウィジェットに表示される価格を確認します。
1. 米国以外のお客様がログアウトしてログインします。

<u> 期待される結果 </u>:

ホームページウィジェットに表示される価格は、顧客の住所に対応しています。

<u> 実際の結果 </u>:

ホームページ ウィジェットには、米国以外の顧客の価格が税金を使用して表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [&#x200B; を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja): Search for patches[!DNL Quality Patches Tool]」を参照してください。
