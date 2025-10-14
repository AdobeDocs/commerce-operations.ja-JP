---
title: AC-15223：ストアフロントページで、ストアの切り替え後にキャッシュされたコンテンツが表示される
description: AC-15223 パッチを適用すると、ストアを切り替えた後にページがキャッシュから提供され、ストアが期待どおりに切り替えられないAdobe Commerceの問題が修正されます。
feature: Cache
role: Admin, Developer
type: Troubleshooting
source-git-commit: ea3584e180acad1765f5b8105c45170725c71269
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---


# AC-15223：ストアフロントページで、ストアの切り替え後にキャッシュされたコンテンツが表示される

AC-15223 パッチでは、ストアを切り替えるとストアの切り替えボタンが機能しないので、キャッシュからページが提供される問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 がインストールされている場合に使用できます。 パッチ ID は AC-15223 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ストアを切り替えた後、ページはキャッシュから提供されます（ストアの切り替えボタンが機能していません）。

<u> 再現手順 </u>:

1. **[!UICONTROL Stores]**/**[!UICONTROL Settings]**/**[!UICONTROL All Stores]** に移動します。
2. 新しいストア表示を作成します。
3. ストアフロントに移動して、ストアビューを切り替えてみてください。

<u> 期待される結果 </u>:

ストア表示が正常に切り替わりました。

<u> 実際の結果 </u>:

バックエンドからキャッシュが削除されるまで、ヘッダーのストアビュー名は変更されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
