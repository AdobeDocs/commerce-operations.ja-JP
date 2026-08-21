---
title: ACSD-57570：管理者ユーザーによる共有カタログへのアクセス制限を修正
description: 特定のストアへのアクセス権を持つ制限付き管理者ユーザーが、製品に割り当てられたすべての共有カタログを一貫して表示したり、お客様の情報を保存したりできないAdobe Commerceの問題を修正するには、ACSD-57570 パッチを適用します。これにより、システムの不整合が発生します。
feature: B2B, Companies, Roles/Permissions
role: Admin, Developer
exl-id: 3eeaf1f1-0338-459f-99ec-53764f3f12db
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 0%

---

# ACSD-57570：管理者ユーザーによる共有カタログへのアクセス制限を修正

ACSD-57570 パッチでは、特定のストアへのアクセス権を持つ制限付き管理者ユーザーが、製品に割り当てられたすべての共有カタログを一貫して表示したり、顧客情報を保存したりできず、システムの不整合が生じる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57がインストールされている場合に利用できます。 パッチ IDはACSD-57570です。 この問題は、Adobe Commerce 2.5.0で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.4-p9

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

特定のストアへのアクセスが制限されている管理者ユーザーが、すべての共有カタログを常に表示したり、顧客を保存したりすることはできず、不整合が生じます。 複数のストアがある場合、制限付き管理者は新しい会社やカスタム共有カタログを表示できません。

<u>複製する手順</u>:

1. 次の順序でストアを設定します。
   * W2という名前の新しいweb サイトを作成します。
   * デフォルトのweb サイトの新しいストアビューを作成します。
   * Web サイト W2用にW2S2という名前の新しいストアを作成します。
   * ストア W2S2のW2S2SV1という名前の新しいストアビューを作成します。
   * W2S2S2という名前の別の新しいストアビューをストア W2S2用に作成します。
   * W2の会社を作成します。
1. 製品の割り当て：
   * 一部の製品はW1にのみ割り当てます。
   * 一部の製品をW2にのみ割り当てます。
   * W1とW2の両方に製品を割り当てます。
1. カスタム共有カタログを作成し、それにすべての製品を割り当てます。
1. **W2**&#x200B;ではなく&#x200B;**W2S2**&#x200B;のみにアクセスできるカスタム管理者ロールを作成します。
1. 制限付き管理者ユーザーを新しいカスタム管理者ロールに割り当てます。
1. 制限付き管理者ユーザーとしてログインします。
1. アクセスを確認：
   * どの企業を見ているか調べてみましょう。
   * 表示されている共有カタログを確認します。
   * 製品リストを開き、製品が割り当てられているすべての共有カタログを表示できるかどうかを確認します。

<u>期待される結果</u>:

動作は一貫している必要があります。

<u>実際の結果</u>:

追加のweb サイト、ストア、ストアビューを1つだけ作成した場合、制限付き管理者ユーザーは、製品リストに会社、共有カタログ、および両方の共有カタログを表示できます。 上記の設定では、制限付き管理者は新しい会社またはカスタム共有カタログを表示できず、デフォルトの共有カタログのみが製品リストに表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
