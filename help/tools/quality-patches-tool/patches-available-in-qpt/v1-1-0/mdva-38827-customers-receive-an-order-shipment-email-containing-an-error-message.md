---
title: MDVA-38827：お客様が注文出荷エラーを電子メールで受信する
description: MDVA-38827 パッチは、お客様が次のエラーメッセージを含む注文出荷メールを受信する問題を修正します。*このコンテンツの生成中にエラーが発生しました*。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.0がインストールされている場合に利用できます。 パッチ IDはMDVA-38827です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
exl-id: ab522c9c-2983-4c2f-b341-4487bdbee34d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---

# MDVA-38827：お客様が注文出荷エラーを電子メールで受信する

MDVA-38827 パッチは、顧客が次のエラーメッセージを含む注文出荷メールを受信する問題を修正します。*このコンテンツの生成中にエラーが発生しました*。 このパッチは、[品質パッチツール （QPT） &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0がインストールされている場合に使用できます。 パッチ IDはMDVA-38827です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce on cloud infrastructure 2.4.2-p1

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

「メールで顧客に通知」オプションを選択すると、顧客に次のエラーメッセージがメールで送信されます。*このコンテンツの生成中にエラーが発生しました*。

<u>複製する手順</u>:

1. **マーケティング** > **コミュニケーション** > **電子メールテンプレート**&#x200B;に移動し、**新しいテンプレートを追加**&#x200B;を選択します。
   * **Magento Sales** > **New Shipment**&#x200B;を選択します。
   * 「**テンプレートを読み込む**」をクリックします。
   * テンプレート名（例：コア出荷テンプレート）を追加し、**保存**&#x200B;をクリックします。
1. **Store** / 設定/**Configuration** / **Sales** / **Sales Email**&#x200B;に移動します。
   * **送信コメント**&#x200B;を有効にします。
   * 「出荷コメント電子メールテンプレート」および「ゲスト用の出荷コメント電子メールテンプレート」の下で「**コア出荷テンプレート**」（手順1の「テンプレート名を追加」の部分を参照）を選択します。
1. 注文する。 管理パネル / **Sales** / **Order**&#x200B;に移動し、**View**&#x200B;をクリックして注文を発送します。
1. 注文の状態が「保留中」から「処理中」に変わります。
1. 左側のサイドバーメニューで「**出荷**」をクリックし、**表示**」をクリックして注文を確認します。
1. **出荷履歴**&#x200B;の下の&#x200B;**コメントテキスト**&#x200B;にコメントを追加し、**電子メールでお客様に通知**&#x200B;のチェックボックスをオンにします。
1. 「**コメントを送信**」をクリックします。

<u>期待される結果</u>:

出荷コメント付きの販売メールが生成されます。

<u>実際の結果</u>:

次のエラーメッセージがメールで受信されました：*申し訳ありません。このコンテンツの生成中にエラーが発生しました。*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
