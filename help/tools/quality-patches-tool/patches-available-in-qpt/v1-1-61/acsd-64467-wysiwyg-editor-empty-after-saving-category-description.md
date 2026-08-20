---
title: ACSD-64467：店舗表示レベルでカテゴリの説明を保存した後、WYSIWYG エディターが空になる
description: ストアビューレベルでカテゴリの説明を保存した後、WYSIWYG エディターが空で表示されるAdobe Commerceの問題を修正するには、ACSD-64467 パッチを適用します。
feature: Page Content
role: Admin, Developer
exl-id: 8bc1794f-ace1-4719-9fff-194dbd701ab6
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-64467：店舗表示レベルでカテゴリの説明を保存した後、WYSIWYG エディターが空になる

ACSD-64467 パッチは、ストアビューレベルでカテゴリの説明を保存した後にWYSIWYG エディターが空で表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61がインストールされている場合に利用できます。 パッチ IDはACSD-64467です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ストアビューレベルでカテゴリの説明を保存すると、WYSIWYG エディターが空になります。

<u>複製する手順</u>:

1. ストアビューレベルのCommerce管理者でカテゴリを編集します。
1. カテゴリの説明の横にある「*[!UICONTROL Use default value]*」チェックボックスの選択を解除します。
1. WYSIWYG エディターに説明を入力します。
1. **[!UICONTROL Save]**&#x200B;をクリックします。

<u>期待される結果</u>:

説明が保存され、適切に表示されます。

<u>実際の結果</u>:

ページを再読み込みすると、説明は空になります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
