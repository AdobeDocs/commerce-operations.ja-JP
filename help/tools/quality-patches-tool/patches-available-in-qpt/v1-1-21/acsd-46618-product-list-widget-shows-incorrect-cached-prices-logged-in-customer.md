---
title: ACSD-46618：製品リストウィジェットに、ログインした顧客の誤ったキャッシュ価格が表示される
description: ログインしたお客様の商品リストウィジェットに誤ったキャッシュ価格が表示されるAdobe Commerceの問題を修正するパッチを適用します。
feature: Cache, Orders, Products
role: Admin
exl-id: fa350f84-2fe5-474b-b4fd-d6c1e8bb0f95
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-46618：製品リストウィジェットに、ログインした顧客の誤ったキャッシュ価格が表示される

ACSD-46618 パッチは、製品リストウィジェットにログインした顧客に対して誤ったキャッシュ価格が表示される問題を解決します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html) 1.1.21がインストールされている場合に利用できます。 パッチ IDはACSD-46618です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました
* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ACSD-46618 パッチは、製品リストウィジェットにログインした顧客に対して誤ったキャッシュ価格が表示される問題を解決します。

<u>複製する手順</u>:

1. Adobe Commerce Adminで、**[!UICONTROL Stores]**、**[!UICONTROL Configuration]**&#x200B;の順に選択し、**[!UICONTROL Sales]**&#x200B;を展開して、**[!UICONTROL Tax]**&#x200B;を選択します。 税金設定を更新して、税金を含む価格と除外する価格を表示します。
1. **[!UICONTROL Enable Cross Border Trade]** = _はい_&#x200B;に設定します。
1. 米国にのみ適用される税制を構築する。
1. 複数の商品を含むウィジェットをホームページに追加します。
1. 米国の住所と米国以外の住所を持つ2つの顧客を作成します。
1. ストアフロントから米国のお客様を使用してログインします。 ページがキャッシュされていることを確認します。
1. ホームページのウィジェットに表示される価格を確認します。
1. 米国以外のお客様を使用してログアウトしてログインします。

<u>期待される結果</u>:

ホームページウィジェットに表示される価格は、お客様の住所に対応しています。

<u>実際の結果</u>:

ホームページ ウィジェットには、米国以外のお客様の税金を使用した価格が表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
