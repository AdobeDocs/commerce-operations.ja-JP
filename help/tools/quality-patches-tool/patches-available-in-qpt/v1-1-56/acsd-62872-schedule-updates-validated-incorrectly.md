---
title: ACSD-62872：更新のスケジュールが正しく検証されていません
description: スケジュールされた更新が正しく検証されない一意の属性検証でAdobe Commerceの問題を修正するには、ACSD-62872 パッチを適用します。
feature: Catalog Management, Admin Workspace
role: Admin, Developer
exl-id: bd0d452b-aae3-4682-8a2c-471a7f8bf132
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-62872：更新のスケジュールが正しく検証されていません

ACSD-62872 パッチは、スケジュールされた更新が正しく検証されない一意の属性検証の問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56がインストールされている場合に利用できます。 パッチ IDはACSD-62872です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、バージョン 2.4.4 ～ 2.4.6-p8の1.1.58 QPT リリースで非推奨（廃止予定）とマークされています。

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

カスタム属性へのスケジュールされた更新が正しく検証されません。

<u>複製する手順</u>:

1. カテゴリのカスタム属性を作成します。
1. **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**&#x200B;に移動します。
1. 新しいカテゴリを作成します。
1. 同じカテゴリで、**[!UICONTROL Scheduled Updates]** セクションに移動します。
1. 今後このカテゴリの新しい更新を設定します。
1. スケジュールされた更新を開始する前に、カテゴリの作成されたスケジュール更新を編集してみてください。

<u>期待される結果</u>:

スケジュールされた更新を更新できるはずです。

<u>実際の結果</u>:

エラーがスローされました：*カスタム属性の値が一意ではありません。 一意の値を設定して、もう一度試してください。*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* Cloud Infrastructure上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > Commerce Cloud Infrastructure ガイドのパッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
