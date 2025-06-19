---
title: ACSD-55339:Adobe Commerceの交渉可能な引用符で囲まれた SKU トリミングの問題の解決
description: ACSD-55339 パッチを適用すると、先頭に 0 が付いている商品 SKU が切り取られ、ネゴシエーション エラーが発生するAdobe Commerceの問題が修正されます。
feature: B2B, Quotes
role: Admin, Developer
exl-id: 7a9f92df-fb3e-4723-b731-155c6c4fc431
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-55339:Adobe Commerceの交渉可能な引用符で囲まれた SKU トリミングの問題の解決

ACSD-55339 パッチでは、先頭にゼロが付いた製品 SKU がトリムされ、ネゴシエーション プロセス中にエラーが発生する問題が修正されています。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.56 がインストールされている場合に使用できます。 パッチ ID は ACSD-55339 です。 この問題はAdobe Commerce B2B 1.5.0 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

数値の先頭にゼロが付いた製品 SKU は、交渉可能な見積で使用するとトリミングされ、数量の更新や価格の設定を妨げるエラーが発生します。

<u> 再現手順 </u>:

1. 管理パネルの「製品作成」セクションに移動します。
1. 製品の [!UICONTROL SKU] を 01910 のように設定します。
1. ストアフロントにログインし、次の操作を実行します。
   1. 商品を買い物かごに追加します。
   1. 買い物かごを表示して編集します。
   1. 見積もりを依頼します。
1. [!UICONTROL admin]/[!UICONTROL Quote]/[!UICONTROL View] に移動し、[!UICONTROL Add Products by SKU]/01910 を選択します。

**注意：** SKU は、*01910* ではなく *1910* と表示されます。 この不一致により、カタログには SKU 1910 を持つ製品が存在しないので、ユーザーは数量や価格の設定を更新できません。

<u> 期待される結果 </u>:

交渉可能な見積もりは、エラーを発生させずに正常に更新される必要があります。

<u> 実際の結果 </u>:

製品が存在しないことを示す警告メッセージが表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
