---
title: ACSD-64137：郵便番号による受け取り場所の検索が、オランダ語翻訳では正しく機能しません
description: ACSD-64137 パッチを適用して、郵便番号による受け取り場所の検索がオランダ語翻訳では正しく機能しない問題を修正してください。
feature: Shipping/Delivery
role: Admin, Developer
exl-id: 86c28b6d-6584-4caf-bd35-13e0c1bdcf1d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-64137：郵便番号による受け取り場所の検索が、オランダ語翻訳では正しく機能しません

ACSD-64137 パッチは、郵便番号による受け取り場所の検索がオランダ語翻訳では正しく機能しない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60 がインストールされている場合に使用できます。 パッチ ID は ACSD-64137 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

オランダの郵便番号の検索で、フロントエンドチェックアウトページに結果が表示されません。 ただし、市区町村で機能し、検索せずに対応するアドレスを表示します。

<u> 再現手順 </u>:

1. インベントリモジュールを使用してクリーンなインスタンスをインストールします。
1. カスタム在庫を作成します。
1. オランダの住所を含む 2 つのソースを作成し、それらを在庫（郵便番号 7311ER および 7311AE）に割り当てます。
1. シンプルな製品を作成し、在庫を追加します。
1. **[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Sales]**/**[!UICONTROL Delivery Methods]** に移動して、**[!UICONTROL In-Store Delivery]** を有効にします。
1. **[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Catalog]**/**[!UICONTROL Inventory]**/**[!UICONTROL Distance Provider for Distance Based SSA]** に移動します。 **[!UICONTROL Provider]** を *オフライン計算* に設定します。
1. 次のコマンドを実行して、NL 国の地域名を読み込みます。

   ```bash
   bin/magento inventory-geonames:import NL
   ```

1. 商品をカートに追加し、配送手順に進みます。
1. 「**[!UICONTROL Pick In Store]**」を選択します。 次に、「**[!UICONTROL Select Other]**」をクリックして、他のストアを選択します。
1. **[!UICONTROL Select Store]** の検索フォームに *7311* または *7311AE* と入力します。


**期待される結果**:

* 一致したストアは入力する必要があります。

**実際の結果**:

* 結果が見つかりません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
