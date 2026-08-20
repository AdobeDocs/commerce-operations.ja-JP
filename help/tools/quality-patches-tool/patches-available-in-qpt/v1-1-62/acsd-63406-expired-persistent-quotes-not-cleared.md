---
title: ACSD-63406:persistent_clear_expired cron ジョブの実行時に期限切れの永続的な引用符がクリアされない
description: ACSD-63406 パッチを適用して、「persistent_clear_expired」 cron ジョブの実行時に、期限切れの永続的な引用符がcron ジョブによってクリアされないAdobe Commerceの問題を修正します。
feature: Quotes, Shopping Cart
role: Admin, Developer
exl-id: 795d1ddf-0d5b-406c-870b-36cb92cf07fa
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-63406: `persistent_clear_expired` cron ジョブの実行時に期限切れの永続的な引用符がクリアされない

ACSD-63406 パッチは、`persistent_clear_expired` cron ジョブの実行時に、期限切れの永続的な引用符がcron ジョブによってクリアされない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62がインストールされている場合に利用できます。 パッチ IDはACSD-63406です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.4.4-p9 - 2.4.4-p12、2.4.5-p8 - 2.4.5-p11、2.4.6-p6 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

期限切れの永続的な引用符は、`persistent_clear_expired` cron ジョブの実行時にcron ジョブによってクリアされません。

<u>複製する手順</u>:

1. カテゴリと製品の作成。
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]**&#x200B;に移動します。
   1. すべてのオプションを&#x200B;*はい*&#x200B;に設定します。
   1. **[!UICONTROL Persistence Lifetime (seconds)]**&#x200B;を&#x200B;*60*&#x200B;に設定します。
1. ストアフロントで顧客アカウントを作成し、ログインします。
1. 商品をカートに追加する。
1. ログアウトし、60秒待ってから、再度ログインします。

<u>期待される結果</u>:

`persistent_clear_expired` cron ジョブは、設定の永続性有効期間の設定に基づいて、永続的な引用符を削除する必要があります。

<u>実際の結果</u>:

顧客の見積の`is_persistent`値は、見積テーブルの&#x200B;*1*&#x200B;のままです。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
