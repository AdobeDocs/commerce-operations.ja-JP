---
title: ACSD-48058：バンドルされた製品がweb サイトに割り当てられていない場合、製品価格インデックスが機能しない
description: ACSD-48058 パッチを適用して、バンドルされた商品がどのweb サイトにも割り当てられていない場合に商品の価格インデックスが機能しないAdobe Commerceの問題を修正します。
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: 270e1b5d-75e0-4374-973a-2bb37161ceec
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-48058：バンドルされた製品がweb サイトに割り当てられていない場合、製品価格インデックスが機能しない

ACSD-48058 パッチは、バンドルされた製品がどのweb サイトにも割り当てられていない場合に、製品価格のインデックスが機能しない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25がインストールされている場合に利用できます。 パッチ IDはACSD-48058です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

バンドルされた製品がどのweb サイトにも割り当てられていない場合、製品価格のインデックスは機能しません。

<u>複製する手順</u>:

1. Adobe Commerce Admin > **[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;に移動し、新しいバンドル商品を作成するか、既存のバンドル商品を編集します。
   * 「**[!UICONTROL Product in Websites]**」タブをクリックし、すべてのチェックボックス（web サイト）のチェックを外します
   * 製品を保存
1. 再インデックスを実行します。

<u>期待される結果</u>:

インデックスの再作成が正常に実行されました。

<u>実際の結果</u>:

製品価格インデックスの実行中に次のエラーがスローされます。

```shell
Undefined array key <bundle product id > in vendor/magento/module-bundle/Model/ResourceModel/Indexer/Price/DisabledProductOptionPriceModifier.php on line 117
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
