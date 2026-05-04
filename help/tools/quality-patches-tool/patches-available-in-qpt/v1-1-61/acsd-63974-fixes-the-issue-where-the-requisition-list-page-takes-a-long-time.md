---
title: 'ACSD-63974: ページネーションで[!UICONTROL Requisition List]の読み込み時間が遅くなる問題を修正'
description: ACSD-63974 パッチを適用して、[!UICONTROL Requisition List] ページの読み込みに時間がかかり、項目が多すぎる場合に読み込みに時間がかかる問題を修正します。
feature: B2B
role: Admin, Developer
exl-id: 1798baa3-da2f-44eb-8312-1f1b3f75b24d
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-63974: ページネーションで[!UICONTROL Requisition List]の読み込み時間が遅くなる問題を修正

ACSD-63974 パッチは、項目が多すぎる場合に&#x200B;**[!UICONTROL Requisition List]** ページの読み込みに時間がかかる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61がインストールされている場合に利用できます。 パッチ IDはACSD-63974です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

項目が多い（2000以上）場合、**[!UICONTROL Requisition List]** ページの読み込みに時間がかかります。 これは、ページネーションが存在しないため、すべての項目が一度に読み込まれることが原因です。

<u>複製する手順</u>:

1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > *[!UICONTROL General]* > **[!UICONTROL B2B features]**&#x200B;に移動します。
1. **[!UICONTROL Enable Requisition List]**&#x200B;を&#x200B;*はい*&#x200B;に設定します。
1. `setup/performance-toolkit/profiles/ce/small.xml`の`simple_products` ノードを編集して、2000以上の製品を生成します。
1. コマンドを実行します。

   ```shell
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. 顧客を作成してログインします。
1. すべての製品を&#x200B;**[!UICONTROL Requisition List]**&#x200B;に追加します。
1. ストアフロントで&#x200B;**[!UICONTROL Requisition List]**&#x200B;を表示します。


<u>期待される結果</u>:

ページは合理的な時間内に読み込まれる必要があります。


<u>実際の結果</u>:

ページの読み込み時間は、ページネーションがないため、すべての項目が一度に読み込まれるため、項目数が増えるほど長くなります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* Adobe Commerce オンクラウドインフラストラクチャ：アップグレードとパッチ/パッチの適用については、Commerce オンクラウドインフラストラクチャガイドを参照してください。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
