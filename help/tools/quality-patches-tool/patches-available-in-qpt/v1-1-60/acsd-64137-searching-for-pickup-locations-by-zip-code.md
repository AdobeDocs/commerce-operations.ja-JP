---
title: ACSD-64137：郵便番号による受け取り場所の検索が、オランダ語のローカライゼーションで正しく機能しない
description: ACSD-64137 パッチを適用して、郵便番号による受け取り場所の検索がオランダ語ローカライゼーションで正しく機能しない問題を修正します。
feature: Shipping/Delivery
role: Admin, Developer
exl-id: 86c28b6d-6584-4caf-bd35-13e0c1bdcf1d
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-64137：郵便番号で受け取り場所を検索すると、オランダ語のローカライゼーションが正しく機能しない

ACSD-64137 パッチでは、郵便番号による受け取り場所の検索がオランダ語ローカライゼーションで正しく機能しない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60がインストールされている場合に利用できます。 パッチ IDはACSD-64137です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

オランダの郵便番号の検索では、フロントエンドのチェックアウトページに結果が表示されません。 ただし、都市別に動作し、検索なしで対応するアドレスを表示します。

<u>複製する手順</u>:

1. 在庫モジュールを使用してクリーンインスタンスをインストールします。
1. カスタム在庫の作成。
1. オランダのアドレスを持つ2つのソースを作成し、それらを在庫に割り当てます（郵便番号7311ERと7311AE）。
1. シンプルな商品を制作し、在庫を追加する。
1. **[!UICONTROL In-Store Delivery]**&#x200B;を有効にするには、**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]**&#x200B;に移動します。
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Distance Provider for Distance Based SSA]**&#x200B;に移動します。 **[!UICONTROL Provider]**&#x200B;を&#x200B;*オフライン計算*&#x200B;に設定します。
1. 次のコマンドを実行して、NL countryの地理名を読み込みます。

   ```shell
   bin/magento inventory-geonames:import NL
   ```

1. 商品をカートに追加し、配送ステップに移動します。
1. **[!UICONTROL Pick In Store]**&#x200B;を選択します。 次に、**[!UICONTROL Select Other]**&#x200B;をクリックして、他のストアを選択します。
1. **[!UICONTROL Select Store]**&#x200B;検索フォームに「*7311*」または「*7311AE*」と入力します。


**期待される結果**:

* 一致するストアを入力する必要があります。

**実際の結果**:

* 結果が見つかりませんでした。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
