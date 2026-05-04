---
title: .gitignore リファレンス
description: Adobe Commerce プロジェクトの.gitignore リストにファイルを追加する方法について説明します。 バージョン管理とファイル除外のベストプラクティス。
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# .gitignore リファレンス

Magento Open Sourceには、基本`.gitignore` ファイルが含まれています。 最新のCommerce `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore) ファイルの[を参照してください。 `.gitignore` リストにあるファイルを追加する必要がある場合は、コミットのステージング時に`-f` （強制）オプションを使用できます。

```shell
git add <path/filename> -f
```
