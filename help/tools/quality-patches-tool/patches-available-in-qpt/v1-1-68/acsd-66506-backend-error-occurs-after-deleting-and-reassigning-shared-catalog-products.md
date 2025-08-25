---
title: ACSD-66506：共有カタログ製品を削除して再割り当てした後に、バックエンドエラーが発生する
description: ACSD-66506 パッチを適用して、バックエンドがエラーをスローするAdobe Commerceの問題を修正してください。 以前に割り当てた製品を削除し、新しい製品を共有カタログに割り当ててから、製品を確認して再試行してください*。
feature: B2B
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8f77101832ccfb415d040c202f0fc7221f97419a
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---


# ACSD-66506：共有カタログ製品を削除して再割り当てした後に、バックエンドエラーが発生する

ACSD-66506 パッチは、バックエンドが *リクエストされた製品が存在しない。 以前に割り当てた製品を削除し* 新しい製品を共有カタログに割り当ててから、製品を確認して、もう一度試してください。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 がインストールされている場合に使用できます。 パッチ ID は ACSD-66506 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

以前に割り当てた製品を削除し、新しい製品を **[!UICONTROL Shared Catalog]** に割り当てると、バックエンドが次のエラーを返します。*リクエストされた製品が存在しません。 製品を確認して、もう一度試してください*

<u> 再現手順 </u>:

1. パフォーマンス・ツールキットを使用して製品を作成します。`bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`
1. **[!UICONTROL [!DNL B2B] Features]** Configuration に移動し、**[!UICONTROL Enable Company]** を設定し、**[!UICONTROL Enable Shared Catalog]** を `Yes` に設定します。
1. 新しい共有カタログを作成します。
1. 生成されたすべての製品を、新しく作成した共有カタログに割り当てます。
1. 共有カタログに割り当てられた製品を削除するには、**[!UICONTROL Product Import]** を使用します。
   1. SKU でフィルターされた製品のエクスポート。
   1. **[!UICONTROL Import Behavior: Delete]** を選択してから、同じファイルを読み込みます。
1. **[!UICONTROL Shared Catalog]** を開き、価格と構造を設定します。
   1. 「**[!UICONTROL Set Pricing and Structure]**」を選択します。
   1. 「**[!UICONTROL Next]**」をクリックし、「**[!UICONTROL Generate Catalog]**」をクリックします。
   1. 「**[!UICONTROL Save]**」をクリックします。

<u> 期待される結果 </u>:

エラーは発生せず、エラーが発生しても製品は共有カタログに残ります。

<u> 実際の結果 </u>:

エラーが発生しました：*リクエストされた製品が存在しません。 製品を確認して再試行すると* すべての製品が共有カタログから削除されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
