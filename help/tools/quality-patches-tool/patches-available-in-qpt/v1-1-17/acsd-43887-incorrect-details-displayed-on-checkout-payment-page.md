---
title: ACSD-43887：チェックアウトの支払いページに表示される詳細が正しくない
description: ACSD-43887 パッチは、会社の発注書が有効になっている場合に、チェックアウト支払いページに間違った詳細が表示される問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.17がインストールされている場合に利用できます。 パッチ IDはACSD-43887です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。
feature: B2B, Checkout, Orders, Payments, User Account
role: Admin
exl-id: e150f093-9f1a-4ba5-bdcf-90e7f42a29c3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 0%

---

# ACSD-43887：チェックアウトの支払いページに表示される詳細が正しくない

ACSD-43887 パッチは、会社の発注書が有効になっている場合に、チェックアウト支払いページに間違った詳細が表示される問題を修正します。 このパッチは、[品質パッチツール（QPT） &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17がインストールされている場合に使用できます。 パッチ IDはACSD-43887です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.4

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

会社の発注書が有効になっている場合、チェックアウト支払いページに誤った詳細が表示されます。

<u>前提条件</u>:

1. B2B モジュールがインストールされている。
1. 「会社を有効にする」は&#x200B;_はい_&#x200B;に設定されています。 **ストア** > **設定** > **一般** > **B2B機能** > **会社を有効にする** > **はい**&#x200B;に移動します。
1. 「発注を有効化」が&#x200B;_はい_&#x200B;に設定されています。 **注文承認設定** > **購入を有効にする** > **はい**&#x200B;に移動します。
1. PayPal Expressは支払い方法として設定されています。

<u>複製する手順</u>:

1. バーチャルな商品を作成する。
1. フロントエンドから会社アカウントを会社の管理者に登録します。
1. バックエンドから会社アカウントを承認し、会社の承認中に&#x200B;**発注を有効にする**&#x200B;を&#x200B;_はい_&#x200B;に設定します。
1. フロントエンドに移動し、手順2で作成した会社管理者アカウントを使用してログインします。
1. 会社の「デフォルトユーザー」を作成します。 **会社ユーザー** > **新しいユーザーを追加**&#x200B;に移動します。
1. 会社の「承認ルール」を作成します。 **承認ルール** > **新しいルールを追加**&#x200B;に移動します。

   * ルールタイプ：注文合計
   * 注文合計：1 ドル以上
   * 次からの承認が必要：会社管理者

1. ログアウトし、「デフォルトユーザー」アカウントを使用してログインします。
1. 手順1で作成したバーチャル商品をカートに追加し、チェックアウトに進みます。
1. 支払い方法としてPayPal Expressを選択し、**発注書を作成**&#x200B;をクリックします。
1. 会社の管理者アカウントを使用してログアウトしてログインします。
1. **My Purchase Orders**&#x200B;に移動し、**Company Purchase Orders**&#x200B;から、手順9で作成した注文の&#x200B;**表示**&#x200B;をクリックします。
1. 発注を承認します。 発注書のステータスは「承認済み：支払い待ち」である必要があります。
1. 会社の「デフォルトユーザー」アカウントを使用してログアウトしてログインします。
1. **購入注文** > **表示** > **注文を配置**&#x200B;に移動します。
1. **注文概要**&#x200B;を確認してください。

<u>期待される結果</u>:

注文の概要に、正しいゼロ以外の値が表示されます。

<u>実際の結果</u>:

注文の概要の合計値はゼロです。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
