---
title: モジュールの更新失敗後にロールバック
description: モジュールのアップデートエラーが発生した後、Adobe Commerceのアップグレードをトラブルシューティングします。
exl-id: 1537a6b1-b450-4f90-bffb-73359fa71598
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
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
