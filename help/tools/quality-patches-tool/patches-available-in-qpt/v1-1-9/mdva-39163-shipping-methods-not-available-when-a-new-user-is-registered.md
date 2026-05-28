---
title: MDVA-39163：新しく登録したユーザーがゲストセッションから製品を使用した場合、配送方法が利用できない
description: MDVA-39163 パッチは、新しいユーザーが登録され、カート内の製品がゲストセッションから送信されたときに、配送方法が利用できない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.9がインストールされている場合に利用できます。 パッチ IDはMDVA-39163です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: CMS, Marketing Tools, Orders, Products, Shipping/Delivery
role: Admin
exl-id: 781b466b-7d8f-4ad1-9fb4-5404cd02f7d8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 0%

---

# MDVA-39163：新しく登録したユーザーがゲストセッションから製品を使用した場合、配送方法が利用できない

MDVA-39163 パッチは、新しいユーザーが登録され、カート内の製品がゲストセッションから送信されたときに、配送方法が利用できない問題を解決します。 このパッチは、[品質パッチツール （QPT） ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9がインストールされている場合に使用できます。 パッチ IDはMDVA-39163です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

新しいユーザーが登録されている場合、配送方法は利用できず、カート内の商品はゲストセッションからのものです。

<u>複製する手順</u>:

1. **管理者** > **店舗** > **設定** > **販売** > **配信方法**&#x200B;に移動します。 **定額料金**&#x200B;の配送方法のみを有効にし、他のすべてを無効にします。
1. **定額料金**&#x200B;の配送方法で、**適用国への配送**&#x200B;設定で使用可能な&#x200B;**特定**&#x200B;国オプションを選択し、リストから1国（米国など）を選択します。
1. **Admin** > **Stores** > **Configuration** > **Customer** > **Customer Configuration**&#x200B;に移動し、**メール確認を必要とする**&#x200B;を&#x200B;_Yes_&#x200B;に設定します。
1. **管理者** / **マーケティング** / **電子メールテンプレート**&#x200B;で新しい電子メールテンプレートを作成し、`Footer (magento/luma)` テンプレートを読み込んで、テンプレートコンテンツをCMS ブロックに置き換えます。

   ```CMS
   {{block class="Magento\Cms\Block\Block" block_id="footer_links_block"}}
   ```

1. **管理者** > **コンテンツ** > **デザイン** > **設定**&#x200B;に移動し、フロントエンド web サイトに関連するテーマを選択します。 「フッターテンプレート」を、作成した新しいメールテンプレートに設定します。
1. フロントエンドに移動し、商品をカートに追加します。
1. 顧客を作成すると、メールアドレスを確認するメールが届きます。 確認リンクをクリックします。 Web サイトにログインします。
1. **マイアカウント**&#x200B;に移動し、アドレスを追加します。 アドレス国を、以前に管理者設定で設定した出荷国に設定します。
1. 決済プロセスを見る。

<u>期待される結果</u>:

お客様の住所が配送国と互換性があるため、配送方法を利用できます。

<u>実際の結果</u>:

配送方法は利用できません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
