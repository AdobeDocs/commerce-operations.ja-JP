---
title: OPcache メモリ サイズのベストプラクティス
description: Adobe Commerce プロジェクトでのOPcache メモリ使用量の特定の設定によるパフォーマンスの低下を回避する方法について説明します。
role: Developer
feature: Best Practices
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 1%
---
# Adobe CommerceでのOPcache メモリ サイズのベストプラクティス

Adobe Commerce on cloud infrastructure Pro プランアーキテクチャ 2.3.xの場合、パフォーマンスの低下を避けるために、`opcache.memory_consumption`を2 GB以上に設定することをお勧めします。

## 影響を受ける製品とバージョン

* Adobe Commerce on cloud infrastructure Pro プランアーキテクチャ 2.3.x
* PHP 7.0以降

## メモリの設定

[OPcache PHP モジュール &#x200B;](https://www.php.net/manual/en/book.opcache.php)に少なくとも&#x200B;**2 GB**&#x200B;のメモリを割り当てます。 OPcache モジュールは`php.ini` ファイルで構成されています。 2048 MBのメモリを割り当てるには、`opcache.memory_consumption = 2048`を設定します。

## 追加情報

* [&#x200B; パフォーマンスのベストプラクティス - PHP設定](../../../performance/software.md#php-settings)
* [PHP オプションの設定](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/configure-app-yaml)
* [Adobe Commerce on cloud infrastructureのデータベースのベストプラクティス](database-on-cloud.md)
* [Adobe Commerceのクラウドインフラストラクチャで最も一般的なデータベースの問題](../maintenance/resolve-database-performance-issues.md)
* [インデクサーの「スケジュールに従って更新」により、Adobe Commerceのパフォーマンスが最適化される](../maintenance/indexer-configuration.md)
