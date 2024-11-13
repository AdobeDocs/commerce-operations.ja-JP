---
title: 「ACSD-60804：削除された会社に関連付けられている顧客を編集すると、エラーが発生する」
description: 削除された会社に関連付けられたカスタマーを編集すると、*null のメンバー関数 getSuperUserId （）の呼び出し*が発生するAdobe Commerceの問題を修正するために、ACSD-60804 パッチを適用します。
feature: Companies, Customers, B2B
role: Admin, Developer
source-git-commit: 1231dac065565ff636424673a15ae4148a5f84dd
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-60804：削除された会社に関連付けられている顧客を編集すると、エラーが発生する

ACSD-60804 パッチでは、削除された会社に関連付けられた顧客を編集すると、エラー *メンバー関数 getSuperUserId （）の null での呼び出し* が発生する問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 がインストールされている場合に使用できます。 パッチ ID は ACSD-60804 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

削除された会社に関連付けられている顧客を編集すると、エラー *メンバー関数 getSuperUserId （）の null での呼び出し* が発生します。

<u> 前提条件：</u>:

Adobe Commerce B2B モジュールをインストールして有効にします。

<u> 再現手順 </u>:

1. **[!UICONTROL Settings]**/**[!UICONTROL B2B]**/**[!UICONTROL Enable Company]** に移動します。
1. **[!UICONTROL Customers]**/**[!UICONTROL Company]**/**[!UICONTROL Create New Company]** に移動します。
1. インスタンスの `mysql` にログインします。
1. `entity_id` = *1* の会社を削除します。
1. **[!UICONTROL Customers]**/**[!UICONTROL All Customers]** に移動します。
1. 会社の作成時に自動的に作成された顧客を編集します。

<u> 期待される結果 </u>:

顧客は編集されますが、例外エラーはスローされません。

<u> 実際の結果 </u>:

エラーが発生します。*会社が顧客に関連付けられていない場合に* null のメンバー関数 getSuperUserId （）の呼び出し。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
