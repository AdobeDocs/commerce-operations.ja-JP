---
title: AC-15223：ストアを切り替えた後、ストアフロントページにキャッシュされたコンテンツが表示される
description: ストアを切り替えた後にページがキャッシュから提供され、ストアが期待どおりに切り替わらないAdobe Commerceの問題を修正するには、AC-15223 パッチを適用します。
feature: Cache
role: Admin, Developer
type: Troubleshooting
exl-id: 22257e94-8d59-4221-bf79-1d63b5600498
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# AC-15223：ストアを切り替えた後、ストアフロントページにキャッシュされたコンテンツが表示される

AC-15223 パッチでは、ストアを切り替えた後、ストアスイッチャーが機能しないので、ページがキャッシュから提供される問題が修正されます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69がインストールされている場合に利用できます。 パッチ IDはAC-15223です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ストアを切り替えた後、ページはキャッシュから提供されます（ストアスイッチャーは機能しません）。

<u>複製する手順</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]**&#x200B;に移動します。
2. 新しいストアビューを作成します。
3. ストアフロントに移動し、ストアビューを切り替えてみてください。

<u>期待される結果</u>:

ストアビューが正常に切り替えられました。

<u>実際の結果</u>:

キャッシュがバックエンドからクリーニングされるまで、ストアビュー名はヘッダーで変更されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
