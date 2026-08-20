---
title: OPcache メモリ サイズのベストプラクティス
description: Adobe Commerce プロジェクトでのOPcache メモリ使用量の特定の設定によるパフォーマンスの低下を回避する方法について説明します。
role: Developer
feature: Best Practices
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
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

[OPcache PHP モジュール ](https://www.php.net/manual/en/book.opcache.php)に少なくとも&#x200B;**2 GB**&#x200B;のメモリを割り当てます。 OPcache モジュールは`php.ini` ファイルで構成されています。 2048 MBのメモリを割り当てるには、`opcache.memory_consumption = 2048`を設定します。

## 追加情報

* [ パフォーマンスのベストプラクティス - PHP設定](../../../performance/software.md#php-settings)
* [PHP オプションの設定](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/configure-app-yaml)
* [Adobe Commerce on cloud infrastructureのデータベースのベストプラクティス](database-on-cloud.md)
* [Adobe Commerceのクラウドインフラストラクチャで最も一般的なデータベースの問題](../maintenance/resolve-database-performance-issues.md)
* [インデクサーの「スケジュールに従って更新」により、Adobe Commerceのパフォーマンスが最適化される](../maintenance/indexer-configuration.md)
