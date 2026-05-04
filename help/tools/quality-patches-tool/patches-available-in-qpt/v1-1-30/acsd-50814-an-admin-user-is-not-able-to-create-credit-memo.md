---
title: ACSD-50814：管理者ユーザーがクレジットメモを作成できない
description: ACSD-50814 パッチを適用して、管理者ユーザーがクレジットメモを作成できないAdobe Commerceの問題を修正します。
feature: Admin Workspace, Orders, Returns
role: Admin
exl-id: 87ee7166-7492-4948-9a85-a183ecf54fa7
type: Troubleshooting
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# ACSD-50814：管理者ユーザーがクレジットメモを作成できない

ACSD-50814 パッチは、管理者ユーザーがクレジットメモを作成できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30がインストールされている場合に利用できます。 パッチ IDはACSD-50814です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

管理者ユーザーはクレジットメモを作成できません。

<u>複製する手順</u>:

1. Adobe Commerce管理者で、**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping methods]** > **[!UICONTROL Free shipping]**&#x200B;に移動し、**[!UICONTROL Enable free shipping]**&#x200B;を&#x200B;*[!UICONTROL Yes]*&#x200B;に設定します
1. もう一度&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]**&#x200B;に移動し、計算設定を展開して設定します。
   * [!UICONTROL Shipping prices] = [!UICONTROL Including tax]
   * [!UICONTROL Enable cross border trade] = [!UICONTROL No]
1. 価格表示設定を展開し、[!UICONTROL Display shipping prices] = [!UICONTROL Including tax]を設定します。
1. [!UICONTROL Orders]、[!UICONTROL Invoices]、[!UICONTROL Credit memo]の表示設定を展開し、[!UICONTROL Display shipping amount] = [!UICONTROL Including tax]を設定します。
1. キャッシュのクリア：
1. ストアフロントで注文。
1. 管理画面で注文の請求書を作成します。
1. クレジットメモの作成。

<u>期待される結果</u>:

クレジットメモが作成されます。

<u>実際の結果</u>:

次のエラーがスローされます。

*エラーのため、ページを表示できません*

```text
report.CRITICAL: DivisionByZeroError: Division by zero in vendor/magento/module-sales/Model/Order/Creditmemo/Total/Tax.php:139*
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
