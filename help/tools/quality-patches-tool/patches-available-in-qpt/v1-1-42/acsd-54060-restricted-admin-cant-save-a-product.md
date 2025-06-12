---
title: ACSD-54060：制限付き管理者は、別の製品の子である製品を保存できません
description: ACSD-54060 パッチを適用すると、制限付きの管理者が、別のスコープに割り当てられた別の商品の子である場合に、商品を保存できないAdobe Commerceの問題を修正できます。
feature: Admin Workspace, Roles/Permissions, Products
role: Admin, Developer
exl-id: 2af24cbf-65a1-4bd6-aad3-19b613bee7f2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-54060：制限付き管理者は、別の製品の子である製品を保存できません

ACSD-54060 パッチは、制限された管理者が、別の範囲に割り当てられた別の製品の子である場合に、製品を保存できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42 がインストールされている場合に使用できます。 パッチ ID は ACSD-54060 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 ～ 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

制限付きの管理者は、製品が、別の範囲に割り当てられた別の製品の子である場合、製品を保存できません。

<u> 再現手順 </u>:

1. 追加の web サイトを作成します。
1. シンプルな製品を作成して、両方の web サイトに割り当てます。
1. シンプルな製品を唯一のバリエーションとして設定可能な製品を作成し、設定可能な製品をデフォルトの web サイトにのみ割り当てます。
1. 2 つ目の web サイトにのみアクセスできる、制限付きの管理者ユーザーを作成します。
1. 制限付きの管理者ユーザーとしてログインします。
1. 2 つ目の web サイト範囲で、シンプルな製品名を変更してみてください。

<u> 期待される結果 </u>:

制限付きの管理者は、製品名を変更できます。

<u> 実際の結果 </u>:

エラーが発生しました：*このアイテムを表示するには、さらに権限が必要です*。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
