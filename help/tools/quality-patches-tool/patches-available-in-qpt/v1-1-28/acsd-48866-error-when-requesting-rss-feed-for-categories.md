---
title: ACSD-48866：カテゴリの RSS フィードをリクエスト中にエラーが発生する
description: ACSD-48866 パッチを適用すると、カテゴリの RSS フィードを要求したときにエラーが発生するAdobe Commerceの問題を修正できます。
feature: Admin Workspace, Categories
role: Admin
exl-id: f278a90f-f30c-401f-a544-713c89eb208a
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# ACSD-48866：カテゴリの RSS フィードをリクエスト中にエラーが発生する

ACSD-48866 パッチでは、カテゴリの RSS フィードを要求したときにエラーが発生する問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 がインストールされている場合に使用できます。 パッチ ID は ACSD-48866 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 ～ 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

カテゴリの RSS フィードを要求すると、エラーが発生します。

<u> 再現手順 </u>:

1. **[!UICONTROL Stores]**/**[!UICONTROL Configurations]**/**[!UICONTROL Catalog]**/**[!UICONTROL RSS Feeds]**/**[!UICONTROL RSS Config]**/**[!UICONTROL Enable RSS]** で RSS フィードを有効にします。
1. **[!UICONTROL Stores]**/**[!UICONTROL Configurations]**/**[!UICONTROL Catalog]**/**[!UICONTROL RSS Feeds]**/**[!UICONTROL Catalog]**/**[!UICONTROL Top Level Category]** で [!UICONTROL Top Level Category] を有効にします。
1. ストアフロントの RSS フィード カテゴリ ページを参照します。
1. `var/log` のログファイルを確認します。

<u> 期待される結果 </u>:

ログファイルにエラーはありません。

<u> 実際の結果 </u>:

次のエラーがログファイルに表示されます。

```
Text fields are not optimised for operations that require per-document field data like aggregations and sorting, so these operations are disabled by default. Please use a keyword field instead. Alternatively, set fielddata=true on [updated_at] in order to load field data by uninverting the inverted index.
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
