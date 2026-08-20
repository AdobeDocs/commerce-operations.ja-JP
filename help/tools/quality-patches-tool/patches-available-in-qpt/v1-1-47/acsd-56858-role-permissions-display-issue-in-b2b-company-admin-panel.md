---
title: ACSD-56858:B2B会社管理者の役割の権限の違い
description: ACSD-56858 パッチを適用して、B2B環境の制限付き会社管理者に対してロール権限が誤って表示されるAdobe Commerceの問題を修正します。
feature: Companies, B2B, Roles/Permissions
role: Admin, Developer
exl-id: 28f90c8b-5d8b-4444-99ef-c91cfb5d6081
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-56858:B2B会社管理者の役割の権限の違い

ACSD-56858 パッチは、B2B環境の制限付き会社管理者に対して、役割の権限が誤って表示される問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.47がインストールされている場合に利用できます。 パッチ IDはACSD-56858です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

B2B環境の制限付き会社管理者に対するロール権限が正確に表示されません。

<u>複製する手順</u>:

1. まず、会社を設定し、会社管理者と会社ユーザーを追加します。
1. ストアフロントの会社管理者としてログインし、様々なユーザーに対して様々な役割を作成します。
1. 必要に応じて役割を割り当てます。例えば、一部のタスクにはアクセスを制限し、他のタスクには完全なアクセスを許可します。
1. 会社の管理者以外のユーザーに完全なアクセス権を持つ役割を割り当てます。
1. company_managerなど、会社以外の管理者ユーザーにログインします。
1. **[!UICONTROL Roles and permission]**&#x200B;に移動し、役割を編集します。
1. 表示される権限が、その役割IDに対して会社のデータベースで設定された権限と一致しないことに注意してください。

<u>期待される結果</u>:

会社以外の管理者ユーザーの役割と権限が正しく表示されます。

<u>実際の結果</u>:

権限テーブルのデータベースレコードに従って、会社以外の管理者ユーザーに対して役割が正しく表示されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > Commerce クラウドインフラストラクチャ上のパッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」ガイド

## 関連トピックス

* [[!DNL Quality Patches Tool]  リリース：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを確認します
* [Commerce実装プレイブックのデータベーステーブルを修正するためのベストプラクティス &#x200B;](/help/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables.md#why-adobe-recommends-avoiding-modifications)

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
