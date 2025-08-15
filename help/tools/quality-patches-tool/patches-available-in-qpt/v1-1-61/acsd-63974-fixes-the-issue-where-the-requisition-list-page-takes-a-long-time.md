---
title: ACSD-63974：ページネーションで読み込み時間 [!UICONTROL Requisition List] 遅くなる問題を修正しました
description: ACSD-63974 パッチを適用して、項目が多すぎると [!UICONTROL Requisition List] ページの読み込みに時間がかかる問題を修正してください。
feature: B2B
role: Admin, Developer
exl-id: 1798baa3-da2f-44eb-8312-1f1b3f75b24d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-63974：ページネーションで読み込み時間 [!UICONTROL Requisition List] 遅くなる問題を修正しました

ACSD-63974 パッチは、項目が多すぎると **[!UICONTROL Requisition List]** ページの読み込みに時間がかかる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 がインストールされている場合に使用できます。 パッチ ID は ACSD-63974 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

項目が多い（2000 以上）場合、**[!UICONTROL Requisition List]** ページの読み込みに時間がかかる。 これは、ページネーションが行われないので、すべての項目が一度に読み込まれるからです。

<u> 再現手順 </u>:

1. **[!UICONTROL Admin]**/**[!UICONTROL Stores]**/*[!UICONTROL Settings]*/**[!UICONTROL Configuration]**/*[!UICONTROL General]*/**[!UICONTROL B2B features]** に移動します。
1. **[!UICONTROL Enable Requisition List]** を *はい* に設定します。
1. `simple_products` のノードを編集して、2000 以上 `setup/performance-toolkit/profiles/ce/small.xml` 製品を生成する。
1. 次のコマンドを実行します。

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. 顧客を作成し、ログインします。
1. すべての製品を **[!UICONTROL Requisition List]** に追加します。
1. ストアフロントの **[!UICONTROL Requisition List]** を表示します。


<u> 期待される結果 </u>:

このページは、適切な時間内に読み込まれる必要があります。


<u> 実際の結果 </u>:

ページネーションがないためすべての項目が一度に読み込まれるので、ページの読み込み時間は項目の数が多いほど長くなります。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* Adobe Commerce on Cloud Infrastructure: アップグレードとパッチ > Commerce on Cloud Infrastructure ガイドのパッチの適用

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
