---
title: OPcache のメモリー・サイズのベスト・プラクティス
description: Adobe Commerce プロジェクトでの OPcache メモリ使用について、具体的な設定を行ってパフォーマンスの低下を回避する方法について説明します。
role: Developer
feature: Best Practices
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---

# Adobe Commerceの OPcache メモリサイズのベストプラクティス

クラウドインフラストラクチャー上のAdobe Commerce Pro プランアーキテクチャ 2.3.x の場合は、次を設定することをお勧めします `opcache.memory_consumption` から 2 GB 以上に縮小して、パフォーマンスの低下を回避します。

## 影響を受ける製品とバージョン

* Adobe Commerce on cloud infrastructure Pro プランアーキテクチャ 2.3.x
* PHP 7.0 以降

## メモリの設定

少なくとも割り当てる **2 GB** のメモリ容量 [OPcache PHP モジュール](https://www.php.net/manual/en/book.opcache.php). OPcache モジュールは、 `php.ini` ファイル。 2048 MB のメモリを割り当てるには、次のように設定します `opcache.memory_consumption = 2048`.

## 追加情報

* [パフォーマンスのベストプラクティス - PHP 設定](../../../performance/software.md#php-settings)
* [PHP オプションの設定](https://devdocs.magento.com/cloud/project/project-conf-files_magento-app.html#customize-phpini-settings)
* [クラウドインフラストラクチャー上のAdobe Commerceに関するデータベースのベストプラクティス](database-on-cloud.md)
* [クラウドインフラストラクチャー上のAdobe Commerceで最も一般的なデータベースの問題](../maintenance/resolve-database-performance-issues.md)
* [インデクサーの「スケジュールに従った更新」により、Adobe Commerceのパフォーマンスが最適化されます](../maintenance/indexer-configuration.md)
