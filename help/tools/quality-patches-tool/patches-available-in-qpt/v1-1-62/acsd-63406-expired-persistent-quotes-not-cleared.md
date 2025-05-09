---
title: 'ACSD-63406: persistent_clear_expired cron ジョブの実行時に期限切れの永続的な引用符がクリアされない'
description: 「persistent_clear_expired」 cron ジョブが実行されたときに、期限切れの永続的な引用符が cron ジョブでクリアされないAdobe Commerceの問題を修正するために、ACSD-63406 パッチを適用します。
feature: Quotes, Shopping Cart
role: Admin, Developer
source-git-commit: b3bb6ae825f4912b19e2d1f88b5d55835d9769ff
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---


# ACSD-63406:Cron ジョブの実行時に、期限切れの永続的な引用符がクリア `persistent_clear_expired` れない

ACSD-63406 パッチは、`persistent_clear_expired` cron ジョブが実行されたときに、期限切れの永続的な引用符が cron ジョブによってクリアされない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 がインストールされている場合に使用できます。 パッチ ID は ACSD-63406 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p9 - 2.4.4-p12、2.4.5-p8 - 2.4.5-p11、2.4.6-p6 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

期限切れの永続的な引用符は、`persistent_clear_expired` cron ジョブの実行時にいずれの cron ジョブでもクリアされません。

<u> 再現手順 </u>:

1. カテゴリと製品を作成します。
1. **[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Customers]**/**[!UICONTROL Persistent Shopping Cart]** に移動します。
   1. すべてのオプションを *はい* に設定します。
   1. **[!UICONTROL Persistence Lifetime (seconds)]** を *60* に設定します。
1. ストアフロントで顧客アカウントを作成し、ログインします。
1. 商品を買い物かごに追加します。
1. ログアウトし、60 秒待ってから、もう一度ログインします。

<u> 期待される結果 </u>:

`persistent_clear_expired` cron ジョブでは、設定の永続性有効期間の設定に基づいて、永続的な引用符を削除する必要があります。

<u> 実際の結果 </u>:

顧客の見積もりの `is_persistent` 値は、見積もりテーブルに *1* 残ります。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
