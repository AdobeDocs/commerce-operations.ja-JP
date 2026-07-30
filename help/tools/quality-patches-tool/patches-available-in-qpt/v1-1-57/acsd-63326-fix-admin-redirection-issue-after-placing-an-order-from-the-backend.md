---
title: ACSD-63326：バックエンドからの注文後に管理者のリダイレクトの問題を修正する
description: バックエンドから注文した後、管理者が壊れたページにリダイレクトされるAdobe Commerceの問題を修正するには、ACSD-63326 パッチを適用します。
feature: Orders, Admin Workspace
role: Admin, Developer
exl-id: 8fffc3ad-11a4-4e62-b747-1c4c7b493ada
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-63326：バックエンドからの注文後に管理者のリダイレクトの問題を修正する

ACSD-63326 パッチは、バックエンドからの注文を行った後、管理者が壊れたページにリダイレクトされる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57がインストールされている場合に利用できます。 パッチ IDはACSD-63326です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

管理者は、バックエンドから顧客の注文に成功した後、レイアウトが破損しているページにリダイレクトされます。

<u>複製する手順</u>:

1. 管理者パネルの&#x200B;**[!UICONTROL Customers]** セクションに移動します。
1. 任意の顧客を選択し、**[!UICONTROL Edit]**&#x200B;をクリックします。
1. お客様の詳細ページで、上部メニューから「**[!UICONTROL Create Order]**」をクリックします。
1. [!UICONTROL FR French] ストアを選択し、利用可能な商品を注文に追加します。
1. チェックアウト時に必要な詳細を入力し、**[!UICONTROL Get shipping methods and rates]**&#x200B;をクリックします。
1. 「**[注文を送信]**」をクリックして注文します。

<u>期待される結果</u>:

管理者は、正しいレイアウトの注文確認ページまたは感謝ページにリダイレクトされます。

<u>実際の結果</u>:

管理者は、壊れたレイアウトのページにリダイレクトされます。 レイアウトは、ページを更新した後にのみ修正されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
