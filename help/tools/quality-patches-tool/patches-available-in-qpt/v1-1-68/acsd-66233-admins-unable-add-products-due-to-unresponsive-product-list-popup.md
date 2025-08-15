---
title: ACSD-66233：製品リストポップアップが応答しないため、管理者が製品を追加できない
description: ACSD-66233 パッチを適用すると、ビジュアルマーチャンダイザーの [!UICONTROL Add Product] ポップアップが無期限に読み込まれるので、管理者が商品をカテゴリに追加できないAdobe Commerceの問題を修正できます。
feature: Inventory, Merchandising
role: Admin, Developer
type: Troubleshooting
exl-id: 2e01e62d-b6f9-4aa5-9040-7908aa83d422
source-git-commit: a1241f709fc1b7128d1d267c54586c60dadab436
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-66233：製品リストポップアップが応答しないため、管理者が製品を追加できない

ACSD-66233 パッチは、ビジュアルマーチャンダイザーの [!UICONTROL Add Product] ポップアップが無期限に読み込まれるので、管理者がカテゴリに製品を追加できない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 がインストールされている場合に使用できます。 パッチ ID は ACSD-66233 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ビジュアルマーチャンダイザーの [!UICONTROL Add Product] ポップアップが無期限に読み込まれ、管理者がカテゴリに製品を追加できない問題。

<u> 再現手順 </u>:

1. インベントリモジュールをインストールして有効にします。
1. 多数の在庫ソース（700 など）を作成する。
1. 複数の在庫在庫（たとえば、12）を作成し、在庫ソースをそれらに割り当てます。
1. 一部の製品を作成して在庫ソースに割り当てます。
1. カテゴリを作成します。
1. 「[!UICONTROL Products in Category]」セクションを展開します。
1. [!UICONTROL Add Product] ボタンをクリックします。
1. 製品のリストがポップアップに表示されます。

<u> 期待される結果 </u>:

適切な時間内にポップアップに製品リストが読み込まれます。

<u> 実際の結果 </u>:

ポップアップが無期限に読み込まれ、製品リストの表示に失敗する。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
