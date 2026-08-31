---
title: 開発システムの設定
description: Commerce アプリケーションの開発システムをセットアップする方法について説明します。
exl-id: 242e9a38-2eb2-4090-8f59-3fd588f7ad3a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---

# 開発システムの設定

任意の数の開発システムを使用できます。ただし、すべてのシステムに当てはまるものを次に示します。

- これらはすべてCommerce 2.2以降を実行します
- すべてのCommerce コードは、ビルドシステムと実稼動システムと同じリポジトリ内のソース管理の下にあります
- 各開発システムでは、[ デフォルトモード ](../bootstrap/application-modes.md#default-mode)または[開発者モード ](../bootstrap/application-modes.md#developer-mode)のいずれかを使用する必要があります
- このファイル システムには、[開発、ビルド、および実稼動システムの前提条件](../deployment/technical-details.md)で説明されているように、ファイル システムの所有権と権限が設定されています。
- 次のすべてが&#x200B;_ソース管理から除外_&#x200B;されていることを確認します。

  - `vendor` ディレクトリ （およびサブディレクトリ）
  - `generated` ディレクトリ （およびサブディレクトリ）
  - `pub/static` ディレクトリ （およびサブディレクトリ）
  - `app/etc/env.php` ファイル

- `app/etc/config.php`がソース管理に&#x200B;_インクルード_&#x200B;されていることを確認してください

Gitを使用する場合、`.gitignore` ファイルには上記のほとんどの機能が用意されています。 [`.gitignore`参照](../reference/config-reference-gitignore.md)を参照してください。
