---
title: 'ACSD-48204: *Yes/No*属性に基づいて作成されたカタログ価格ルールで、選択した範囲が考慮されない'
description: ACSD-48204 パッチを適用して、*Yes/No*属性に基づいて作成されたカタログ価格ルールが選択した範囲を考慮しないAdobe Commerceの問題を修正します。
feature: Admin Workspace, Attributes, Catalog Management, Orders, Price Rules
role: Admin
exl-id: 69f2b35c-856e-4f96-ae2f-fb0c64d5eb94
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 2%

---

# ACSD-48204: *Yes/No*&#x200B;属性に基づいて作成されたカタログ価格ルールは、選択した範囲を考慮しません

ACSD-48204 パッチは、*Yes/No*&#x200B;属性に基づいて作成されたカタログ価格ルールが、選択した範囲を考慮しない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.28がインストールされている場合に利用できます。 パッチ IDはACSD-48204です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

*Yes/No*&#x200B;属性に基づいて作成されたカタログ価格ルールは、選択した範囲を考慮しません。

<u>複製する手順</u>:

1. 2つのWeb サイト（デフォルトとW2）を作成します。
1. *Yes/No* タイプの製品属性を作成します。
   * Set [!UICONTROL Default value] = [!UICONTROL No]
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. 2つのバリエーション（V1とV2）を持つ任意の属性に基づいて、設定可能な製品を作成します。
   * 設定可能なバリエーション属性セットに&#x200B;*Yes/No*&#x200B;属性を追加します
   * バリエーション（V1）の1つについては、デフォルト以外のweb サイト（W2）で値を&#x200B;*[!UICONTROL Yes]*&#x200B;に設定します
1. カタログルールの作成：
   * 両方のウェブサイトに適用
   * 条件：*はい/いいえ*&#x200B;属性値は&#x200B;*[!UICONTROL Yes]*&#x200B;です
   * 割引= 50%
1. デフォルト以外のweb サイト（W2）で設定可能な製品を開きます。
1. V1のバリエーションに50%の割引が適用されていることを確認します。
1. Adobe Commerce管理者でV1 バリエーションを開きます。
   * 既定のWeb サイトに切り替える
   * 変更を加えずに製品を保存します
1. 設定可能な製品ストアフロントページを更新します。

<u>期待される結果</u>:

V1のバリエーションは、変更が行われなかったため、50%の割引が引き続き適用されます。

<u>実際の結果</u>:

割引は消えます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
