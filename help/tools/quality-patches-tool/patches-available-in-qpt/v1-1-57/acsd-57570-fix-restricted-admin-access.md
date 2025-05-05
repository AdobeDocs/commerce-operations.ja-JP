---
title: ACSD-57570：共有カタログへの管理者ユーザーアクセスが制限される問題を修正
description: ACSD-57570 パッチを適用すると、特定のストアへのアクセス権を持つ制限付き管理者ユーザーが、製品に割り当てられたすべての共有カタログを一貫して表示したり、顧客情報を保存したりできず、システムの不整合が発生するAdobe Commerceの問題を修正できます。
feature: B2B, Companies, Roles/Permissions
role: Admin, Developer
source-git-commit: 6147a028e2ce783809b5c2c32c65784611d03f0e
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---


# ACSD-57570：共有カタログへの管理者ユーザーアクセスが制限される問題を修正

ACSD-57570 パッチは、特定のストアへのアクセスを持つ制限付き管理者ユーザーが、製品に割り当てられたすべての共有カタログを一貫して表示したり、顧客情報を保存したりできず、システムの不整合が発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 がインストールされている場合に使用できます。 パッチ ID は ACSD-57570 です。 この問題はAdobe Commerce 2.5.0 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 ～ 2.4.4-p9

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

特定のストアへのアクセス権を持つ制限付き管理者ユーザーは、すべての共有カタログを表示したり、顧客を保存したりできないので、不整合が発生します。 複数のストアがある場合、制限付き管理者は、新しい会社またはカスタム共有カタログを表示できません。

<u> 再現手順 </u>:

1. 次の順序でストアを設定します。
   * W2 という名前の新しい web サイトを作成します。
   * デフォルトの web サイトの新しいストア表示を作成します。
   * Web サイト W2 に W2S2 という名前の新しいストアを作成します。
   * ストア W2S2 に W2S2SV1 という名前の新しいストアビューを作成します。
   * ストア W2S2 に対して、W2S2SV2 という名前の別の新しいストアビューを作成します。
   * W2 の会社を作成します。
1. 製品の割り当て：
   * 一部の製品を W1 のみに割り当てます。
   * 一部の製品を W2 のみに割り当てます。
   * 一部の製品を W1 と W2 の両方に割り当てます。
1. カスタムの共有カタログを作成し、すべての製品を割り当てます。
1. **W2** ではなく、**W2S2** のみにアクセスできるカスタムの管理者の役割を作成します。
1. 制限付き管理者ユーザーを新しいカスタム管理者の役割に割り当てます。
1. 制限付きの管理者ユーザーとしてログインします。
1. アクセスの確認：
   * 表示できる会社を確認します。
   * 表示できる共有カタログを確認します。
   * 製品リストを開き、製品が割り当てられているすべての共有カタログを表示できるかどうかを確認します。

<u> 期待される結果 </u>:

この動作は一貫している必要があります。

<u> 実際の結果 </u>:

追加の web サイト、ストア、ストア表示を 1 つだけ作成した場合、制限された管理者ユーザーは、会社、共有カタログおよび両方の共有カタログを製品リストに表示できます。 上記の設定では、制限付き管理者は新しい会社やカスタムの共有カタログを表示できず、製品リストにはデフォルトの共有カタログのみが表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
