---
title: 変更を移行
description: を使用して、最後のMagento 1 のデータ移行以降に変更されたデータのみを移行する方法を説明します [!DNL Data Migration Tool].
exl-id: c300c567-77d3-4c25-8b28-a7ae4ab0092e
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# 変更を移行

増分移行ツールにより、差分テーブル（のプレフィックスはです）がインストールされます `m2_cl_*`）およびトリガー（変更内容のトラッキング用）（Magento1 データベース内） [データの移行](data.md). これらの差分テーブルとトリガーは、データを最後に移行した後にMagento1 で行われた変更内容のみを移行するために不可欠です。 以下のような変更があります。

* 顧客がストアフロントを通じて追加したデータ（作成した注文、レビュー、顧客プロファイルの変更）

* 管理パネルに注文、製品、カテゴリが含まれるすべての操作

>[!NOTE]
>
>属性や CMS ページなど、管理者から入力されたその他の新規エンティティや更新されたエンティティは、増分移行に含まれず、移行されません。


開始する前に、次の手順に従って準備を行います。

1. としてアプリケーションサーバーにログインします [ファイルシステム所有者](../../../installation/prerequisites/file-system/overview.md).
1. をに変更します。 `/bin` ディレクトリを指定するか、システムに追加されていることを確認してください `PATH`.

を参照してください。 [最初の手順](overview.md#first-steps) の節を参照してください。

## 増分移行コマンドを実行します

増分変更の移行を開始するには、次を実行します。

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

ここで、

* `[-r|--reset]` は、最初から移行を開始するオプションの引数です。 この引数を使用して、移行をテストできます。

* `[-a|--auto]` は、整合性チェックエラーが発生した場合に移行が停止するのを防ぐオプション引数です。

* `{<path to config.xml>}` は、への絶対ファイルシステムパスです。 `config.xml`。この引数は必須です。

>[!NOTE]
>
>増分移行は継続的なプロセスで、5 秒ごとに自動的に再起動します。 Ctrl + C キーを使用して移行プロセスを中止します。


## サードパーティの拡張機能で作成されたデータを移行する

が含まれる `Delta` モード、 [!DNL Data Migration Tool] は、Magento独自のモジュールによってのみ作成されたデータを移行し、サードパーティの開発者によって作成されたコードや拡張機能には責任を負いません。 これらの拡張機能によってストアフロント データベースにデータが作成され、マーチャントがこのデータをMagento 2 に格納したい場合は、の config ファイルです。 [!DNL Data Migration Tool] 適宜、作成および変更する必要があります。

拡張機能に独自のテーブルがあり、デルタ移行のための変更を追跡する必要がある場合は、次の手順に従います。

1. 追跡するテーブルをに追加します `deltalog.xml` ファイル
1. を拡張する追加の delta クラスを作成します。 `Migration\App\Step\AbstractDelta`
1. の差分モードセクションに新しく作成したクラスの名前を追加します。 `config.xml`
