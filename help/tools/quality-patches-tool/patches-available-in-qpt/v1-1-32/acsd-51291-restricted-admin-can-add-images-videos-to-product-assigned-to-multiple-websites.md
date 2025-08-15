---
title: ACSD-51291：制限付き管理者は、複数の web サイトに割り当てられた製品に画像/ビデオを追加できる
description: ACSD-51291 パッチを適用すると、1 つの web サイトへのアクセスを制限された管理者が、複数の web サイトに割り当てられた製品に画像/ビデオを追加できるAdobe Commerceの問題を修正できます。
feature: Admin Workspace, Products, Page Content
role: Admin
exl-id: a4edd034-f718-4559-9993-11609f0d0efa
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-51291：制限付き管理者は、複数の web サイトに割り当てられた製品に画像/ビデオを追加できる

ACSD-51291 パッチは、1 つの web サイトへのアクセスを持つ制限付き管理者が、複数の web サイトに割り当てられた製品に画像/ビデオを追加できる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.32 がインストールされている場合に使用できます。 パッチ ID は ACSD-51291 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 ～ 2.4.4-p3、2.4.5 ～ 2.4.5-p2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

1 つの web サイトへのアクセス権を持つ制限付き管理者は、複数の web サイトに割り当てられた製品に画像/ビデオを追加できます。

<u> 再現手順 </u>

1. 管理者としてログインします。
1. 2 つ目の web サイト、ストア、ストア表示を作成します。
1. 2 つ目の web サイト、ストア、ストアの各表示用のリソースのみを持つ 2 つ目の管理者ロールを作成します。
1. 2 人目の管理者を作成して、新しい制限付き管理者の役割に割り当てます。
1. 新しい製品を作成して、デフォルトの Web サイトと新しい Web サイトの両方に割り当てます。
1. メインの管理プロファイルからログアウトします。
1. 新しい制限付き管理者としてログインします。
1. 両方の web サイトに割り当てられている、作成した製品を編集します。
1. 「**[!UICONTROL Images and Videos]**」タブを開きます。

<u> 期待される結果 </u>:

* 次のメッセージが表示されます。

  *制限付き管理者は、製品が割り当てられているすべての web サイトに対する権限を管理者が持っている場合にのみ、画像やビデオでアクションを実行できます。*

* 「**[!UICONTROL Add Video]**」ボタンはアクティブではありません。

<u> 実際の結果 </u>:

制限付き管理者は、アクセス権のない web サイトに製品が割り当てられている場合でも、画像やビデオを追加できます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja): Search for patches[!DNL Quality Patches Tool]」を参照してください。
