---
title: ACSD-52041：ページビルダーのレンダリングでロックが解放されない
description: ACSD-52041 パッチを適用して、ページビルダーがロックを解除せずに 5 秒間レンダリングされるAdobe Commerceの問題を修正してください。
feature: Page Builder
role: Admin, Developer
exl-id: 48a7fc36-e98a-4a4e-bed3-248d7d73f6cb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-52041：ページビルダーのレンダリングでロックが解放されない

ACSD-52041 パッチでは、ページビルダーがロックを解除せずに 5 秒間レンダリングされる問題を修正しています。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.48 がインストールされている場合に使用できます。 パッチ ID は ACSD-52041-v2 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 ～ 2.4.4-p5、2.4.5 ～ 2.4.5-p4、および 2.4.6 ～ 2.4.6-p2。



>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。


## 問題

**[!DNL Page Builder]** は、ロックを解除せずに *5* 秒間レンダリングされます。

<u> 再現手順 </u>:

1. CMSページ、製品ページまたは **[!DNL Page Builder]** を含んだものを編集します。
1. 変更を保存します。
1. ページの保存時間に注意してください。

<u> 期待される結果 </u>

コンテンツが保存されます。 ブラウザーログにエラーは見つかりませんでした。

<u> 実績 </u>

保存が完了するまでに通常より時間がかかります。
コンソールのエラー：``Page Builder was rendering for 5 seconds without releasing locks``

## パッチの適用

バージョン **2.4.4～2.4.4-p5、2.4.5～2.4.5-p4 および 2.4.6～2.4.6-p2** の個別パッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja>)」を参照してください。
