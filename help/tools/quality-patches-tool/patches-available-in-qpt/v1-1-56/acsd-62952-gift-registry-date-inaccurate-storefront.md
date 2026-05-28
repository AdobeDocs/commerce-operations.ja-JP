---
title: 'ACSD-62952: ストアフロントにギフトレジストリの日付が不正確に表示される'
description: ACSD-62952 パッチを適用して、ギフトレジストリの日付がストアフロントに不正確に表示されるAdobe Commerceの問題を修正します。
feature: Gift, Storefront
role: Admin, Developer
exl-id: c11e95ab-775d-4aa7-828b-29ec52685d47
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-62952: ストアフロントにギフトレジストリの日付が不正確に表示される

ACSD-62952 パッチは、ギフトレジストリの日付がストアフロントに不正確に表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56がインストールされている場合に利用できます。 パッチ IDはACSD-62952です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

共有ギフトレジストリのストアフロントに表示されるイベント日付が、実際の日付よりも1日早く誤って表示される。

<u>複製する手順</u>:

1. フロントエンドに顧客としてログインします。
1. [!UICONTROL My Account] ダッシュボードで、**[!UICONTROL Gift Registry]**&#x200B;をクリックします。
1. 既存のレジストリがない場合は、レジストリを作成し、任意の日付を指定します。
1. 買い物かごに商品を追加します。
1. 買い物かごページで、**[!UICONTROL Add all items to Gift Registry]**&#x200B;をクリックします。
1. ギフトレジストリを共有します。

<u>期待される結果</u>:

ギフトレジストリに正しいイベント日が表示されます。

<u>実際の結果</u>:

招待メールから開いたギフトレジストリには、イベントの日付が1日前に表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* Adobe Commerce オンクラウドインフラストラクチャ：アップグレードとパッチ/パッチの適用については、Commerce オンクラウドインフラストラクチャガイドを参照してください。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
