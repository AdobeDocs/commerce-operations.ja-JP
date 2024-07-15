---
title: カスタム cron ジョブと cron グループのリファレンス
description: cron グループを使用して cron をカスタマイズする方法を説明します。
exl-id: 16e342ff-aa94-4e31-8c75-dfea1ef02706
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---

# Cron リファレンスのカスタマイズ

このトピックは、カスタムモジュールの crontab とオプションで cron グループの設定に役立ちます。 カスタムモジュールでタスクを定期的にスケジュールする必要がある場合は、そのモジュールの crontab を設定する必要があります。 _crontab_ は cron ジョブ設定です。

オプションとして、カスタムグループを設定できます。このグループを使用することで、他の cron ジョブとは無関係に、そのグループで定義された cron ジョブを実行できます。

詳しい手順のチュートリアルについては、[ カスタム cron ジョブと cron グループの設定（チュートリアル） ](custom-cron-tutorial.md) を参照してください。

cron ジョブの概要については、[cron ジョブの設定 ](../cli/configure-cron-jobs.md) を参照してください。

## Cron グループの設定

この節では、カスタムモジュールの cron グループをオプションで作成する方法について説明します。 これを行う必要がない場合は、次の節に進みます。

_cron グループ_ は、一度に複数のプロセスに対して cron を簡単に実行できる論理グループです。 ほとんどのCommerce モジュールは `default` cron グループを使用します。一部のモジュールは `index` グループを使用します。

カスタムモジュール用に cron を実装する場合は、`default` グループを使用するか、別のグループを使用するかを選択できます。

**モジュールに cron グループを設定するには**:

モジュールディレクトリに `crontab.xml` ファイルを作成します。

```text
<your component base dir>/<vendorname>/module-<name>/etc/crontab.xml
```

1 つのグループの場合、ファイルには次の内容が含まれている必要があります。

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="<group_name>">
        <job name="<job_name>" instance="<classpath>" method="<method>">
            <schedule><time></schedule>
        </job>
    </group>
</config>
```

ここで、

| 値 | 説明 |
|---|---|
| `group_name` | Cron グループの名前。 グループ名は一意である必要はありません。 一度に 1 つのグループに対して cron を実行できます。 |
| `job_name` | この Cron ジョブの一意の ID。 |
| `classpath` | インスタンス化するクラス （クラスパス）。 |
| `method` | 呼び出 `classpath` メソッド。 |
| `time` | cron 形式でスケジュールします。 スケジュールがCommerce データベースまたは他のストレージで定義されている場合は、このパラメーターを省略します。 |

2 つのグループを持つ結果の `crontab.xml` は、次のようになります。

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="<job_1_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_2_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
    <group id="index">
        <job name="<job_3_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_4_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

Magento例として、[Customer_crontab.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml) を参照してください。

### Cron グループオプションの指定

新しいグループを宣言し、次の場所にある `cron_groups.xml` ファイルを介して設定オプション（すべてのグループがストアビュースコープで実行される）を指定できます。

```text
<your component base dir>/<vendorname>/module-<name>/etc/cron_groups.xml
```

次に、`cron_groups.xml` ファイルの例を示します。

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/cron_groups.xsd">
    <group id="<group_name>">
        <schedule_generate_every>1</schedule_generate_every>
        <schedule_ahead_for>4</schedule_ahead_for>
        <schedule_lifetime>2</schedule_lifetime>
        <history_cleanup_every>10</history_cleanup_every>
        <history_success_lifetime>60</history_success_lifetime>
        <history_failure_lifetime>600</history_failure_lifetime>
        <use_separate_process>1</use_separate_process>
    </group>
</config>
```

ここで、

| オプション | 説明 |
| -------------------------- | ------------------------------------------------------------------------------------------------------ |
| `schedule_generate_every` | スケジュールが `cron_schedule` テーブルに書き込まれる頻度（分）。 |
| `schedule_ahead_for` | スケジュールが `cron_schedule` テーブルに書き込まれる前の時間（分単位）。 |
| `schedule_lifetime` | Cron ジョブを開始しなければならない時間（分単位）、または Cron ジョブを見逃したと見なす時間（「遅すぎる」）。 |
| `history_cleanup_every` | Cron 履歴がデータベースに保持される時間（分単位）。 |
| `history_success_lifetime` | 正常に完了した cron ジョブの記録がデータベースに保持される時間（分単位）。 |
| `history_failure_lifetime` | 失敗した cron ジョブの記録がデータベースに保持される時間（分単位）。 |
| `use_separate_process` | 別の php プロセスでこの cron グループのジョブを実行します。 |

## Cron ジョブの無効化

Cron ジョブには、[ 監視者 ](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers) 向けの `disable` 機能はありません。 ただし、cron ジョブは、次の手法を使用して無効にすることができます。`schedule` 発生することのない日付を含む時間を無効にします。

例えば、モジュールで定義した `visitor_clean` cron ジョブ `Magento_Customer` 無効にします。

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
...
```

`visitor_clean` cron ジョブを無効にするには、カスタムモジュールを作成し、`visitor_clean` cron ジョブを次の `schedule` うに書き換えます。

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

現在、`visitor_clean` cron ジョブは、2 月 30 日の 00:00 に実行するように設定されています。この日付は、実行されません。
