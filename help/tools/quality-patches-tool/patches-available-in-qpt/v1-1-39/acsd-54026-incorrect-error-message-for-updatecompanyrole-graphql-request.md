---
title: ACSD-54026:updateCompanyRole GraphQL リクエストに対して誤ったエラーメッセージ
description: ACSD-54026 パッチを適用して、許可されていないユーザーに対する updateCompanyRole GraphQL リクエストに間違ったエラーメッセージが表示されるAdobe Commerceの問題を修正してください。
feature: Roles/Permissions
role: Admin, Developer
exl-id: 21695333-5f18-48db-acde-246f269dd691
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-54026:GraphQL リクエストに対する誤っ `updateCompanyRole` エラーメッセージ

ACSD-54026 パッチは、許可されていないユーザーに対する `updateCompanyRole` GraphQL リクエストで誤ったエラーメッセージが表示される問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.39 がインストールされている場合に使用できます。 パッチ ID は ACSD-54026 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

許可されていないユーザーに対する `updateCompanyRole` GraphQL リクエストで、誤ったエラーメッセージが表示される。

<u> 再現手順 </u>:

1. 設定で B2B 会社を有効にします。
1. 会社を作成します。
1. ベアラートークンを渡さずに、または無効なベアラートークンを指定して、`updateCompanyRole` GraphQL リクエストを送信します。
1. GraphQL応答でエラーメッセージを確認します。

<u> 期待される結果 </u>:

次のエラーメッセージが表示されます。*現在の顧客は承認されていません。*

<u> 実際の結果 </u>:

「*顧客は会社ユーザーではありません。* というエラーメッセージが表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
