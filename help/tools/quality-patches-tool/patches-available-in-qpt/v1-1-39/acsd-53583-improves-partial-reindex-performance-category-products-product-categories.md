---
title: 'ACSD-53583: [!UICONTROL Category Products]および[!UICONTROL Product Categories]個のインデクサーの部分的なインデックス再作成パフォーマンスを改善します'
description: ACSD-53585 パッチを適用して、カテゴリ製品および製品カテゴリのインデクサーの部分的なインデックス再作成のパフォーマンスを向上させます。
feature: Products, Categories
role: Admin, Developer
exl-id: 11e60cc2-1f7e-4e4a-a5eb-0f1dbe399ef2
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-53583: カテゴリ製品と製品カテゴリのインデックスの部分的なインデックス再作成のパフォーマンスを改善します。

ACSD-53583 パッチは、*カテゴリ製品*&#x200B;および&#x200B;*製品カテゴリ* インデクサーの部分的なインデックス再作成パフォーマンスを改善します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.39がインストールされている場合に利用できます。 パッチ IDはACSD-53583です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p3
* [!DNL Live Search] モジュールと互換性がありません。 このパッチを[!DNL Live Search] インストールに適用するには、追加のACSD-55719 パッチをリクエストしてください。

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

部分再インデックスは、完全な再インデックスよりも時間がかかります。

<u>複製する手順</u>:

1. すべてのインデクサーを&#x200B;*スケジュール別に更新*&#x200B;に切り替えます。
1. [!DNL Performance Toolkit] （中程度のプロファイル）を使用してデータを生成します。
1. すべての製品とカテゴリに変更を加えて、インデックスのバックログに入り、すべてのインデックスがアイドル状態になるようにします。
1. *カテゴリ製品*&#x200B;および&#x200B;*製品カテゴリ*&#x200B;のインデクサーに対して部分的なインデックス再作成を実行します。

<u>期待される結果</u>:

部分再インデックスは製品ごとに1回呼び出され、すべての製品とカテゴリが変更されたため、完全な再インデックスとほぼ同じ時間がかかります。

<u>実際の結果</u>:

部分再インデックスは、製品ごとに何度も呼び出され、完全な再インデックスよりも時間がかかります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
