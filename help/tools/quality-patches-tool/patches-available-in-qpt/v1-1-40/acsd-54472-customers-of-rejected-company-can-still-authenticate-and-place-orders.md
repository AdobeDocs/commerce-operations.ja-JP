---
title: ACSD-54472：拒否された会社の顧客は、引き続き認証できます
description: ACSD-54472 パッチを適用すると、拒否された会社の顧客は引き続き認証でき、ブロックおよび拒否された会社の顧客は引き続き注文できるAdobe Commerceの問題を修正できます。
feature: B2B
role: Admin, Developer
exl-id: c0bd960f-609b-4253-9fc8-dc47fbbddc93
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# ACSD-54472：拒否された会社の顧客は、引き続き認証できます

ACSD-54472 パッチは、拒否された会社の顧客が引き続き認証でき、ブロックされて拒否された会社の顧客が引き続き注文できる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40 がインストールされている場合に使用できます。 パッチ ID は ACSD-54472 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

拒否された会社の顧客は引き続き認証でき、ブロックされて拒否された会社の顧客は引き続き注文できます。

<u> 再現手順 </u>:

1. 会社を作成します。
1. [!DNL GraphQL] を使用して商品を買い物かごに追加します。
1. 会社ステータスを *ブロック* に変更します。
1. 注文を行い、譲渡可能な見積もりを作成するための [!DNL GraphQL] リクエストを送信します。
1. 会社のステータスを *却下* に変更します。
1. 会社のユーザー認証トークンを取得するための [!DNL GraphQL] リクエストを送信します。
1. 顧客ステータスを *非アクティブ* に設定します。
1. 会社のユーザー認証トークンを取得するための [!DNL GraphQL] リクエストを送信します。

<u> 期待される結果 </u>:

* 注文および交渉可能な見積もりは、*ブロック* 会社のユーザーによって行われていません。
* *却下* 会社のユーザーに対する認証トークンが取得されていません。
* *非アクティブ* 顧客の認証トークンが取得されていません。

<u> 実際の結果 </u>:

* 注文および交渉可能な見積もりは、*ブロック* 会社のユーザーによって行われます。
* 認証トークンは、*却下* 会社のユーザーについて取得されます。
* 認証トークンは、「非アクティブ *な顧客に対して取得され* す。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
