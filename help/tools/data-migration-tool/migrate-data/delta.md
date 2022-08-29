---
title: 変更を移行
description: を使用して、前回のMagento1 のデータ移行以降に変更されたデータのみを移行する方法を説明します。 [!DNL Data Migration Tool].
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---


# 変更を移行

増分移行ツールでは、deltalog テーブル（プレフィックス付き）がインストールされます `m2_cl_*`) およびトリガー（変更を追跡するため）を、 [データの移行](data.md). これらのデタログ表とトリガーは、最後にデータを移行した時点以降にMagento1 でおこなわれた変更のみを移行するために必要です。 次の変更がおこなわれました。

* 顧客がを通じて追加したデータ [店頭](https://glossary.magento.com/storefront) （顧客プロファイルの作成済みの注文、レビュー、変更）

* 内の注文、製品、カテゴリを持つすべての操作 [管理者](https://glossary.magento.com/magento-admin) パネル

>[!NOTE]
>
>属性や CMS ページなど、管理者から入力されたその他の新規または更新済みのエンティティは、増分移行には含まれず、移行されません。


開始する前に、次の手順に従って準備を行います。

1. としてMagentoサーバーにログイン [ファイルシステムの所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Magento `/bin` ディレクトリに追加するか、システムの PATH に追加されていることを確認します。

詳しくは、 [最初の手順](overview.md#first-steps) 」の節を参照してください。

## 増分移行コマンドを実行します。

増分変更の移行を開始するには、次のコマンドを実行します。

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

ここで、

* `[-r|--reset]` は、最初から移行を開始するオプションの引数です。 この引数は、移行のテストに使用できます。

* `[-a|--auto]` は、整合性チェックエラーが発生した場合に移行を停止しないようにする、オプションの引数です。

* `{<path to config.xml>}` は、 `config.xml`;この引数は必須です。

>[!NOTE]
>
>増分移行は継続的なプロセスです。5 秒ごとに自動的に再起動します。 移行プロセスを中止するには、Ctrl + C キーを押します。


## サードパーティの拡張機能で作成されたデータの移行

内 `Delta` mode, [!DNL Data Migration Tool] は、Magento独自のモジュールによってのみ作成されたデータを移行し、サードパーティ開発者によるコードや拡張に対する責任を負いません。 これらの拡張機能がストアフロントデータベースにデータを作成し、商人がこのデータをMagento2 — [!DNL Data Migration Tool] を適切に作成および変更する必要があります。

次の場合、 [拡張](https://glossary.magento.com/extension) には独自のテーブルがあり、差分移行に伴う変更を追跡する必要があります。次の手順に従います。

1. 追跡するテーブルを `deltalog.xml` ファイル
1. 追加の delta クラスを作成し、 `Migration\App\Step\AbstractDelta`
1. 新しく作成したクラスの名前をのデルタモードセクションに追加 `config.xml`