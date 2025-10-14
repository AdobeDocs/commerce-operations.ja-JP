---
title: ACSD-56760：管理者ユーザーが特定の web サイトに制限されており、新しい製品を並べ替えたり追加したりすることができません
description: ACSD-56760 パッチを適用すると、特定の web サイトに制限されている管理者ユーザーが、web ストアに独自のルートカテゴリがある場合、カテゴリ内で新しい商品の並べ替えや追加ができないAdobe Commerceの問題を修正できます。
role: Admin
exl-id: 2d75164e-c463-4e1a-aa6f-f420dbe0aaeb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-56760：管理者ユーザーが特定の web サイトに制限されており、新しい製品を並べ替えたり追加したりすることができません

ACSD-56760 パッチは、特定の web サイトに制限されている管理者ユーザーが、web ストアに独自のルートカテゴリがある場合に、カテゴリ内で新しい製品の並べ替えや追加ができない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.47 がインストールされている場合に使用できます。 パッチ ID は ACSD-56760 です。 この問題はAdobe Commerce 2.4.8-beta1 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

管理者ユーザーが特定の web サイトに限定されており、web ストアに独自のルートカテゴリがある場合に、カテゴリ内で新しい製品を並べ替えたり追加したりできない。

<u> 再現手順 </u>:

1. *2* web サイトを作成します。
1. **[!UICONTROL restricted admin user]** 1 *web サイトのみにアクセスできる* を作成します。
1. **[!UICONTROL restricted admin user]** としてログインし、カテゴリ内の製品の位置を変更してみてください。

*ケース 1*:

* *2* ストア。
* *2* ルートカテゴリ。各 web サイトはそれ自身のカテゴリルートに割り当てられます。

*ケース 2*:

* *2* ストア。
* 両方の Web サイトに割り当てられるのは *1* ルートカテゴリのみです。

<u> 期待される結果 </u>:

* *ケース 1*：制限付き管理者は、利用可能なカテゴリ内の製品を並べ替えられるはずです。
* *ケース 2*：制限された管理者は、使用可能なカテゴリ内の製品を並べ替えることができません。これは、制限されたストアにも影響を与えるからです。

<u> 実際の結果 </u>:

* *ケース 1*：制限された管理者が、利用可能なカテゴリ内の製品を並べ替えることができない。
* *ケース 2*：制限付き管理者は、利用可能なカテゴリ内の製品を並べ替えることができ、制限付きストアに影響を与えます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
