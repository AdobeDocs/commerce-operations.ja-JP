---
title: ACSD-51574：別の画像に置き換えても、フロントエンドで画像が更新されない
description: ACSD-51574 パッチを適用して、別の画像に置き換えた後にフロントエンドで画像が更新されないAdobe Commerceの問題を修正してください。
feature: Configuration
role: Admin
exl-id: 199674fc-c3b3-4fee-9061-f0546833c1cd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-51574：別の画像に置き換えても、フロントエンドで画像が更新されない

ACSD-51574 パッチは、画像を別の画像に置き換えた後、フロントエンドで画像が更新されない問題を修正しました。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.37 がインストールされている場合に使用できます。 パッチ ID は ACSD-51574 です。 この問題はAdobe Commerce 2.4.7 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.7

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

画像を別の画像に置き換えた後、フロントエンドで画像が更新されません。

<u> 再現手順 </u>:

1. いくつかの画像を使用して製品を作成します。
1. 製品を編集し、既知の名前の画像をアップロードします（例：*image.jpg*）。
1. 商品を保存します。
1. 製品を再度編集し、古いバージョンの画像を削除して、同じ名前の新しいバージョンの画像をアップロードします。 **問題を確認するには、新しいバージョンが異なることを確認してください。**
1. 商品を保存します。 管理者とフロントエンドの両方が画像を表示します。
1. 製品を再度編集し、同じ名前を使用して、同じ新しい画像を再度アップロードします。
1. 製品を保存し、フロントエンドの製品ページを確認します。

<u> 期待される結果 </u>:

2 回目にアップロードされる画像は、名前が変更された画像名と共に、新しい画像である必要があります。

<u> 実際の結果 </u>:

2 回目にアップロードされる画像は、同じ新しい画像ではなく、以前に削除された古いバージョンの画像です。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
