---
title: 開発システムの設定
description: コマースアプリケーションの開発システムを設定する方法を説明します。
exl-id: 242e9a38-2eb2-4090-8f59-3fd588f7ad3a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# 開発システムの設定

以下の条件を満たす場合、任意の数の開発システムを使用できます。

- すべて Commerce 2.2 以降を実行しています。
- すべてのコマースコードは、ビルドおよび実稼動システムと同じリポジトリ内のソース管理下にあります
- 各開発システムは、 [デフォルトモード](../bootstrap/application-modes.md#default-mode) または [開発者モード](../bootstrap/application-modes.md#developer-mode)
- ファイル・システムの所有権と権限が設定されています。 [開発、ビルド、実稼動システムの前提条件](../deployment/technical-details.md).
- 次のすべてを確認します。 _除外済み_ ソース管理から：

   - `vendor` ディレクトリ（およびサブディレクトリ）
   - `generated` ディレクトリ（およびサブディレクトリ）
   - `pub/static` ディレクトリ（およびサブディレクトリ）
   - `app/etc/env.php` ファイル

- 確認 `app/etc/config.php` 次に該当 _含む_ ソース管理下で

Git を使用する場合、 `.gitignore` ファイルは、前述のほとんどを提供します。 詳しくは、 [`.gitignore` 参照](../reference/config-reference-gitignore.md).
