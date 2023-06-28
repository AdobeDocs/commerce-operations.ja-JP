---
title: OPcache メモリサイズのベストプラクティス
description: Adobe Commerceプロジェクトでの OPcache メモリ消費の特定の設定によるパフォーマンスの低下を回避する方法について説明します。
role: Developer
feature: Best Practices
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---

# Adobe Commerceの OPcache メモリサイズのベストプラクティス

クラウドインフラストラクチャのAdobe Commerce Pro プランアーキテクチャ 2.3.x の場合、 `opcache.memory_consumption` を 2 GB 以上に変更して、パフォーマンスの低下を防ぎます。

## 影響を受ける製品およびバージョン

* Adobe Commerce on cloud infrastructure Pro プランアーキテクチャ 2.3.x
* PHP 7.0 以降

## メモリの設定

少なくとも **2 GB** 記憶の [OPcache PHP モジュール](https://www.php.net/manual/en/book.opcache.php). OPcache モジュールは、 `php.ini` ファイル。 2048 MB のメモリを割り当てるには、 `opcache.memory_consumption = 2048`.

## 追加情報

* [パフォーマンスのベストプラクティス — PHP 設定](../../../performance/software.md#php-settings)
* [PHP オプションの設定](https://devdocs.magento.com/cloud/project/project-conf-files_magento-app.html#customize-phpini-settings)
* [クラウドインフラストラクチャ上のAdobe Commerceのデータベースのベストプラクティス](database-on-cloud.md)
* [クラウドインフラストラクチャ上のAdobe Commerceで最も一般的なデータベースの問題](../maintenance/resolve-database-performance-issues.md)
* [インデクサー「スケジュールに従って更新」を使用すると、Adobe Commerceのパフォーマンスが最適化されます](../maintenance/indexer-configuration.md)
