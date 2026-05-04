---
title: 管理者アカウントの作成、編集、またはロック解除
description: Adobe Commerce Admin アプリケーションの管理者アカウントを管理するには、次の手順に従います。
feature: Install, User Account
exl-id: d87871a1-717d-4662-b84d-98a018518286
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# 管理者アカウントの作成、編集、またはロック解除

このコマンドを使用する前に、次の操作を行う必要があります。

- [デプロイメント設定の作成](deployment.md)
- [Magento_Authorization モジュールとMagento_User モジュールを少なくとも有効にする](manage-modules.md)
- データベーススキーマの作成

>[!NOTE]
>
>データベースを作成する最も簡単な方法は、コマンド `magento setup:upgrade`を使用することです。

## 管理者の作成または編集

このコマンドを使用して、管理者を作成するか、既存の管理者を編集します。

>[!NOTE]
>
>管理者を編集する場合は、`first name`、`last name`および`password`のみを編集できます。

コマンドの使用状況：

```shell
bin/magento admin:user:create [--<parameter_name>=<value>, ...]
```

次の表でパラメーターと値を定義します。

| 名前 | 値 | 必要ですか？ |
|--- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--- |
| `--admin-firstname` | 管理者ユーザーの名前。 | はい |
| `--admin-lastname` | 管理者ユーザーの姓。 | はい |
| `--admin-email` | 管理者ユーザーのメールアドレス。 | はい |
| `--admin-user` | 管理者ユーザー名。 | はい |
| `--admin-password` | 管理者ユーザーパスワード。 パスワードは12文字以上の長さである必要があり、1文字以上のアルファベットと1文字以上の数字を含める必要があります。 <br><br>Adobeでは、より長く複雑なパスワードを指定することをお勧めします。 パスワード文字列にリテラル解釈を必要とする特殊文字（バックスラッシュやスペースなど）が含まれている場合は、パスワードを一重引用符で囲みます。 | はい |
| `--magento-init-params` | 任意のコマンドに追加して、アプリケーションの初期化パラメーターをカスタマイズします<br/><br/>例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | いいえ |

使用例：

```shell
bin/magento admin:user:create --admin-firstname=John --admin-lastname=Doe --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A0b9%t3g
```

```text
Created Magento administrator user named j.doe
```

必要なパラメーターのいずれかを指定しない場合、アプリケーションはCLIでそれについて尋ねます。

```shell
bin/magento admin:user:create
```

```text
Admin user: John
Admin password:
Admin email: j.doe.young@example.com
Admin first name: John
Admin last name: Doe Young
```

```text
Created Magento administrator user named John
```

次の例では、`j.doe`人の管理者ユーザーのうち`first name`、`last name`および`password`人を更新します。

```shell
bin/magento admin:user:create --admin-firstname="John X" --admin-lastname="Doe X" --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A1234567
```

```text
Created Magento administrator user named j.doe
```

## 管理者アカウントのロック解除

このコマンドを使用して、ロックされた管理者のアカウントのロックを解除します。通常は、複数の誤ったログイン試行が原因です。

```shell
bin/magento admin:user:unlock {username}
```

管理者のユーザー名を指定する必要があります。 例：

```shell
bin/magento admin:user:unlock admin
```

```text
The user account "admin" has been unlocked
```

アカウントのロックが解除されていないか、問題が発生した場合は、次のメッセージが表示されます。

```text
The user account "admin" was not locked or could not be unlocked
```

ユーザーが管理者であり、ユーザーがアクティブであり、アカウントがロックされていることを確認します。 管理者のロック済みユーザーのリストを表示するには、管理者としてログインし、**システム**/**権限**/**ロック済みユーザー**&#x200B;をクリックします。

アカウントが存在しない場合は、次のメッセージが表示されます。

```text
Couldn't find the user account "bob"
```
