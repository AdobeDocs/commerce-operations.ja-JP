---
title: ACSD-62629：ウィジェットの製品リストに間違ったカテゴリが表示される
description: ACSD-62629 パッチを適用すると、ウィジェットで使用される商品リストがカテゴリ条件を尊重しないAdobe Commerceの問題を修正できます。
feature: Page Content
role: Admin, Developer
exl-id: a7d6bd43-4b8b-48c4-ae9a-4093ac3a4110
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-62629：ウィジェットの製品リストに間違ったカテゴリが表示される

ACSD-62629 パッチは、ウィジェットで使用される製品リストがカテゴリ条件を尊重しない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 がインストールされている場合に使用できます。 パッチ ID は ACSD-62629 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ウィジェットで使用される製品リストがカテゴリ条件に違反する。

<u> 再現手順 </u>:

1. TEST という名前の [!UICONTROL simple product] を作成して、カテゴリ 1 に追加します。
1. テスト製品の終了日を指定せずにステージング更新を作成します。 更新がアクティブになるまで待ちます。
1. 2 つの子製品を持つ TEST 2 という名前の [!UICONTROL configurable product] を作成して、カテゴリ 2 に追加します。
1. TEST 5 という名前の別の [!UICONTROL simple product] を作成して、カテゴリ 1 に追加します。
1. 完全な再インデックスを実行します。
1. **[!UICONTROL Content]**/**[!UICONTROL Elements]**/**[!UICONTROL Pages]** に移動し、ホームページを編集します。
1. *[!UICONTROL Appearance]* を *[!UICONTROL Product Carousel]* に設定し、*[!UICONTROL Category]* をカテゴリ 2 に設定した [!UICONTROL Products] ウィジェットを追加します。 ページを保存します
1. フロントエンドに移動し、ホームページを開きます。

<u> 期待される結果 </u>:

ページには、TEST 2 （設定可能）製品のみが表示されます。

<u> 実際の結果 </u>:

TEST 5 （シンプル）製品と TEST 2 （設定可能）製品の両方がページに存在します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
