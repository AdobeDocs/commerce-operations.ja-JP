---
title: ACSD-66233：製品リストのポップアップが応答しないために管理者が製品を追加できない
description: Visual Merchandiserの[!UICONTROL Add Product] ポップアップが無期限に読み込まれるため、管理者が商品をカテゴリに追加できないAdobe Commerceの問題を修正するには、ACSD-66233 パッチを適用します。
feature: Inventory, Merchandising
role: Admin, Developer
type: Troubleshooting
exl-id: 2e01e62d-b6f9-4aa5-9040-7908aa83d422
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-66233：製品リストのポップアップが応答しないために管理者が製品を追加できない

ACSD-66233 パッチでは、Visual Merchandiserの[!UICONTROL Add Product] ポップアップが無期限に読み込まれるため、管理者がカテゴリに製品を追加できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68がインストールされている場合に利用できます。 パッチ IDはACSD-66233です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

Visual Merchandiserの[!UICONTROL Add Product] ポップアップが無期限に読み込まれ、管理者がカテゴリに製品を追加できない問題です。

<u>複製する手順</u>:

1. インベントリモジュールをインストールして有効にします。
1. 多数の在庫ソース（700など）を作成します。
1. 複数の在庫在庫（例：12）を作成し、それらに在庫ソースを割り当てます。
1. 商品を作成し、在庫ソースに割り当てる。
1. カテゴリを作成します。
1. [!UICONTROL Products in Category] セクションを展開します。
1. 「[!UICONTROL Add Product]」ボタンをクリックします。
1. 商品リストでポップアップを監視します。

<u>期待される結果</u>:

製品リストは、妥当な時間内にポップアップに読み込まれます。

<u>実際の結果</u>:

ポップアップは無期限に読み込まれ、製品リストの表示に失敗します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
