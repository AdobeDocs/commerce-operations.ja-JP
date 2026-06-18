---
title: Quality Patches ToolでAdobe Commerceの問題が発生した場合のパッチの確認
description: この記事では、品質パッチツール（QPT）の概要と、その使用方法を説明するリソースへのリンクについて説明します。
feature: Tools and External Services
role: Admin
exl-id: 4d651c3c-95ad-4b53-bf77-92758acb795d
type: Troubleshooting
source-git-commit: 8be75548a939008057fb5fdf37ba5b5a0345f6d4
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# Quality Patches ToolでAdobe Commerceの問題が発生した場合のパッチの確認

この記事では、品質パッチツール（QPT）の概要と、その使用方法を説明するリソースへのリンクについて説明します。

## 影響を受ける製品とバージョン

* Adobe Commerce オンプレミス、すべて[&#x200B; サポートされているバージョン &#x200B;](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* クラウドインフラストラクチャ上のAdobe Commerce、すべての[&#x200B; サポートされているバージョン &#x200B;](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 品質パッチツールとは

[Quality Patches Tool](https://github.com/magento/quality-patches) （QPT）は、AdobeとMagento Open Source コミュニティによって開発された個別のパッチです。

これにより、次のことが可能になります。

* パッケージに含まれる品質パッチを適用する
* 以前に適用したパッチを元に戻す
* インストールされているバージョンのAdobe Commerceで使用できる高品質パッチに関する一般的な情報を表示します。

使用可能なパッチを表示するために取得できるステータステーブルの例を次に示します。

![品質パッチツールのステータス テーブルに、使用可能なパッチとそのインストールステータスが表示されている](/help/assets/tools/status_table.png)

このツールは、Adobe Commerceで発生する可能性のある問題のパッチをセルフサービスで使用したり、Adobe Commerce サポートによって提案されたパッチを簡単に適用したりできるようにすることを目的としています。

>[!NOTE]
>
>QPTは品質パッチ専用です。 セキュリティパッチは、[Magento セキュリティセンター](https://experienceleague.adobe.com/ja/docs/commerce-operations/release/notes/overview)で入手できます。

## 品質パッチツールで使用可能なパッチ

使用可能なパッチのリストについては、開発者ドキュメントの[品質パッチツール &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)を参照してください。

## 品質パッチツールのインストールと使用方法

Adobe Commerce オンプレミスとAdobe Commerce オンクラウドインフラストラクチャでは、QPT パッケージがece-tools パッケージに含まれているため、インストールと使用のコマンドが異なります。

### Adobe Commerce オンプレミス用QPTのインストールおよび使用方法

パッチの適用と取り消しにQPTをインストールして使用する方法の詳細については、開発者ドキュメントの[&#x200B; ソフトウェアアップデートガイド > パッチ適用](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/usage)を参照してください。

### クラウドインフラストラクチャ上のAdobe Commerce用QPTのインストールと使用方法

Adobe Commerce向けCloud > パッチを適用[&#128279;](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)する方法の詳細については、開発者向けドキュメントの「Cloud for Cloud Cloud Cloud Cloudでパッチを適用する」を参照してください。クラウド インフラストラクチャ上のAdobe Commerceにパッチを適用および元に戻すためにQPTをインストールおよび使用する方法について詳しくは、開発者向けドキュメントを参照してください。

## 関連トピックス

* 開発者ドキュメントの[品質パッチツールのリリースノート &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/release-notes)。
* [Adobe](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)が提供するコンポーザーのパッチをサポートナレッジベースで適用する方法。
