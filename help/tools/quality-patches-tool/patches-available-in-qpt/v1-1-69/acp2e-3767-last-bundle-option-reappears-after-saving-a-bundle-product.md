---
title: ACP2E-3767：バンドル製品を保存すると、最後のバンドルオプションが再び表示される
description: ACP2E-3767 パッチを適用して、バンドル製品の最後のバンドルオプションを削除できないAdobe Commerceの問題を修正します。
feature: Products, Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: f39442925d9cc82087af9e84d91137a0fcd0ec14
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# ACP2E-3767：バンドル製品を保存すると、最後のバンドルオプションが再び表示される

ACP2E-3767 パッチは、バンドル製品を保存した後に最後のバンドルオプションが再び表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 がインストールされている場合に使用できます。 パッチ ID は ACP2E-3767 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

バンドル製品の最後のバンドルオプションは削除できません。

<u> 再現手順 </u>:

1. **[!UICONTROL Catalog]**/**[!UICONTROL Products]**/**[!UICONTROL Add Product]** に移動します。
1. ドロップダウンから「**[!UICONTROL Simple Product]**」を選択します。
1. 必要なデータを入力して保存します。
1. **[!UICONTROL Catalog]**/**[!UICONTROL Products]**/**[!UICONTROL Add Product]** に移動します。
1. ドロップダウンから「**[!UICONTROL Bundle Product]**」を選択します。
1. 必要なデータを入力します。
1. 「バンドル項目」で、「**[!UICONTROL Add Option]**」をクリックします。
1. 「新規」オプションにタイトルを追加し、「**[!UICONTROL Add Products to Option]**」をクリックします。
1. 以前に作成したシンプルな製品を選択し、「**[!UICONTROL Add Selected Products]**」を選択します。
1. バンドル製品を保存します。
1. バンドルオプションを削除して保存します。

<u> 期待される結果 </u>:

1. バンドルオプションが正常に削除されました。
1. 削除が許可されていない場合は、メッセージが表示されます。

<u> 実際の結果 </u>:

1. バンドルオプションはアクティブのままです。
1. エラーや通知は表示されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
