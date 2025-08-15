---
title: 'ACSD-46938: ''setup:upgrade''中に DB トリガーでパフォーマンスの問題が発生します'
description: ACSD-46938 パッチを適用して、「setup:upgrade」コマンドがインデクサーモードをスケジュールから保存に変更し、パフォーマンスの著しい低下を引き起こすAdobe Commerceの問題を修正してください。
feature: Upgrade
role: Admin, Developer
exl-id: a4e88329-c5bb-4666-8738-b78b86056b71
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-46938:`setup:upgrade` ークフロー中に DB トリガーでパフォーマンスの問題が発生する

ACSD-46938 パッチでは、`setup:upgrade` コマンドがインデクサーモードをスケジュールから保存に変更し、パフォーマンスの大幅な低下を引き起こす問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 がインストールされている場合に使用できます。 パッチ ID は ACSD-46938 です。 この問題はAdobe Commerce 2.4.6 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.5-p9

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

`setup:upgrade` で DB トリガーを再作成する際にパフォーマンスが低下します。

<u> 再現手順 </u>:

1. 多くの製品やカテゴリを含む大規模なカタログを作成します。
1. [!UICONTROL Admin] にログインします。
1. すべてのインデクサーを [!UICONTROL Update By Schedule] モードに設定します。
1. 任意の製品を開きます。
1. 更新します。 例えば、新しいカテゴリを割り当てます。
1. 「[!UICONTROL Save]」をクリックします。
1. `bin/magento setup:upgrade` コマンドと `bin/magento cron:run` コマンドを並行して実行します。

<u> 期待される結果 </u>:

`bin/magento setup:upgrade` のコマンドを同時に実行すると、`bin/magento cron:run` のコマンドの実行時間が大幅に長くなる。

<u> 実際の結果 </u>:

コマンドの実行時間は増えません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja): Search for patches[!DNL Quality Patches Tool]」を参照してください。
