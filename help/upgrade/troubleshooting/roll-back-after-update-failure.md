---
title: モジュールの更新エラー後にロールバック
description: モジュールの更新エラーが発生した場合は、Adobe CommerceまたはMagento Open Sourceのアップグレードをトラブルシューティングします。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# モジュールの更新エラー後にロールバック

モジュールの更新に失敗した場合、コンソールログに次のようなメッセージが表示されます。

```terminal
[2015-08-14 12:12:02 CDT] Job "update {"components":[{"name":"example/module","version":"1.1.0"}]}" has been started
[2015-08-14 12:12:02 CDT] Starting composer update...
[2015-08-14 12:12:02 CDT] An error occurred while executing job "update {"components":
[{"name":"example/module","version":"1.1.0"}]}": Could not complete update {"components":
[{"name":"example/module","version":"1.1.0"}]} successfully: Cannot find component to update
```

前の例では、ロールバックするコンポーネントバージョンがありません。 コンポーネントのベンダーに問い合わせるか、自分で問題の解決を試みてください。

それまでの間、「 」をクリックして以前のバージョンにロールバックできます。 **ロールバック**：以前にバックアップをおこなっていない場合でも、データを復元します。
