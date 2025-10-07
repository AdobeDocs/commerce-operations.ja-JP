---
title: QPT ツールで使用可能なパッチの概要
description: この記事では、 [!DNL Quality Patches Tool]  （QPT）の概要と、その使用方法を説明するリソースへのリンクを示します。
feature: Support, Tools and External Services
role: Admin
exl-id: e67e5823-d878-4efc-90af-c7bb8c59d654
type: Troubleshooting
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# QPT ツールで使用可能なパッチの概要

この記事では、[!DNL Quality Patches Tool] （QPT）の概要と、その使用方法を説明するリソースへのリンクを示します。

## 影響を受ける製品とバージョン

* Adobe Commerce オンプレミス、すべて [&#x200B; サポート対象バージョン &#x200B;](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* クラウドインフラストラクチャー上のAdobe Commerce、すべて [&#x200B; サポート対象バージョン &#x200B;](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 品質向上パッチツールとは

[[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) （QPT）は、AdobeとMagento Open Source コミュニティが開発した個別のクオリティパッチを適用できるツールです。

次の操作が可能です。

* パッケージに含まれる品質向上パッチの適用
* 以前に適用したパッチを元に戻す
* インストール済みバージョンのAdobe Commerceで使用可能なクオリティパッチに関する一般情報を表示します。

使用可能なパッチを表示するために取得できるステータステーブルの例を次に示します。

![&#x200B; 使用可能なパッチとそのインストールステータスを示す「品質向上パッチツールのステータス」テーブル &#x200B;](/help/assets/tools/status_table.png)

このツールの目的は、Adobe Commerceで発生する可能性のある問題のパッチをセルフサービスで提供できるようにしたり、Adobe Commerce サポートから提案されたパッチを簡単に適用できるようにすることです。

>[!NOTE]
>
>QPT は品質向上パッチ専用です。 セキュリティパッチは、[Adobe CommerceおよびMagento Open Sourceのリリースノート &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/overview.html?lang=ja) で入手できます。

## [!DNL Quality Patches Tool] で使用可能なパッチ

Adobe Commerce サポートナレッジベースのこのセクションでは、QPT パッチによって解決された問題の詳細な説明を、QPT リリースバージョン別にグループ化して示します。
また、サポートナレッジベースの [[!DNL Quality Patches Tool]：パッチを検索ページで、動的に生成されたテーブルを使用して、使用可能な QPT パッチのリストを確認し &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) コンポーネントでフィルタリングすることもできます。

## [!DNL Quality Patches Tool] のインストール方法と使用方法

Adobe Commerce オンプレミスの場合と、クラウドインフラストラクチャ上のAdobe Commerceの場合は、インストールコマンドと使用コマンドが異なります。クラウドの場合は、QPT パッケージが ece-tools パッケージに含まれています。

### Adobe Commerce オンプレミスで QPT をインストールして使用する方法

パッチを適用および元に戻す際に QPT をインストールして使用する方法について詳しくは、開発者向けドキュメントの [Commerce/ツール/使用方法 &#x200B;](../usage.md) を参照してください。

### クラウドインフラストラクチャーにAdobe Commerce用 QPT をインストールして使用する方法

クラウドインフラストラクチャ上でCommerceにパッチを適用したり元に戻したりする際に [QPT をインストールして使用する方法について詳しくは、開発者向けドキュメントの &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)Adobe Commerce on Cloud Infrastructure ガイド/パッチの適用を参照してください。

## 関連資料

* 開発者向けドキュメントの [[!DNL Quality Patches Tool]  リリースノート &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html?lang=ja)。
