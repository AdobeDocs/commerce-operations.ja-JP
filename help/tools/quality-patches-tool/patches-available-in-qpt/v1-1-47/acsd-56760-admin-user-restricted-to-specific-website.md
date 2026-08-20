---
title: ACSD-56760：管理者ユーザーが特定のweb サイトに制限されており、新製品を並べ替えたり追加したりできない
description: ACSD-56760 パッチを適用して、Adobe Commerceの問題を修正します。この問題は、特定のweb サイトに制限されている管理者ユーザーが、web ストアに独自のルートカテゴリがある場合に、カテゴリ内で新製品を並べ替えたり追加したりできない場合に発生します。
role: Admin
exl-id: 2d75164e-c463-4e1a-aa6f-f420dbe0aaeb
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# ACSD-56760：管理者ユーザーが特定のweb サイトに制限されており、新製品を並べ替えたり追加したりできない

ACSD-56760 パッチでは、特定のweb サイトに制限されている管理者ユーザーが、web ストアに独自のルートカテゴリがある場合に、カテゴリ内で新製品を並べ替えたり追加したりできない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.47がインストールされている場合に利用できます。 パッチ IDはACSD-56760です。 この問題は、Adobe Commerce 2.4.8-beta1で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

特定のweb サイトに制限され、web ストアに独自のルートカテゴリがある場合に備えて、カテゴリ内で新製品を並べ替えたり追加したりできない管理者ユーザー。

<u>複製する手順</u>:

1. *2*&#x200B;個のWeb サイトを作成します。
1. *1* web サイトのみにアクセスできる&#x200B;**[!UICONTROL restricted admin user]**&#x200B;を作成します。
1. **[!UICONTROL restricted admin user]**&#x200B;としてログインし、カテゴリ内の製品の位置を変更してみてください。

*ケース 1*:

* *2*&#x200B;店舗。
* *2*&#x200B;個のルートカテゴリ。各web サイトは独自のカテゴリルートに割り当てられています。

*ケース 2*:

* *2*&#x200B;店舗。
* 両方のweb サイトに割り当てられているのは&#x200B;*1* ルートカテゴリのみです。

<u>期待される結果</u>:

* *ケース 1*：制限付き管理者は、使用可能なカテゴリ内の製品を並べ替えることができるようにする必要があります。
* *ケース 2*：制限付き管理者は、使用可能なカテゴリ内の製品を並べ替えることができません。これは、制限付きストアにも影響を与えるためです。

<u>実際の結果</u>:

* *ケース 1*：制限付き管理者は、使用可能なカテゴリ内の製品を並べ替えることができません。
* *ケース 2*：制限付き管理者は、使用可能なカテゴリ内の製品を並べ替えることができ、制限されたストアに影響を与えます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
