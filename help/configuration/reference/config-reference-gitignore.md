---
title: .gitignore リファレンス
description: 無視リストに含まれるファイルの追加方法を参照してください。
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '51'
ht-degree: 0%

---

# .gitignore リファレンス

Magento Open Sourceには、ベース `.gitignore` ファイルが含まれています。 [ 最新のCommerce `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore) ファイルを参照してください。 `.gitignore` リストにあるファイルを追加する必要がある場合は、コミットをステージングするときに `-f` （force） オプションを使用できます。

```bash
git add <path/filename> -f
```
