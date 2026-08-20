---
title: 'ACSD-61553: [!UICONTROL Cart Price Rule]は、優先度が異なる複数の割引が適用されている場合に誤って計算されます'
description: ACSD-61553 パッチを適用して、優先度の異なる複数の割引が適用された場合に[!UICONTROL Cart Price Rule]が誤って計算されるAdobe Commerceの問題を解決します。
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 0fb7a988-d391-49e5-a59d-62315a16132c
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# ACSD-61553: [!UICONTROL Cart Price Rule]は、優先度が異なる複数の割引が適用されている場合に誤って計算されます

ACSD-61553 パッチでは、優先度が異なる複数の割引が適用される場合に[!UICONTROL Cart Price Rule]が誤って計算される問題が修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53がインストールされている場合に利用できます。 パッチ IDはACSD-61553です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p8

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

優先度が異なる複数の割引が適用されている場合、[!UICONTROL Cart Price Rule]が誤って計算されます。

<u>複製する手順</u>:

1. 9,000 ドルの価格でシンプルな商品を制作します。
1. [!UICONTROL Cart Price Rule]を作成します。条件なしで、後続のルールを破棄することなく、700 ドルの固定割引を含むルール A。
1. 別の[!UICONTROL Cart Price Rule]を作成します。条件なしで、後続のルールを破棄することなく、1000 ドルの固定割引を含むルール B。
1. 数量13の商品をカートに追加します。
1. 以下のいずれかのシナリオでルールを更新します。

   シナリオ 01

        ルール A
     優先度：1
     最大Qty割引の適用先：1
     
      ルール B
     優先度：0
     最大Qty割引の適用先：0
   
   シナリオ 02

        ルール A
     優先度：0
     最大Qty割引の適用先：0
     
      ルール B
     優先度：1
     最大Qty割引の適用先：1
   
   シナリオ 03

        ルール A
     優先度：0
     最大Qty割引の適用先：0
     
      ルール B
     優先度：0
     最大Qty割引の適用先：1
   
1. **[!UICONTROL Update Shopping Cart]** ボタンをクリックして、割引を再計算します。

<u>期待される結果</u>:

様々なシナリオに対して、次の合計割引が表示されます。

     シナリオ 01: $13,700
     シナリオ 02: $10,100
     シナリオ 03: $10,100

<u>実際の結果</u>:

3つのシナリオすべてで、合計割引は9,000 ドルです。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!DNL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
