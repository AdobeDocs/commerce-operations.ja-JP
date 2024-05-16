---
title: 開発システムのセットアップ
description: Commerce アプリケーションの開発システムの設定方法について説明します。
exl-id: 242e9a38-2eb2-4090-8f59-3fd588f7ad3a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---

# 開発システムのセットアップ

任意の数の開発システムを用意できます。ただし、それらすべてに次の点が当てはまります。

- いずれもCommerce 2.2 以降を実行します
- すべてのCommerce コードは、ビルドシステムおよび実稼動システムと同じリポジトリでソース管理下にあります
- 各開発システムでは、次のいずれかを使用する必要があります [デフォルトモード](../bootstrap/application-modes.md#default-mode) または [開発者モード](../bootstrap/application-modes.md#developer-mode)
- ファイル・システムの所有権と権限が設定されています（を参照）。 [開発、ビルド、実稼動システムの前提条件](../deployment/technical-details.md).
- 次のすべてを確認します _除外済み_ ソース管理から：

   - `vendor` ディレクトリ（およびサブディレクトリ）
   - `generated` ディレクトリ（およびサブディレクトリ）
   - `pub/static` ディレクトリ（およびサブディレクトリ）
   - `app/etc/env.php` ファイル

- 確認する `app/etc/config.php` 等しい _included_ ソース管理で

Git を使用する場合、 `.gitignore` ファイルは、上記のほとんどを提供します。 を参照してください。 [`.gitignore` 参照](../reference/config-reference-gitignore.md).
