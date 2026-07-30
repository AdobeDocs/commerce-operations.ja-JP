---
title: 'ACSD-55241: **Used**および**Times Used**属性で、生成されたクーポンに誤った値が表示される'
description: '**Used**および**Times Used**属性で生成されたクーポンに誤った値が表示されるAdobe Commerceの問題を修正するには、ACSD-55241 パッチを適用します'
feature: Price Rules
role: Admin, Developer
exl-id: a156f03c-c939-4ea7-bd34-03c2234edbff
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# ACSD-55241: **使用済み**&#x200B;および&#x200B;**使用済み**&#x200B;回の属性で、生成されたクーポンに誤った値が表示される

ACSD-55241 パッチでは、生成されたクーポンの&#x200B;**Used**&#x200B;属性と&#x200B;**Times Used**&#x200B;属性に誤った値が表示される問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.47がインストールされている場合に利用できます。 パッチ IDはACSD-55241です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

**使用済み**&#x200B;および&#x200B;**使用済み**&#x200B;回の属性に、生成されたクーポンに誤った値が表示されます。

<u>複製する手順</u>:

1. **[!UICONTROL Admin]** > **[!UICONTROL Marketing]** > **[!UICONTROL Promotion]**&#x200B;から&#x200B;**[!UICONTROL Cart Price Rules]**&#x200B;を作成し、注文中に一致する条件を追加します（例：*5$*&#x200B;より大きい小計）

   * 割引を適用する。
   * **[!UICONTROL Auto Coupon]**&#x200B;を選択します。
   * **クーポンコードの管理**&#x200B;から、いくつかのクーポンコードが生成されます。
   * キャッシュのインデックスを再作成してクリーニングします。

1. **[!UICONTROL customer account]**&#x200B;を作成し、フロントエンドにログインします。
1. 買い物かごに&#x200B;*2*&#x200B;個を超える数量を含む商品を1つ追加し、1つのクーポンを適用します。
1. **[!UICONTROL Check Out with Multiple Addresses]**&#x200B;をクリックします。
1. 数量ごとに別の住所を選択して注文し、チェックアウトプロセスを完了します。
1. 管理者からの注文合計を確認し、適用された割引を確認します。
1. 別のクーポンで注文。
1. `php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &` コマンドを実行して、クーポンコードの使用状況を更新します。

<u>期待される結果</u>:

**使用時間**&#x200B;および&#x200B;**使用済み**&#x200B;列に正しいカウントを表示し、管理画面の&#x200B;**[!UICONTROL cart price rule]**&#x200B;で&#x200B;**[!UICONTROL manage coupon]**&#x200B;の&#x200B;**はい**&#x200B;値を表示する必要があります。

<u>実際の結果</u>:

クーポンコードの使用回数は、クーポングリッドの&#x200B;**使用時間**&#x200B;列では更新されません。また、**使用済み**&#x200B;列には、複数の配送先住所で注文した場合の&#x200B;*No*&#x200B;値が表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
