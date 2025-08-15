---
title: ACSD-52906：ログインしたカスタマーキャッシングに関する X-Magento-Vary cookie の問題の解決
description: ログイン中のお客様の X-Magento-Vary cookie が正しく設定されていないAdobe Commerceの問題を修正するには、ACSD-52906 パッチを適用してください。
feature: Cache
role: Admin, Developer
exl-id: 487b7588-7131-4502-b714-05f37520991f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-52906：ログイン済みのお客様の X-Magento-Vary cookie の問題の解決

ACSD-52906 パッチは、ログインしているお客様に対して X-Magento-Vary cookie が正しく設定されない問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.36 がインストールされている場合に使用できます。 パッチ ID は ACSD-52906 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 ～ 2.4.6-p2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

X-Magento-Vary cookie が、同じ顧客セグメントに属するログインした顧客に対して正しく設定されておらず、一部のページで不適切なキャッシュが発生する。

<u> 前提条件 </u>:

Adobe Commerce Inventory management（MSI）モジュールがインストールされ、有効になっています。

<u> 再現手順 </u>:

1. [!DNL Varnish] または [!DNL Fastly] キャッシュを設定します。
1. 新しい顧客セグメントを作成して、（登録済み *顧客* に割り当てます。
1. customer1 と customer2 のように、2 つの顧客を作成します。
1. キャッシュをクリアします。
1. customer1 としてログインし、ホームページに移動します。
1. ブラウザーで匿名ページを開きます。
1. ホーム ページ以外の任意のページに移動します。
1. customer2 としてログインします。
1. ホームページに移動します。
1. ページがブラウザー開発コンソールにキャッシュされているかどうかを確認します。

<u> 期待される結果 </u>:

ページがキャッシュから取得されます。

<u> 実際の結果 </u>:

ページはキャッシュされません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja): Search for patches[!DNL Quality Patches Tool]」を参照してください。
