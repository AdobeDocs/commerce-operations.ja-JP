---
title: ACSD-48058：バンドルされた製品が web サイトに割り当てられていない場合、製品価格のインデックス再作成が機能しない
description: バンドルされた製品がいずれの Web サイトにも割り当てられていない場合に製品の価格の再インデックスが機能しないAdobe Commerceの問題を修正するには、ACSD-48058 パッチを適用してください。
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: 270e1b5d-75e0-4374-973a-2bb37161ceec
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-48058：バンドルされた製品が web サイトに割り当てられていない場合、製品価格のインデックス再作成が機能しない

ACSD-48058 パッチは、バンドルされた製品が Web サイトに割り当てられていない場合、製品の価格インデックス再作成が機能しない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25 がインストールされている場合に使用できます。 パッチ ID は ACSD-48058 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

バンドルされた製品が Web サイトに割り当てられていない場合、製品価格の再インデックスが機能しません。

<u> 再現手順 </u>:

1. Adobe Commerce管理者/ **[!UICONTROL Catalog]** / **[!UICONTROL Products]** に移動して、新しいバンドル商品を作成するか、既存のバンドル商品を編集します。
   * 「**[!UICONTROL Product in Websites]**」タブをクリックし、すべてのチェックボックス（web サイト）のチェックを解除します。
   * 商品の保存
1. 再インデックスを実行します。

<u> 期待される結果 </u>:

再インデックスが正常に実行されました。

<u> 実際の結果 </u>:

製品価格インデックスの実行中に次のエラーがスローされます。

```bash
Undefined array key <bundel product id > in vendor/magento/module-bundle/Model/ResourceModel/Indexer/Price/DisabledProductOptionPriceModifier.php on line 117
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
