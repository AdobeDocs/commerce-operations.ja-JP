---
title: ACSD-48300：設定可能な製品が削除された場合、返品を作成できない
description: ACSD-48300 パッチを適用して、設定可能な製品が削除された場合に返品を作成できないAdobe Commerceの問題を修正します。
feature: Admin Workspace, Configuration, Orders, Products, Returns
role: Admin
exl-id: 50139364-e2ea-47a8-9bca-09876dd0e70d
type: Troubleshooting
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-48300：設定可能な製品が削除された場合、返品を作成できない

ACSD-48300 パッチは、設定可能な製品が削除された場合にリターンを作成できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25がインストールされている場合に利用できます。 パッチ IDはACSD-48300です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

設定可能な製品を削除すると、返品を作成できません。

<u>複製する手順</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL RMA Settings]**&#x200B;のストアフロントでRMAを有効にします。
1. 設定可能な商品を作成する。
1. ストアフロントでアカウントを作成します（またはログインします）。
1. 最初の商品として、設定可能な商品をカートに追加します。
1. 後で簡単な製品を追加します。
1. 注文する。
1. 配送：注文をキャンセルします。
1. 設定可能な製品のみを削除します（子製品は削除しないでください）。
1. ストアフロントで、**[!UICONTROL My Orders]**&#x200B;に移動して注文を表示します。
1. **[!UICONTROL Return]**&#x200B;をクリックします。

<u>期待される結果</u>:

管理者は、設定可能な製品が削除されても、項目を返すことができます。

<u>実際の結果</u>:

アイテムを返す際にエラーが発生します。

```text
report.CRITICAL: Error: Call to a member function getShipmentType() on null in magento2ee/app/code/Magento/Rma/view/frontend/templates/return/create.phtml:52
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
