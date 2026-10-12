---
title: カスタム cron ジョブとcron グループ参照
description: Adobe Commerceでcron グループとcrontabsを使用してcronをカスタマイズする方法について説明します。 カスタムモジュールの設定とスケジュールされたタスクの設定について説明します。
exl-id: 16e342ff-aa94-4e31-8c75-dfea1ef02706
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
source-wordcount: '549'
ht-degree: 0%
---
# crons リファレンスのカスタマイズ

このトピックでは、カスタムモジュール用にcrontabsとcron グループを設定する方法を説明します。 カスタムモジュールでタスクを定期的にスケジュールする必要がある場合は、そのモジュールにcrontabを設定する必要があります。 _crontab_&#x200B;はcron ジョブ設定です。

オプションで、カスタムグループを設定できます。特に、そのグループで定義されたcron ジョブを他のcron ジョブとは独立して実行できます。

ステップバイステップチュートリアルについては、[&#x200B; カスタム cron ジョブとcron グループの設定（チュートリアル） &#x200B;](custom-cron-tutorial.md)を参照してください。

cron ジョブの概要については、[cron ジョブの設定](../cli/configure-cron-jobs.md)を参照してください。

## cron グループの設定

この節では、カスタムモジュールのcron グループをオプションで作成する方法について説明します。 これを行う必要がない場合は、次のセクションに進みます。

_cron グループ_&#x200B;は、一度に複数のプロセスでcronを簡単に実行できる論理グループです。 ほとんどのCommerce モジュールは`default` cron グループを使用しています。一部のモジュールは`index` グループを使用しています。

カスタムモジュールにcronを実装する場合は、`default` グループまたは別のグループを使用できます。

**モジュールのcron グループを設定するには**:

モジュールディレクトリに`crontab.xml` ファイルを作成します。

```text
<your component base dir>/<vendorname>/module-<name>/etc/crontab.xml
```

1つのグループの場合、ファイルには次の内容が含まれている必要があります。

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

どこで：

| 値 | 説明 |
|---|---|
| `group_name` | cron グループの名前。 グループ名は一意である必要はありません。 cronは一度に1つのグループに対して実行できます。 |
| `job_name` | このcron ジョブの一意のID。 |
| `classpath` | インスタンス化するクラス （クラスパス）。 |
| `method` | 呼び出す`classpath`のメソッド。 |
| `time` | cron形式でスケジュールします。 スケジュールがCommerce データベースまたはその他のストレージで定義されている場合は、このパラメーターを省略します。 |

2つのグループを持つ結果の`crontab.xml`は次のようになります。

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

例として、[Magento_Customer crontab.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml)を参照してください。

### Cron グループオプションの指定

新しいグループを宣言し、次の場所にある`cron_groups.xml` ファイルを使用して、その構成オプション（すべてストアビュースコープで実行）を指定できます。

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

どこで：

| オプション | 説明 |
| -------------------------- | ------------------------------------------------------------------------------------------------------ |
| `schedule_generate_every` | スケジュールが`cron_schedule` テーブルに書き込まれる頻度（分単位）。 |
| `schedule_ahead_for` | スケジュールが`cron_schedule` テーブルに書き込まれる前の時間（分単位）。 |
| `schedule_lifetime` | cron ジョブを開始する必要がある時間（分単位）またはcron ジョブが見逃されたと見なされる時間（「実行が遅すぎます」）。 |
| `history_cleanup_every` | cron履歴がデータベースに保持される時間（分単位）。 |
| `history_success_lifetime` | 正常に完了したcron ジョブのレコードがデータベースに保持される時間（分単位）。 |
| `history_failure_lifetime` | 失敗したcron ジョブのレコードがデータベースに保持される時間（分単位）。 |
| `use_separate_process` | このcron グループのジョブを別のphp プロセスで実行する |

## cron ジョブを無効にする

Cron ジョブには、[&#x200B; オブザーバー](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers)と同様に`disable`機能がありません。 ただし、cron ジョブは、次の手法を使用して無効にできます。`schedule`は、発生しない日付を含む時間です。

例えば、`Magento_Customer` モジュールで定義された`visitor_clean` cron ジョブを無効にします。

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
...
```

`visitor_clean` cron ジョブを無効にするには、カスタムモジュールを作成し、`visitor_clean` cron ジョブ `schedule`を書き換えます。

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

これで、`visitor_clean` cron ジョブが2月30日の00:00に実行されるように設定されました。この日付は実行されません。
