---
title: 「ACSD-61366:「bin/magento setup:static-content:deploy —jobs 4」コマンドで、複数のジョブエラーがエラーで発生する」
description: ACSD-61366 パッチを適用すると、DB 接続用のポートを指定しているにもかかわらず、「bin/magento setup:static-content:deploy —jobs 4」コマンドで*Port must be configured within host parameter* エラーが発生するAdobe Commerceの問題が修正されます。
feature: SCD
role: Admin, Developer
source-git-commit: b671dc30cd511d63dbbbaa6edd47ee36c1351620
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-61366:`bin/magento setup:static-content:deploy --jobs 4` コマンドを実行すると、複数のジョブ エラーが発生してエラーが表示される

ACSD-61366 パッチでは、DB 接続用のポートを指定しているにもかかわらず、`bin/magento setup:static-content:deploy --jobs 4` コマンドで *Port must be configure within the host parameter* エラーが発生する複数のジョブ エラーが検出される問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52 がインストールされている場合に使用できます。 パッチ ID は ACSD-61366 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

DB 接続のポートを指定しているにもかかわらず、`bin/magento setup:static-content:deploy --jobs 4` コマンドで *Port must be configured within the host parameter* エラーが発生する複数のジョブ エラーが発生します。

<u> 再現手順 </u>:

1. `app/etc/env.php` のデータベース接続のポートを指定します。
1. コマンド `bin/magento setup:static-content:deploy --jobs 4` 実行します。

<u> 期待される結果 </u>:

静的コンテンツのデプロイメントが正常に完了しました。

<u> 実際の結果 </u>:

コマンドが失敗し、「*Port must be configured within host parameter*」というエラーが表示される。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。