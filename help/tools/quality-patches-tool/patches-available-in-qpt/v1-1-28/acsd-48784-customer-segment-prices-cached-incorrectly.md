---
title: ACSD-48784：顧客グループ間で顧客セグメントの価格が正しくキャッシュされない
description: ACSD-48784 パッチを適用して、カスタマーセグメントの価格がカスタマーグループ間で誤ってキャッシュされるAdobe Commerceの問題を修正します。
feature: Admin Workspace, Cache, Customer Service, Orders
role: Admin
exl-id: a691c61c-fdba-4d6a-8314-095dfb0ba4a1
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-48784：顧客グループ間で顧客セグメントの価格が正しくキャッシュされない

ACSD-48784 パッチは、顧客グループ間で顧客セグメントの価格が誤ってキャッシュされる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.28がインストールされている場合に利用できます。 パッチ IDはACSD-48784です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

顧客セグメントの価格が顧客グループ間で誤ってキャッシュされる。

<u>前提条件</u>:

[!DNL Varnish]または[!DNL Fastly]を設定します。

<u>複製する手順</u>:

1. ストアでフルページキャッシュを有効にします。
1. 特別な顧客グループの価格を持つユーザーとしてサイトにログインします。
1. 特別な顧客グループの価格を設定している製品については、製品ページをご覧ください。 *特別価格*&#x200B;をご覧ください。
1. 別のブラウザーで、ログインせずにゲストユーザーと同じ製品ページを開きます。 普通の価格を見てください。
1. Adobe Commerce管理インターフェイスにアクセスし、このストアのAdobe Commerceと[!DNL Fastly] キャッシュをクリアします。
1. ログインブラウザーで、`X-Magento-Vary` Cookieを削除します。
1. ログインブラウザーで、キャッシュが完全にフラッシュされるまで、同じ製品ページを数回再読み込みします。
1. ログインしていないブラウザーで製品ページを再読み込みすると、顧客グループの価格が表示されます。

<u>期待される結果</u>:

製品ページには、特定の顧客グループの正しい価格が表示されます。

<u>実際の結果</u>:

* ゲストユーザーには、ログインしたユーザーの特別価格が表示されます。
* ミニカートに商品が追加されると、正しい価格が表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
