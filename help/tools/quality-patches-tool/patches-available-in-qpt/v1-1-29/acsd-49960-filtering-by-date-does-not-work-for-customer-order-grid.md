---
title: ACSD-49960：日付によるフィルタリングが顧客の注文グリッドで機能しない
description: ACSD-49960 パッチを適用して、日付によるフィルタリングがカスタマー注文グリッドで機能しないAdobe Commerceの問題を修正します。
feature: Admin Workspace, Orders
role: Admin
exl-id: 0ca607b4-5500-4d70-be5e-a3a2b62c6864
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-49960：日付によるフィルタリングが顧客の注文グリッドで機能しない

ACSD-49960 パッチは、日付によるフィルタリングが顧客の注文グリッドで機能しない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.29がインストールされている場合に利用できます。 パッチ IDはACSD-49960です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

日付によるフィルタリングは、顧客注文グリッドでは機能しません。

<u>複製する手順</u>:

1. バックエンドの&#x200B;**[!UICONTROL Edit customer]**&#x200B;に移動します。
1. 「**[!UICONTROL Orders]**」タブを開きます。
1. 列&#x200B;*[!UICONTROL Purchased]*&#x200B;に日付フィルターを適用します。

<u>期待される結果</u>:

フィルターを適用すると、顧客の注文が購入日ごとに並べ替えられます。

<u>実際の結果</u>:

フィルターを適用すると、コンソールにJS エラーがスローされ、ローダーが読み込み続けます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
