---
title: ACSD-59930：会社のフローのパフォーマンスを向上させます
description: ACSD-59930 パッチを適用すると、アドレス帳に*1000+* アドレスを持つ管理者の会社を作成、保存または削除する際に、管理パネルに*Timeout* エラーが表示されるAdobe Commerceの問題を修正できます。
feature: Customers, B2B
role: Admin, Developer
exl-id: eaa6c78d-13e3-439d-90f7-70c1c96c3197
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-59930：会社のフローのパフォーマンスを向上させます

ACSD-59930 パッチを使用すると、アドレス帳に *1000+* を超えるアドレスを持つ管理者の会社を作成、保存または削除する際に、管理パネルに *タイムアウト* エラーが表示される問題を修正できます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.53 がインストールされている場合に使用できます。 パッチ ID は ACSD-59930 です。 この問題は、Adobe Commerce B2B-1.5.0 で修正される予定です。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p4

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

会社の作成、保存および削除フローのパフォーマンスを向上させます。

<u> 前提条件：</u>:

Adobe Commerce B2B モジュールをインストールして有効にします。

<u> 再現手順 </u>:

1. *で* 1000 以上の *[!UICONTROL Address Book]* アドレスを持つ顧客を作成します。
1. 会社を作成し、上記の顧客を管理者として使用します。
1. 会社を保存します。

<u> 期待される結果 </u>:

会社は正常に作成され、タイムアウトエラーは表示されません。

<u> 実際の結果 </u>:

タイムアウトエラーが表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
