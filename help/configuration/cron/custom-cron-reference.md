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

このトピックは、カスタムモジュールの crontab とオプションで cron グループの設定に役立ちます。 カスタムモジュールでタスクを定期的にスケジュールする必要がある場合は、そのモジュールの crontab を設定する必要があります。 A _crontab_ は cron ジョブ設定です。

オプションとして、カスタムグループを設定できます。このグループを使用することで、他の cron ジョブとは無関係に、そのグループで定義された cron ジョブを実行できます。

詳細な手順のチュートリアルについては、を参照してください。 [カスタム cron ジョブと cron グループの設定（チュートリアル）](custom-cron-tutorial.md).

Cron ジョブの概要については、を参照してください。 [Cron ジョブの設定](../cli/configure-cron-jobs.md).

## Cron グループの設定

この節では、カスタムモジュールの cron グループをオプションで作成する方法について説明します。 これを行う必要がない場合は、次の節に進みます。

A _cron グループ_ は、一度に複数のプロセスに対して cron を簡単に実行できる論理グループです。 ほとんどのCommerce モジュールでは、 `default` cron グループ。一部のモジュールはを使用 `index` グループ。

カスタムモジュール用に cron を実装している場合は、 `default` グループまたは別のグループ。

**モジュールに cron グループを設定するには：**:

を作成 `crontab.xml` モジュールディレクトリ内のファイル：

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
| `method` | メソッド： `classpath` を呼び出します。 |
| `time` | cron 形式でスケジュールします。 スケジュールがCommerce データベースまたは他のストレージで定義されている場合は、このパラメーターを省略します。 |

結果の `crontab.xml` 2 つのグループがある場合、次のようになります。

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

例として、を参照してください。 [Magento_顧客 crontab.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml).

### Cron グループオプションの指定

新しいグループを宣言し、その設定オプション（すべてがストア表示スコープで実行）を次の方法で指定できます。 `cron_groups.xml` ファイル。次の場所にあります。

```text
<your component base dir>/<vendorname>/module-<name>/etc/cron_groups.xml
```

次に、 `cron_groups.xml` ファイル：

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
| `schedule_generate_every` | スケジュールがに書き込まれる頻度（分） `cron_schedule` テーブル。 |
| `schedule_ahead_for` | スケジュールがに書き込まれる前の時間（分単位） `cron_schedule` テーブル。 |
| `schedule_lifetime` | Cron ジョブを開始しなければならない時間（分単位）、または Cron ジョブを見逃したと見なす時間（「遅すぎる」）。 |
| `history_cleanup_every` | Cron 履歴がデータベースに保持される時間（分単位）。 |
| `history_success_lifetime` | 正常に完了した cron ジョブの記録がデータベースに保持される時間（分単位）。 |
| `history_failure_lifetime` | 失敗した cron ジョブの記録がデータベースに保持される時間（分単位）。 |
| `use_separate_process` | 別の php プロセスでこの cron グループのジョブを実行します。 |

## Cron ジョブの無効化

Cron ジョブには `disable` にあるような機能 [監視者](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers). ただし、次の方法を使用して cron ジョブを無効にすることができます。 `schedule` 決して起こらない日付を含む時間。

例えば、 `visitor_clean` で定義された cron ジョブ `Magento_Customer` モジュール：

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
...
```

を無効にするには `visitor_clean` cron ジョブで、カスタムモジュールを作成して、 `visitor_clean` cron ジョブ `schedule`:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

さて、 `visitor_clean` cron ジョブは、2 月 30 日の 00:00 に実行するように設定されています。この日付では実行されません。
