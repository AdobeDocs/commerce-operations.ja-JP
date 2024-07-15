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
- 各開発システムは、[ デフォルトモード ](../bootstrap/application-modes.md#default-mode) または [ 開発者モード ](../bootstrap/application-modes.md#developer-mode) のいずれかを使用する必要があります
- [ 開発、ビルド、実稼働システムの前提条件 ](../deployment/technical-details.md) で説明されているように、ファイルシステムの所有権と権限が設定されています。
- 次のすべてがソース管理から _除外_ されていることを確認します。

   - `vendor` ディレクトリ（およびサブディレクトリ）
   - `generated` ディレクトリ（およびサブディレクトリ）
   - `pub/static` ディレクトリ（およびサブディレクトリ）
   - `app/etc/env.php` ファイル

- `app/etc/config.php` がソース管理に _含まれる_ ことを確認

Git を使用する場合は、上記のほとんどを `.gitignore` ファイルで提供します。 [`.gitignore` リファレンスを参照してください ](../reference/config-reference-gitignore.md)。
