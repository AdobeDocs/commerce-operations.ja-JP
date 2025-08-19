---
title: ACSD-66952：ターゲットルールが設定されると、PLP または買い物かごへの訪問ごとにキャッシュがクリアされる
description: ACSD-66952 パッチを適用すると、ターゲットルールが設定されたときに、PLP または買い物かごへの訪問ごとにキャッシュがクリアされ、不要なパフォーマンスのオーバーヘッドが発生するAdobe Commerceの問題を修正できます。
feature: Shopping Cart, Cache, Price Rules
role: Admin, Developer
source-git-commit: 1aec8de86696ffc9ecb13100e6ffa1f912b281fb
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---


# ACSD-66952：ターゲットルールが設定されると、PLP または買い物かごへの訪問ごとにキャッシュがクリアされる

ACSD-66952 パッチでは、PLP や買い物かごへの訪問のたびにキャッシュがクリアされ、ターゲットルールが設定されるとパフォーマンスのオーバーヘッドが発生する問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 がインストールされている場合に使用できます。 パッチ ID は ACSD-66952 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

PLP または買い物かごへの訪問のたびにキャッシュがクリアされ、ターゲットルールが設定されるとパフォーマンスのオーバーヘッドが発生する問題。

<u> 再現手順 </u>:

1. 小さなサンプルデータセットを生成する。
1. ターゲットルールの値を次のように作成します。
   1. **[!UICONTROL Rule information]**
      * **[!UICONTROL Rule Name]** = *関連製品*
      * **[!UICONTROL Status]** = *アクティブ*
      * **[!UICONTROL Apply to]** = *関連製品*
   1. **[!UICONTROL Products to Match]**
      * デフォルト値のままにします。
   1. **[!UICONTROL Products to Display]**
      * これらの条件の **ALL** が *true* の場合、**[!UICONTROL Product Category]** = *定数値 111111* を設定します
1. キャッシュ無効化リクエストのログの監視を開始します。
1. 製品ページにアクセスします。
1. 買い物かごに製品を追加し、買い物かごページに移動します。

<u> 期待される結果 </u>:

アプリケーションは、サイトの閲覧中にキャッシュを無効にしないでください。

<u> 実際の結果 </u>:

キャッシュタグが無効になります。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドの
* クラウドインフラストラクチャー上のAdobe Commerce:[ アップグレードとパッチ適用 ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) クラウドインフラストラクチャー上のCommerce ガイド

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]：品質向上パッチを適用するためのセルフサービス ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) ツール（『ツールガイド』）
