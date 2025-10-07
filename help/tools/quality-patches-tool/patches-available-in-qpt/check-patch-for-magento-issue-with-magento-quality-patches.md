---
title: Quality Patches Tool を使用して、Adobe Commerceの問題のパッチを確認します。
description: この記事では、品質向上パッチツール（QPT）の概要と、その使用方法を説明するリソースへのリンクを示します。
feature: Tools and External Services
role: Admin
exl-id: 4d651c3c-95ad-4b53-bf77-92758acb795d
type: Troubleshooting
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Quality Patches Tool を使用して、Adobe Commerceの問題のパッチを確認します。

この記事では、品質向上パッチツール（QPT）の概要と、その使用方法を説明するリソースへのリンクを示します。

## 影響を受ける製品とバージョン

* Adobe Commerce オンプレミス、すべて [ サポート対象バージョン ](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* クラウドインフラストラクチャー上のAdobe Commerce、すべて [ サポート対象バージョン ](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 品質向上パッチツールとは

[Quality Patches Tool](https://github.com/magento/quality-patches) （QPT）は、AdobeとMagento Open Source コミュニティが開発した個別のパッチです。

次の操作が可能です。

* パッケージに含まれる品質向上パッチの適用
* 以前に適用したパッチを元に戻す
* インストール済みバージョンのAdobe Commerceで使用可能なクオリティパッチに関する一般情報を表示します。

使用可能なパッチを表示するために取得できるステータステーブルの例を次に示します。

![ 使用可能なパッチとそのインストールステータスを示す「品質向上パッチツールのステータス」テーブル ](/help/assets/tools/status_table.png)

このツールの目的は、Adobe Commerceで発生する可能性のある問題のパッチをセルフサービスで提供できるようにしたり、Adobe Commerce サポートから提案されたパッチを簡単に適用できるようにすることです。

>[!NOTE]
>
>QPT は品質向上パッチ専用です。 セキュリティパッチは、[Magento セキュリティセンター ](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview) で入手できます。

## 品質向上パッチツールで使用可能なパッチ

使用可能なパッチのリストについては、開発者向けドキュメントの [Quality Patches Tool](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) を参照してください。

## 品質向上パッチツールのインストール方法と使用方法

Adobe Commerce オンプレミスの場合と、クラウドインフラストラクチャ上のAdobe Commerceの場合は、インストールコマンドと使用コマンドが異なります。クラウドの場合は、QPT パッケージが ece-tools パッケージに含まれています。

### Adobe Commerce オンプレミスで QPT をインストールして使用する方法

パッチの適用と元に戻すための QPT のインストールおよび使用方法の詳細については、開発者向けドキュメントの [ ソフトウェア更新ガイド/パッチ適用 ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) を参照してください。

### クラウドインフラストラクチャーにAdobe Commerce用 QPT をインストールして使用する方法

クラウドインフラストラクチャで QPT をインストールして使用し、Adobe Commerceにパッチを適用したり元に戻したりする方法について詳しくは、開発者向けドキュメントの [Cloud for Adobe Commerce/パッチを適用 ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) を参照してください。

## 関連資料

* 開発者向けドキュメントの [ 品質向上パッチツールのリリースノート ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/release-notes)
* [Adobeが提供する Composer パッチをサポートナレッジベースに適用する方法 ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)。
