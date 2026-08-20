---
title: MDVA-41628：制限付き管理者ユーザーが新しいリソースにアクセスする
description: MDVA-41628 パッチは、新しいモジュールが追加されたときに、制限された管理者ユーザーが新しいリソースにアクセスできる問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.12がインストールされている場合に利用できます。 パッチ IDはMDVA-41628です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Admin Workspace
role: Admin
exl-id: 774a4329-fa1f-4cca-aa97-1b8ef03c11d1
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-41628：制限付き管理者ユーザーが新しいリソースにアクセスする

MDVA-41628 パッチは、新しいモジュールが追加されたときに、制限された管理者ユーザーが新しいリソースにアクセスできる問題を修正します。 このパッチは、[品質パッチツール（QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.12がインストールされている場合に使用できます。 パッチ IDはMDVA-41628です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

制限付き管理者ユーザーは、新しいモジュールが追加されたときに新しいリソースにアクセスできます。

<u>複製する手順</u>:

1. 制限されたリソースを使用して、新しい管理者ユーザーロールを作成します。
1. 手順1で作成した役割の下に新しい管理者ユーザーを作成します。
1. ACL リソースと共に新しいメニューアイテムのセットを作成するカスタムモジュールをインストールして有効にします。
1. 新しく作成した管理者ユーザーを使用してログインします。

<u>期待される結果</u>:

アクセスが制限された管理者ユーザーは、新しく作成されたメニュー項目にアクセスできません。

<u>実際の結果</u>:

制限付き管理者ユーザーは、新しいリソースがユーザーの役割に割り当てられていなくても、新しいメニュー項目にアクセスできます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
