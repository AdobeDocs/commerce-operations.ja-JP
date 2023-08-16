---
title: カスタム cron ジョブと cron グループの参照
description: cron グループを使用して cron をカスタマイズする方法を説明します。
exl-id: 16e342ff-aa94-4e31-8c75-dfea1ef02706
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# Cron リファレンスのカスタマイズ

このトピックでは、crontabs を設定し、カスタムモジュール用の cron グループを任意で設定する方法について説明します。 カスタムモジュールが定期的にタスクをスケジュールする必要がある場合は、そのモジュール用の crontab を設定する必要があります。 A _crontab_ は cron ジョブ設定です。

必要に応じて、カスタムグループを設定できます。カスタムグループでは、他の cron ジョブとは別に、そのグループで定義された cron ジョブを個別に実行できます。

詳細なチュートリアルについては、 [カスタム cron ジョブと cron グループの設定（チュートリアル）](custom-cron-tutorial.md).

cron ジョブの概要については、 [cron ジョブの設定](../cli/configure-cron-jobs.md).

## Cron グループの設定

このセクションでは、カスタムモジュールの cron グループを任意で作成する方法について説明します。 これをおこなう必要がない場合は、次の節に進みます。

A _cron グループ_ は、一度に複数のプロセスに対して cron を簡単に実行できる論理グループです。 ほとんどのコマースモジュールでは、 `default` cron グループ。一部のモジュールは `index` グループ化します。

カスタムモジュールに cron を実装する場合は、 `default` グループまたは別のグループに関連付けることができます。

**モジュールの cron グループを設定するには**:

の作成 `crontab.xml` ファイルの内容は次のとおりです。

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

次の場合：

| 値 | 説明 |
|---|---|
| `group_name` | cron グループの名前。 グループ名を一意にする必要はありません。 cron は一度に 1 つのグループに対して実行できます。 |
| `job_name` | この cron ジョブの一意の ID。 |
| `classpath` | インスタンス化するクラス（クラスパス）。 |
| `method` | でのメソッド `classpath` を呼び出します。 |
| `time` | Cron 形式のスケジュール。 スケジュールが Commerce データベースまたは他のストレージで定義されている場合は、このパラメータを省略します。 |

結果 `crontab.xml` との 2 つのグループは、次のようになります。

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

例えば、 [Magento_Customer crontab.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml).

### Cron グループオプションの指定

新しいグループを宣言し、その設定オプション（すべてストア表示範囲で実行）を `cron_groups.xml` ファイル：次の場所にあります。

```text
<your component base dir>/<vendorname>/module-<name>/etc/cron_groups.xml
```

以下に、 `cron_groups.xml` ファイル：

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

次の場合：

| オプション | 説明 |
| -------------------------- | ------------------------------------------------------------------------------------------------------ |
| `schedule_generate_every` | スケジュールが `cron_schedule` 表。 |
| `schedule_ahead_for` | スケジュールが `cron_schedule` 表。 |
| `schedule_lifetime` | Cron ジョブを開始する必要がある時間（分）、または Cron ジョブが失われたと見なされる時間（実行するには「遅すぎる」）。 |
| `history_cleanup_every` | cron 履歴がデータベースに保持される時間（分）。 |
| `history_success_lifetime` | 正常に完了した cron ジョブのレコードがデータベースに保持される時間（分）。 |
| `history_failure_lifetime` | 失敗した cron ジョブのレコードがデータベースに保持される時間（分）。 |
| `use_separate_process` | この cron グループのジョブを別の php プロセスで実行します。 |

## cron ジョブを無効にする

Cron ジョブには `disable` ～に対するのと同じ特徴 [監視者](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers). ただし、cron ジョブは、次の方法を使用して無効にできます。 `schedule` 発生しない日付を含む時間です。

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

を無効にするには、以下を実行します。 `visitor_clean` cron ジョブ、カスタムモジュールの作成、 `visitor_clean` cron ジョブ `schedule`:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

さて、 `visitor_clean` cron ジョブは、2 月 30 日の 0 時（決して発生しない日）に実行されるように設定されています。
