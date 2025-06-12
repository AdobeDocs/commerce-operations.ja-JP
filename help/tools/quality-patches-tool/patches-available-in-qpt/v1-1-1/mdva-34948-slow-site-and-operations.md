---
title: MDVA-34948:Web サイトの速度が低下
description: MDVA-34948 Adobe Commerce パッチを適用すると、Web サイトの速度が低下する問題が修正されます。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.1 がインストールされている場合に利用できます。 パッチ ID は MDVA-34948。 この問題は、Adobe Commerce バージョン 2.4.1 で修正されました。
feature: Observability, Configuration
role: Admin
exl-id: 3c2a2d44-7d60-42da-a0a3-785fb61d571e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# MDVA-34948:Web サイトの速度が低下


## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* クラウドインフラストラクチャー 2.4.0-p1 上のAdobe Commerce

**Adobe Commerce バージョンとの互換性：**

* アドビのクラウドインフラストラクチャー上のAdobe CommerceオンプレミスおよびAdobe Commerce 2.3.6-2.3.6-p1、2.4.0-2.4.0-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

Web サイトの速度が低下し、操作が妨げられます。

<u> 再現手順 </u>:

1. MySQL で `show processlist` を実行します。
1. 次のような複数のクエリがあるかどうかを確認します。

```sql
   SELECT GET_LOCK(SYSTEM_CONFIG', '10');
```

<u> 期待される結果 </u>:

`GET_LOCK` は直ちに実行する必要があります。

<u> 実際の結果 </u>:

複数の `GET_LOCK` クエリが、それぞれ最大 10 秒間停止します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチについては、[QPT で使用可能なパッチ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) の節を参照してください。
