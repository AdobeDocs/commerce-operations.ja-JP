---
title: ACSD-58442：幅 768 px のデバイスがモバイルとして扱われ、メニューとヘッダーがデスクトップではなくモバイルビューに読み込まれる問題を修正しました
description: ACSD-58442 パッチを適用すると、幅が 768 px のデバイスがモバイルとして扱われ、メニューとヘッダーがデスクトップではなくモバイルビューに読み込まれるAdobe Commerceの問題が修正されます。
feature: Storefront
role: Admin, Developer
exl-id: 86ea64aa-10fc-4fa3-9902-918fb8983ca0
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-58442：幅 768 px のデバイスがモバイルとして扱われ、メニューとヘッダーがデスクトップではなくモバイルビューに読み込まれる問題を修正しました

ACSD-58442 パッチは、幅が 768 px のデバイスがモバイルとして扱われ、メニューとヘッダーがデスクトップではなくモバイルビューに読み込まれるAdobe Commerceの問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 がインストールされている場合に使用できます。 パッチ ID は ACSD-58442 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

システムでは幅 768 px のデバイスをデスクトップとして扱うようになり、メニューとヘッダーが正しく読み込まれるようになります。 以前は、幅が 768 px のデバイスはモバイルとして扱われ、メニューとヘッダーがモバイル表示に読み込まれる原因となりました。

<u> 再現手順 </u>:

1. ホームページをiPad Mini に読み込むか、ブラウザーの検査ツールを使用して、ブラウザーのサイズを *768 px* に変更します。
1. メインメニューを開きます。

<u> 期待される結果 </u>:

メニューとヘッダーがデスクトップビューとして読み込まれます。

<u> 実際の結果 </u>:

メニューとヘッダーがモバイルビューとして読み込まれます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
