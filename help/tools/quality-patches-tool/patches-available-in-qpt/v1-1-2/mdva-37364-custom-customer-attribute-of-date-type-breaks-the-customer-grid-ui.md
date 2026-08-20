---
title: MDVA-37364：日付タイプのカスタム顧客属性がグリッド UIを壊す
description: MDVA-37364 パッチは、日付タイプのカスタム顧客属性が顧客グリッド UIを壊す問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.2がインストールされている場合に利用できます。 パッチ IDはMDVA-37364です。 この問題は、Adobe Commerce バージョン 2.4.4で修正される予定です。
feature: Attributes, Cache
role: Developer
exl-id: 5bd64004-06c4-49fd-8e56-e2c44008ca82
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-37364：日付タイプのカスタム顧客属性がグリッド UIを壊す

MDVA-37364 パッチは、日付タイプのカスタム顧客属性が顧客グリッド UIを壊す問題を解決します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2がインストールされている場合に使用できます。 パッチ IDはMDVA-37364です。 この問題は、Adobe Commerce バージョン 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0-2.4.2-p2

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

日付タイプのカスタム顧客属性は、顧客グリッド UIを壊します。

<u>複製する手順</u>:

1. 日付タイプでカスタム属性を作成します。
   * **ストア** > **属性** > **属性を追加**&#x200B;に移動します。
   * 入力タイプを「日付」に設定します。
   * 「列に追加」オプションを「はい」に設定します。
   * 属性を保存します。
1. **管理者** > **顧客** > **すべての顧客**&#x200B;に移動します。
   * 新しく追加したカスタム属性を「列」オプションからグリッドに追加します。
1. 顧客を作成/編集し、作成されたカスタム日付属性フィールドの値を設定します。
1. キャッシュを保存、再インデックス、クリアします。
1. **お客様** > **すべてのお客様**&#x200B;に移動します。
   * 顧客グリッドの確認：

<u>期待される結果</u>:

Admin Customer Gridには、Customer Grid UIを壊すことなく、新しい日付カスタム属性を含むすべてのデータが表示されます。

<u>実際の結果</u>:

Admin Customer Grid UIが壊れています。

## パッチを適用する

個別のパッチを適用するには、デプロイメントタイプに応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：品質パッチをセルフサービスで提供するための新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを確認します。

QPTで使用可能な他のパッチについて詳しくは、「QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)で使用可能な パッチ」セクションを参照してください。
