---
title: MDVA-33606：階層に割り当てられたCMS ページを保存する際にエラーが発生する
description: MDVA-33606 パッチは、階層ツリーに割り当てられたCMS ページを保存する際に、ユーザーが*Unique constraint violation found*エラーを受け取る問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.3がインストールされている場合に利用できます。 パッチ IDはMDVA-33606です。 この問題は、Adobe Commerce 2.4.3で修正されています。
feature: CMS
role: Admin
exl-id: 19aaa13f-7ee6-49bc-b1d9-c288dc93b951
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 0%

---

# MDVA-33606：階層に割り当てられたCMS ページを保存する際にエラーが発生する

MDVA-33606 パッチは、階層ツリーに割り当てられたCMS ページを保存する際に、ユーザーが&#x200B;*一意の制約の違反が見つかりました*&#x200B;というエラーを受ける問題を解決します。 このパッチは、[品質パッチツール （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3がインストールされている場合に使用できます。 パッチ IDはMDVA-33606です。 この問題は、Adobe Commerce 2.4.3で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1-2.4.2-p2

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

階層ツリーに割り当てられたCMS ページを保存しようとすると、次のエラーメッセージが表示されます。*一意の制約の違反が見つかりました*。

<u>複製する手順</u>:

1. 新しいCMS ページを作成します。 範囲をすべてのストアビューに設定します。 これがCMSの1 ページです。
1. 新しいストアビューを作成します。 これがストアビュー2です。
1. **Content** > **Hierarchy** > Add the CMS Page 1 to hierarchy treeに移動します。
1. 範囲をストアビュー2に変更します。
   * 「親ノード階層を使用」のチェックを外します。
   * CMS Page 1をこのスコープに追加して保存します。
1. ここで、範囲をデフォルトのストアビューに変更します。
   * 「親ノード階層を使用」のチェックを外します。
   * CMS Page 1をこのスコープに追加して保存します。
1. **コンテンツ** > **ページ** > **新しいページを追加**&#x200B;に移動します。
   * ページのタイトルは2 ページ目です。
   * 「Web サイトのページ」セクションで、すべてのストアビューと両方のストアビュー（デフォルトのストアビューとストアビュー2）に割り当て、**ページを保存**&#x200B;をクリックします。
1. CMS編集ページで、「階層」タブを開きます。
   * Store View 2 ノード、Default ノード、All Websites ノードにPage 2を割り当てます。

<u>期待される結果</u>:

CMS ページを3つのノードすべてに割り当てることができます。

<u>実際の結果</u>:

次のエラーが発生します：*一意の制約の違反が見つかりました*。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：品質パッチをセルフサービスで提供するための新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを確認します。

QPTで使用可能な他のパッチについて詳しくは、「QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)で使用可能な[ パッチ」セクションを参照してください。
