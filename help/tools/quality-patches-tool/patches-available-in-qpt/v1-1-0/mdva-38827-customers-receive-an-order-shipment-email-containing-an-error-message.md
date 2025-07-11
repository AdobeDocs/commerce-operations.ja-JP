---
title: MDVA-38827：顧客がメールで注文出荷エラーを受信する
description: MDVA-38827 パッチは、次のエラーメッセージが記載された注文出荷メールが顧客に届く問題を修正します。*申し訳ありません。このコンテンツの生成中にエラーが発生しました*。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.0 がインストールされている場合に利用できます。 パッチ ID は MDVA-38827。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
exl-id: ab522c9c-2983-4c2f-b341-4487bdbee34d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# MDVA-38827：顧客がメールで注文出荷エラーを受信する

MDVA-38827 パッチは、次のエラーメッセージが記載された注文出荷メールが顧客に届く問題を修正します。*申し訳ありません。このコンテンツの生成中にエラーが発生しました*。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.0 がインストールされている場合に使用できます。 パッチ ID は MDVA-38827。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

クラウドインフラストラクチャー上のAdobe Commerce 2.4.2-p1

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

出荷について「メールで顧客に通知」オプションを選択すると、顧客は次のエラーメッセージを含むメールを受け取ります。*申し訳ありません。このコンテンツの生成中にエラーが発生しました*。

<u> 再現手順 </u>:

1. **マーケティング**/**コミュニケーション**/**メールテンプレート** に移動し、「**新しいテンプレートを追加**」を選択します。
   * **Magentoの売上** / **新しい出荷** を選択します。
   * 「**テンプレートを読み込み**」をクリックします。
   * テンプレート名（コアシッピングテンプレートなど）を追加し、「**保存**」をクリックします。
1. **Store**/設定/**構成**/**Sales**/**Sales Email** に移動します。
   * **出荷注釈** を有効にします。
   * ゲストの出荷コメントメールテンプレートおよび出荷コメントメールテンプレートで、「**コア出荷テンプレート**」（手順 1 の「テンプレート名の追加」の部分を参照）を選択します。
1. 注文します。 管理パネル/**営業**/**注文** に移動し、「**表示**」をクリックして注文を出荷します。
1. 注文の状態が「保留」から「処理中」に変わります。
1. 左側のサイドバーメニューで **出荷** をクリックし、**表示** をクリックして注文を確認します。
1. **出荷履歴** の下の **コメントテキスト** にコメントを追加し、「**メールで顧客に通知**」チェックボックスをオンにします。
1. **コメントを送信** をクリックします。

<u> 期待される結果 </u>:

出荷コメント付きの販売メールが生成されます。

<u> 実際の結果 </u>:

メールに次のエラーメッセージが表示されます：*申し訳ありません。このコンテンツの生成中にエラーが発生しました。*

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
