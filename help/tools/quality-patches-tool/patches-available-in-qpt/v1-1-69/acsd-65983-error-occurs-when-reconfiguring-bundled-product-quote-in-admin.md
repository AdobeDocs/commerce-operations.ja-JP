---
title: ACSD-65983：管理者でバンドルされた製品見積もりを再設定するとエラーが発生する
description: ACSD-65983 パッチを適用すると、バックエンドの [!UICONTROL Sales] > [!UICONTROL Quotes] > [!UICONTROL Edit] 画面でバンドル製品を設定しようとするとエラーが表示されるAdobe Commerceの問題を修正できます。
feature: B2B, Quotes
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8a8f2b273bcbcf135677ad7ca289398bf660e02e
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---


# ACSD-65983：管理者でバンドルされた製品見積もりを再設定するとエラーが発生する

ACSD-65983 パッチでは、バンドルされた製品見積もりを管理バックエンドで再設定するとエラーが返される問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 がインストールされている場合に使用できます。 パッチ ID は ACSD-65983 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

バンドルされた製品見積もりを管理バックエンドで再設定すると、エラーが返されます。

<u> 再現手順 </u>:

1. 管理パネルに移動し、**[!UICONTROL B2B Feature]**/**[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL General]** の **[!UICONTROL B2B Feature]** を有効にします。
1. 固定金額のバンドル製品（例：*$10*）を作成し、*0* 金額、*オプション 1* の **2** および *オプション 2* の **その他** を持つ 3 つ以上のシンプルな製品を追加します。
1. フロントエンドから会社アカウントを作成します。
1. **[!UICONTROL Catalog]**/**[!UICONTROL Shared Catalogs]** に移動し、作成した会社と製品を新規/カスタムの共有カタログに割り当てます。
1. フロントエンドで **会社ユーザー** としてログインし、1 つのシンプルな製品をバンドルから買い物かごに追加します。
1. 買い物かごページを開き、**見積もり依頼** として送信します。
1. バックエンドに移動し、作成した引用符を編集します。
1. 「**見積品目**」セクションで、「**構成**」ボタンをクリックします。
1. **オプション 2** から別のシンプルな製品を選択します。
1. 次に、「**OK**」ボタンをクリックして、エラーメッセージを表示します。

<u> 期待される結果 </u>:

管理者から要求された見積依頼項目を正常に構成できますが、エラーメッセージは表示されません。

<u> 実際の結果 </u>:

次のエラーメッセージが表示されます。

*サーバーの技術的な問題によりエラーが発生しました。 やり直して、今までの作業を続けてください。 問題が解決しない場合は、後でもう一度試してください。*

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドの
* クラウドインフラストラクチャー上のAdobe Commerce:[ アップグレードとパッチ適用 ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja) クラウドインフラストラクチャー上のCommerce ガイド

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]：品質向上パッチを適用するためのセルフサービス ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) ツール（『ツールガイド』）
