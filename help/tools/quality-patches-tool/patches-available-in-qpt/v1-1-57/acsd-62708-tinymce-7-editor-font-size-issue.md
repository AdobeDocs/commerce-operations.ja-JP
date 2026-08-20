---
title: 'ACSD-62708: [!DNL TinyMCE] 7 エディターのフォントサイズが管理パネルに表示されます（PT）'
description: 管理者の [!DNL TinyMCE] 7 エディターのフォントサイズがPXではなくPTであるAdobe Commerceの問題を修正するには、ACSD-62708 パッチを適用します。 次に、PTではなくPXでフォントサイズを設定することもできます。
feature: Admin Workspace
role: Admin, Developer
exl-id: 037a5831-dbc7-4834-ab8e-9b1f765b92b2
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-62708: [!DNL TinyMCE] 7管理者パネルのエディターフォントサイズにPTが表示される

ACSD-62708 パッチは、管理者パネルの[!DNL TinyMCE] 7 エディターのフォントサイズがPXではなくPTで表示される問題を解決します。 このパッチでは、フォントサイズをPXで設定できます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57がインストールされている場合に利用できます。 パッチ IDはACSD-62708です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.4.4-p11、2.4.5-p10、2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

管理パネルの[!DNL TinyMCE] 7 エディターには、PXではなくPTでフォントサイズが表示されます。

<u>複製する手順</u>:

1. 管理パネルで製品編集ページを開きます。
1. [!UICONTROL Content] セクションを展開します。
1. [!DNL TinyMCE] エディターでフォントコントロールを確認します。

<u>期待される結果</u>:

フォントサイズはPXでなければなりません。

<u>実際の結果</u>:

フォントサイズはPTです。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
