---
title: モジュールの更新失敗後にロールバック
description: モジュールのアップデートエラーが発生した後、Adobe Commerceのアップグレードをトラブルシューティングします。
exl-id: 1537a6b1-b450-4f90-bffb-73359fa71598
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
source-wordcount: '89'
ht-degree: 0%
---
# モジュールの更新失敗後にロールバック

モジュールの更新に失敗した場合、次のようなメッセージがコンソールログに表示されます。

```shell
[2015-08-14 12:12:02 CDT] Job "update {"components":[{"name":"example/module","version":"1.1.0"}]}" has been started
[2015-08-14 12:12:02 CDT] Starting composer update...
[2015-08-14 12:12:02 CDT] An error occurred while executing job "update {"components":
[{"name":"example/module","version":"1.1.0"}]}": Could not complete update {"components":
[{"name":"example/module","version":"1.1.0"}]} successfully: Cannot find component to update
```

前述の例では、ロールバックするコンポーネントバージョンはありません。 コンポーネントベンダーに問い合わせるか、自分で問題を解決してみてください。

また、**ロールバック**&#x200B;をクリックして、以前のバージョンにロールバックできます。以前のバージョンでバックアップしなくても、データを復元できます。
