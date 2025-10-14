---
title: 'ACSD-58141: L2 Redis キャッシュが有効なログイン ユーザーの POST リクエストで PHPSESSID が再生成される'
description: ACSD-58141 パッチを適用すると、L2 Redis キャッシュが有効なログイン済みのお客様のストアフロント領域で、「PHPSESSID」が POST リクエストで再生成され、お客様が管理者から更新されるAdobe Commerceの問題を修正できます。
feature: Customers, Cache
role: Admin, Developer
exl-id: c188c215-204c-489f-8703-4c81ca8703b7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# ACSD-58141: L2 Redis キャッシュが有効な場合、ログインしている顧客の [!DNL POST] リクエストで PHPSESSID が再生成されます

ACSD-58141 パッチは、L2 Redis キャッシュが有効で、管理者から更新され `PHPSESSID` 場合、ログイン中のお客様の [!DNL POST] リクエストに対して ACSD が再生成する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 がインストールされている場合に使用できます。 パッチ ID は ACSD-58141 です。 この問題はAdobe Commerce 2.4.7 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe CommerceおよびMagento Open Source バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

`PHPSESSID` は、L2 Redis キャッシュが有効なログイン済みのお客様の [!DNL POST] リクエストに対して再生成します。

<u> 前提条件 </u>

環境は、少なくとも 3 つのノードを持つ Redis で設定する必要があります。

<u> 再現手順 </u>:

1. シンプルな製品を作成します。
1. 顧客を作成し、ストアフロントにログインします。
1. `PHPSESSID` の値を確認します。
1. [!DNL POST] リクエストをいくつか送信し（例えば、買い物かごに製品を追加するなど）、`PHPSESSID` が同じままであることを確認します。
1. **[!UICONTROL Admin]** パネルにログインし、顧客のミドルネームを変更します。
1. ミドルネームを保存したら、名前を変更して数回保存し直します。
1. ストアフロントで、[!DNL POST] リクエストを送信します。 `PHPSESSID` を更新する必要があります。
1. ストアフロントで別の [!DNL POST] リクエストを送信し、`PHPSESSID` れを確認します。
1. 前の手順を数回繰り返します。

<u> 期待される結果 </u>

`PHPSESSID` は、顧客データを変更した後に 1 回だけ再生成されます。

<u> 実際の結果 </u>:

`PHPSESSID` リクエストが送信されるたびに、[!DNL POST] が再生成されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [&#x200B; を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja): Search for patches[!DNL Quality Patches Tool]」を参照してください。
