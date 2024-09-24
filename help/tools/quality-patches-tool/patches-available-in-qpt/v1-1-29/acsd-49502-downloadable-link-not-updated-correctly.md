---
title: 「ACSD-49502：ダウンロード可能なリンクが after [!DNL staging] update で正しく更新されない」
description: ACSD-49502 パッチを適用して、ダウンロード可能な製品に a [!DNL staging] update が適用された後、ダウンロード可能なリンクが正しく更新されないAdobe Commerceの問題を修正してください。
feature: Staging
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-49502:[!DNL staging] の更新後、ダウンロード可能なリンクが正しく更新されない

ACSD-49502 パッチは、ダウンロード可能な製品に [!DNL staging] アップデートが適用された後、ダウンロード可能なリンクが正しくアップデートされない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 がインストールされている場合に使用できます。 パッチ ID は ACSD-49502 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 ～ 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ダウンロード可能なリンクは、ダウンロード可能な製品に [!DNL staging] の更新が適用された後、適切に更新されません。

<u> 再現手順 </u>:

1. リンクを含むダウンロード可能な製品を作成します。
1. 顧客アカウントを作成し、ログインします。
1. ダウンロード可能な製品をストアフロントからカートに追加します。
1. **[!UICONTROL Admin]** で、ダウンロード可能な製品の新しいアップデートをスケジュールし、スケジュールされたアップデートを完了させます。
1. ストアフロントで注文を完了します。

<u> 期待される結果 </u>:

ダウンロード可能なリンクは、以前に追加された製品が買い物かごに入っている間、スケジュールされた更新を使用する際に保持されます。

<u> 実際の結果 </u>:

ダウンロード可能なリンクが、お客様の *[!UICONTROL My Account]* （[!UICONTROL My Downloadable Products]）ページと **[!UICONTROL Admin]** の注文ビューページの両方に表示されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
