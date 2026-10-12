---
title: .gitignore リファレンス
description: Adobe Commerce プロジェクトの.gitignore リストにファイルを追加する方法について説明します。 バージョン管理とファイル除外のベストプラクティス。
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%
---
# .gitignore リファレンス

Magento Open Sourceには、基本`.gitignore` ファイルが含まれています。 最新のCommerce `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore) ファイルの[を参照してください。 `.gitignore` リストにあるファイルを追加する必要がある場合は、コミットのステージング時に`-f` （強制）オプションを使用できます。

```shell
git add <path/filename> -f
```
