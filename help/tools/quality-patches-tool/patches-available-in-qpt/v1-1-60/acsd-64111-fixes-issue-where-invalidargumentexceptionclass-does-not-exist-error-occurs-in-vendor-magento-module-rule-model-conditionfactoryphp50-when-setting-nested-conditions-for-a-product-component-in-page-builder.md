---
title: 'ACSD-64111:  [!DNL Page Builder]で製品コンポーネントのネストされた条件を設定する際の*InvalidArgumentException: Class does not exist* エラーを修正しました'
feature: Products, Page Builder
role: Admin, Developer
exl-id: dc39c65b-fb78-4105-b0e8-92a78b49adaf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-64111: [!DNL Page Builder]の製品コンポーネントにネストされた条件を設定する際に、*InvalidArgumentException: Class does not exist* エラーが修正されました

ACSD-64111 パッチは、[!DNL Page Builder]で製品コンポーネントのネストされた条件を設定する際に`vendor/magento/module-rule/Model/ConditionFactory.php:50`で&#x200B;*InvalidArgumentException: Class does not exist* エラーが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60がインストールされている場合に利用できます。 パッチ IDはACSD-64111です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法）  2.4.6-p8

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

エラー&#x200B;*InvalidArgumentException: クラスが/app/&lt;project id\>/vendor/magento/module-rule/Model/ConditionFactory.php*&#x200B;に存在しません。製品ウィジェット条件[!DNL Page Builder]に&#x200B;*[!UICONTROL Conditions Combination]*&#x200B;を追加すると、スローされます。

<u>複製する手順</u>:

1. Adobe Commerce管理者にログインします。
1. **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]**&#x200B;に移動します。
1. 新しいページを追加（または既存のページを編集）。
1. **[!UICONTROL Content]** セクションを展開し、**[!UICONTROL Edit with Page Builder]**&#x200B;をクリックします。
1. 新しい行を追加してから&#x200B;**[!UICONTROL Products]** ウィジェットを追加します。
1. **[!UICONTROL Products]** ウィジェットを設定します。
1. **[!UICONTROL Select Products By]**&#x200B;の下の&#x200B;**[!UICONTROL Condition]**&#x200B;を選択します。
1. 新しい条件を追加し、ドロップダウンから「**[!UICONTROL Conditions Combination]**」を選択します。

<u>期待される結果</u>:

ログにエラーはありません。

<u>実際の結果</u>:

以下の例外はログに記録されます。

*report.CRITICAL: InvalidArgumentException: クラスがvendor/magento/module-rule/Model/ConditionFactory.php:50*&#x200B;に存在しません

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
