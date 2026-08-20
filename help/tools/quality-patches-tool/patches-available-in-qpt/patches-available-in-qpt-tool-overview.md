---
title: QPT ツールの概要で使用可能なパッチ
description: この記事では、 [!DNL Quality Patches Tool]  （QPT）の概要と、その使用方法を説明するリソースへのリンクについて説明します。
feature: Support, Tools and External Services
role: Admin
exl-id: e67e5823-d878-4efc-90af-c7bb8c59d654
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# QPT ツールの概要で使用可能なパッチ

この記事では、[!DNL Quality Patches Tool] （QPT）の概要と、その使用方法を説明するリソースへのリンクについて説明します。

## 影響を受ける製品とバージョン

* Adobe Commerce オンプレミス、すべて[&#x200B; サポートされているバージョン &#x200B;](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* クラウドインフラストラクチャ上のAdobe Commerce、すべての[&#x200B; サポートされているバージョン &#x200B;](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 品質パッチツールとは？

[[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) （QPT）は、AdobeおよびMagento Open Source コミュニティによって開発された個別の品質向上パッチを適用できるツールです。

これにより、次のことが可能になります。

* パッケージに含まれる品質パッチを適用する
* 以前に適用したパッチを元に戻す
* インストールされているバージョンのAdobe Commerceで使用できる高品質パッチに関する一般的な情報を表示します。

使用可能なパッチを表示するために取得できるステータステーブルの例を次に示します。

![品質パッチツールのステータス テーブルに、使用可能なパッチとそのインストールステータスが表示されている](/help/assets/tools/status_table.png)

このツールは、Adobe Commerceで発生する可能性のある問題のパッチをセルフサービスで使用したり、Adobe Commerce サポートによって提案されたパッチを簡単に適用したりできるようにすることを目的としています。

>[!NOTE]
>
>QPTは品質パッチ専用です。 セキュリティパッチは、[Adobe CommerceおよびMagento Open Sourceのリリースノート &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/overview.html)で入手できます。

## [!DNL Quality Patches Tool]で使用可能なパッチ

Adobe Commerce サポート ナレッジベースのこのセクションでは、QPT パッチによって解決された問題の詳細な説明を、QPT リリースバージョン別にグループ化して示します。
また、使用可能なQPT パッチのリストを表示し、[[!DNL Quality Patches Tool]: パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で動的に生成されたテーブルを使用して、コンポーネントごとにフィルターを適用することもできます。

## [!DNL Quality Patches Tool]のインストールと使用方法

Adobe Commerce オンプレミスとAdobe Commerce オンクラウドインフラストラクチャでは、QPT パッケージがece-tools パッケージに含まれているため、インストールと使用のコマンドが異なります。

### Adobe Commerce オンプレミス用QPTのインストールおよび使用方法

パッチの適用と取り消しにQPTをインストールして使用する方法について詳しくは、開発者ドキュメントの[Commerce/ツール/使用状況](../usage.md)を参照してください。

### クラウドインフラストラクチャ上のAdobe Commerce用QPTのインストールと使用方法

Cloud Infrastructure上のAdobe Commerceにパッチを適用および元に戻すためにQPTをインストールして使用する方法について詳しくは、開発者向けドキュメントの[Commerce Cloud Infrastructure ガイド/パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)を参照してください。

## 関連トピックス

* 開発者ドキュメントの[[!DNL Quality Patches Tool]  リリースノート &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html)。
