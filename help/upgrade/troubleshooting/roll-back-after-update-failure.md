---
title: モジュール更新失敗後のロールバック
description: モジュール更新エラーが発生した後の、Adobe Commerceのアップグレードのトラブルシューティング。
exl-id: 1537a6b1-b450-4f90-bffb-73359fa71598
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# モジュール更新失敗後のロールバック

モジュールの更新に失敗すると、次のようなメッセージがコンソールログに表示されます。

```
[2015-08-14 12:12:02 CDT] Job "update {"components":[{"name":"example/module","version":"1.1.0"}]}" has been started
[2015-08-14 12:12:02 CDT] Starting composer update...
[2015-08-14 12:12:02 CDT] An error occurred while executing job "update {"components":
[{"name":"example/module","version":"1.1.0"}]}": Could not complete update {"components":
[{"name":"example/module","version":"1.1.0"}]} successfully: Cannot find component to update
```

前述の例では、ロールバック先のコンポーネントバージョンはありません。 コンポーネントのベンダーに問い合わせるか、自分で問題を解決してみてください。

それまでの間、**ロールバック** をクリックすると、以前にバックアップしなかった場合でもデータを復元でき、以前のバージョンにロールバックできます。
