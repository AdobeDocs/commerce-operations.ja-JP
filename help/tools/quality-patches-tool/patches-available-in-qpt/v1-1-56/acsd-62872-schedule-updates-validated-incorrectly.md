---
title: 'ACSD-62872: スケジュールの更新が正しく検証されませんでした'
description: ACSD-62872 パッチを適用して、スケジュールされた更新が正しく検証されない一意の属性検証のAdobe Commerceの問題を修正してください。
feature: Catalog Management, Admin Workspace
role: Admin, Developer
source-git-commit: f734dab2316237d60164a430eeabed17782b0ae6
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# ACSD-62872: スケジュールの更新が正しく検証されませんでした

ACSD-62872 パッチは、スケジュールされた更新が正しく検証されない一意の属性検証の問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 がインストールされている場合に使用できます。 パッチ ID は ACSD-62872 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

カスタム属性に対してスケジュールされた更新は、正しく検証されません。

<u> 再現手順 </u>:

1. カテゴリのカスタム属性を作成します。
1. **[!UICONTROL Catalog]**/**[!UICONTROL Categories]** に移動します。
1. 新しいカテゴリを作成します。
1. 同じカテゴリで、**[!UICONTROL Scheduled Updates]** のセクションに移動します。
1. 今後の任意の時間でこのカテゴリに対して新しい更新を設定します。
1. スケジュールされた更新を開始する前に、カテゴリに対して作成したスケジュールの更新を編集してみてください。

<u> 期待される結果 </u>:

スケジュールされている更新を更新できるはずです。

<u> 実際の結果 </u>:

次のエラーがスローされました：*「カスタム属性」属性の値が一意ではありません。 一意の値を設定し、もう一度試してください。*

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
