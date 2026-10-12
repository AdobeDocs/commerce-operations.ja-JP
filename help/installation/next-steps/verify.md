---
title: インストールの確認
description: オンプレミス Adobe Commerceのインストールが正常に完了したことを確認するには、次の手順に従います。
exl-id: 0bd7ec01-c616-4384-ae26-db2ce3668caf
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
source-wordcount: '264'
ht-degree: 0%
---
# インストールの確認

web ブラウザーでストアフロントに移動します。 例えば、インストールベース URLが`http://www.example.com`の場合、ブラウザーのアドレスまたはロケーションバーに入力します。

次の図は、ストアフロントページの例を示しています。 次のように表示される場合、インストールは成功しました。

![Luma テーマを使用したストアフロント ](../../assets/installation/install-success_store-luma.png)

## ストアフロントの検証（サンプルデータなし）

web ブラウザーでストアフロントに移動します。 例えば、インストールベース URLが`http://www.example.com`の場合、ブラウザーのアドレスまたはロケーションバーに入力します。

次の図は、ストアフロントページの例を示しています。 次のように表示される場合、インストールは成功しました。

![ インストールが成功したことを確認するストアフロント ](../../assets/installation/install-success_store.png)

ページに`404 (Not Found)` エラーが表示されるか、スタイルが表示されない場合は、[ トラブルシューティング ](https://support.magento.com/hc/en-us/articles/360032994352)を参照してください。

## 管理者の確認

Web ブラウザーの管理者に移動します。 例えば、インストールベース URLが`http://www.example.com`、管理者URIが`admin_au1nT`の場合、ブラウザーのアドレスまたはロケーションバーに`http://www.example.com/admin_au1nT`と入力します。

（管理者URIは、`backend-frontname` インストールパラメーターの値で指定されます）。

プロンプトが表示されたら、管理者としてログインします。

次の図は、Admin ページの例を示しています。 次のように表示される場合、インストールは成功しました。

![ インストールが成功したことを確認する管理者](../../assets/installation/install_success_admin.png)

ページにスタイルが表示されない場合は、[ トラブルシューティング ](https://support.magento.com/hc/en-us/articles/360032994352)を参照してください。

次のような404 （見つかりません）エラーが発生した場合は、[PHPのバージョンエラーまたはブラウザーでAdobe Commerceにアクセスする際の404を参照してください](https://support.magento.com/hc/en-us/articles/360033117152)。

`The requested URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ was not found on this server.`
