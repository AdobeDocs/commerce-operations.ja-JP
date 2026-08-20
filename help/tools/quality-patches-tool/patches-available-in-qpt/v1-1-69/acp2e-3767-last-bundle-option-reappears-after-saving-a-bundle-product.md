---
title: ACP2E-3767：バンドル製品を保存すると、最後のバンドルオプションが再度表示される
description: ACP2E-3767 パッチを適用して、バンドル製品の最後のバンドルオプションを削除できなかったAdobe Commerceの問題を修正します。
feature: Products, Catalog Management
role: Admin, Developer
type: Troubleshooting
exl-id: 8c0645e3-47ab-4604-a9db-b070c3779e78
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACP2E-3767：バンドル製品を保存すると、最後のバンドルオプションが再度表示される

ACP2E-3767 パッチは、バンドル製品を保存した後に最後のバンドルオプションが再度表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69がインストールされている場合に利用できます。 パッチ IDはACP2E-3767です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

バンドル製品の最後のバンドルオプションを削除することはできません。

<u>複製する手順</u>:

1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]**&#x200B;に移動します。
1. ドロップダウンから「**[!UICONTROL Simple Product]**」を選択します。
1. 必要なデータを入力して保存します。
1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]**&#x200B;に移動します。
1. ドロップダウンから「**[!UICONTROL Bundle Product]**」を選択します。
1. 必要なデータを入力してください。
1. バンドルアイテムで、**[!UICONTROL Add Option]**&#x200B;をクリックします。
1. 新しいオプションにタイトルを追加し、**[!UICONTROL Add Products to Option]**&#x200B;をクリックします。
1. 以前に作成したシンプルな製品を選択し、**[!UICONTROL Add Selected Products]**&#x200B;を選択します。
1. バンドル製品を保存します。
1. バンドルオプションを削除して保存します。

<u>期待される結果</u>:

1. バンドルオプションが正常に削除されました。
1. 削除が許可されていない場合は、メッセージが表示されます。

<u>実際の結果</u>:

1. バンドルオプションはアクティブなままです。
1. エラーや通知は表示されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
