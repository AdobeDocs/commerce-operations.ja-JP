---
title: ACSD-53704：報酬ポイントのバランス履歴が有効期限後に計算されません
description: ACSD-53704 パッチを適用すると、報酬ポイントの有効期限が切れた後に報酬ポイントのバランス履歴が誤って計算されるAdobe Commerceの問題を修正できます。
feature: Rewards
role: Admin, Developer
exl-id: 8cd297cc-9e9d-4615-b817-283065a79c2f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-53704：報酬ポイントのバランス履歴が有効期限後に計算されません

ACSD-53704 パッチは、報酬ポイントの有効期限が切れた後に報酬ポイントのバランス履歴が誤って計算される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.39 がインストールされている場合に使用できます。 パッチ ID は ACSD-53704 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

報酬ポイントの残高履歴は、報酬ポイントの有効期限後に誤って計算される。

<u> 再現手順 </u>:

1. ストアフロントで顧客を作成します。
1. 有効期限が異なる顧客の報酬ポイントを追加します。
1. `magento_reward_history` テーブルを確認し、報酬ポイントの最新レコードの有効期限を過去の日付に設定します。

   ```
   UPDATE magento_reward_history SET expired_at_static = '2023-08-24 10:47:38' WHERE history_id = 3;
   ```

1. **[!UICONTROL Admin]**/**[!UICONTROL Customers]**/**[!UICONTROL All Customers]**/**[!UICONTROL Edit customer]**/**[!UICONTROL Reward points]**/**[!UICONTROL Reward Points History]** および **[!UICONTROL Reward Points Balance]** の報酬履歴グリッドを確認します。

<u> 期待される結果 </u>:

報酬ポイントの残高には、有効期限が切れていないポイントのみが表示されます。

<u> 実際の結果 </u>:

報酬ポイントの残高には、有効期限切れのポイントが含まれる金額が反映されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドの
* クラウドインフラストラクチャー上のAdobe Commerce:[ アップグレードとパッチ適用 ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) クラウドインフラストラクチャー上のCommerce ガイド

## 関連資料

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースに追加しました
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）
* Commerce実装プレイブックの [ データベーステーブルを変更する際のベストプラクティス ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)

QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
