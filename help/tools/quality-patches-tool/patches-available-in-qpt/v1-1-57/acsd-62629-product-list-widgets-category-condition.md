---
title: 'ACSD-62629: ウィジェット内の製品リストに誤ったカテゴリが表示される'
description: ウィジェットで使用される商品リストがカテゴリ条件を尊重しない場合のAdobe Commerceの問題を修正するには、ACSD-62629 パッチを適用します。
feature: Page Content
role: Admin, Developer
exl-id: a7d6bd43-4b8b-48c4-ae9a-4093ac3a4110
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-62629: ウィジェット内の製品リストに誤ったカテゴリが表示される

ACSD-62629 パッチは、ウィジェットで使用される製品リストがカテゴリ条件を尊重しない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57がインストールされている場合に利用できます。 パッチ IDはACSD-62629です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ウィジェットで使用される製品リストは、カテゴリ条件を尊重しません。

<u>複製する手順</u>:

1. TESTという名前の[!UICONTROL simple product]を作成し、それをカテゴリ 1に追加します。
1. テスト製品の終了日を指定せずにステージング更新を作成します。 更新がアクティブになるまで待ちます。
1. 2つの子製品を含むTEST 2という名前の[!UICONTROL configurable product]を作成し、それをカテゴリ 2に追加します。
1. TEST 5という名前の別の[!UICONTROL simple product]を作成し、それをカテゴリ 1に追加します。
1. 完全なインデックス再作成を実行します。
1. **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**&#x200B;に移動し、ホームページを編集します。
1. *[!UICONTROL Appearance]*&#x200B;が&#x200B;*[!UICONTROL Product Carousel]*&#x200B;に、*[!UICONTROL Category]*&#x200B;がカテゴリー2に設定された[!UICONTROL Products] ウィジェットを追加します。 ページを保存します。
1. フロントエンドに移動し、ホームページを開きます。

<u>期待される結果</u>:

テスト 2 （設定可能）製品のみがページに存在する必要があります。

<u>実際の結果</u>:

テスト 5 （シンプル）とテスト 2 （設定可能）の両方の製品がページに表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
