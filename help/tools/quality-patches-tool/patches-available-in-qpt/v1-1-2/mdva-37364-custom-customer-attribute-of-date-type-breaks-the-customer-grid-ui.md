---
title: 「MDVA-37364：日付タイプのカスタム顧客属性がグリッド UI を中断」
description: MDVA-37364 パッチにより、日付タイプのカスタム顧客属性がカスタマーグリッド UI に表示されない問題が解決されました。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches） 1.1.2 がインストールされている場合に利用できます。 パッチ ID は MDVA-37364。 この問題はAdobe Commerce バージョン 2.4.4 で修正される予定であることに注意してください。
feature: Attributes, Cache
role: Developer
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-37364：日付タイプのカスタム顧客属性によりグリッド UI が機能しない

MDVA-37364 パッチにより、日付タイプのカスタム顧客属性がカスタマーグリッド UI に表示されない問題が解決されました。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)1.1.2 がインストールされている場合に使用できます。 パッチ ID は MDVA-37364。 この問題はAdobe Commerce バージョン 2.4.4 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0-2.4.2-p2

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

日付タイプのカスタム顧客属性により、顧客グリッド UI が機能しなくなる。

<u> 再現手順 </u>:

1. 日付タイプのカスタム属性を作成します。
   * **ストア**/**属性**/**属性の追加** に移動します。
   * 入力タイプを日付に設定します。
   * 「列に追加」オプションを「はい」に設定します。
   * 属性を保存します。
1. **管理者**/**顧客**/**すべての顧客** に移動します。
   * 「列」オプションからグリッドに、新しく追加されたカスタム属性を追加します。
1. 顧客を作成/編集し、作成したカスタム日付属性フィールドの値を設定します。
1. キャッシュの保存、再インデックス、クリア。
1. **顧客**/**すべての顧客** に移動します。
   * カスタマーグリッドを確認します。

<u> 期待される結果 </u>:

管理者カスタマーグリッドは、カスタマーグリッド UI を中断することなく、新しい日付カスタム属性を含むすべてのデータを表示します。

<u> 実際の結果 </u>:

管理カスタマーグリッド UI が壊れています。

## パッチの適用

個々のパッチを適用するには、デプロイメントタイプに応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質パッチツールがリリースされました：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)。

QPT で使用可能なその他のパッチについては、[QPT で使用可能なパッチ ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) の節を参照してください。
