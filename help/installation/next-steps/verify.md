---
title: インストールの確認
description: 次の手順に従って、オンプレミスのAdobe Commerceが正常にインストールされたことを確認します。
exl-id: 0bd7ec01-c616-4384-ae26-db2ce3668caf
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# インストールの確認

Web ブラウザーでストアフロントに移動します。 例えば、インストールベース URL が `http://www.example.com` の場合は、ブラウザーのアドレスまたはロケーションバーに入力します。

次の図は、ストアフロントページのサンプルを示しています。 次のように表示される場合、インストールは成功です。

![Luma テーマを使用したストアフロント &#x200B;](../../assets/installation/install-success_store-luma.png)

## ストアフロントの検証（サンプルデータなし）

Web ブラウザーでストアフロントに移動します。 例えば、インストールベース URL が `http://www.example.com` の場合は、ブラウザーのアドレスまたはロケーションバーに入力します。

次の図は、ストアフロントページのサンプルを示しています。 次のように表示される場合、インストールは成功です。

![&#x200B; インストールが成功したことを確認するストアフロント &#x200B;](../../assets/installation/install-success_store.png)

ページに `404 (Not Found)` エラーが表示される場合や、スタイルが表示されない場合は、[&#x200B; トラブルシューティング &#x200B;](https://support.magento.com/hc/en-us/articles/360032994352) を参照してください。

## 管理者の確認

Web ブラウザーで管理者に移動します。 例えば、インストールベース URL が `http://www.example.com` で、管理者 URI が `admin_au1nT` の場合、ブラウザーのアドレスまたはロケーションバーに `http://www.example.com/admin_au1nT` を入力します。

（管理 URI は、`backend-frontname` インストールパラメーターの値で指定されます）。

プロンプトが表示されたら、管理者としてログインします。

次の図に、管理ページのサンプルを示します。 次のように表示される場合、インストールは成功です。

![&#x200B; インストールが成功したことを確認する Admin](../../assets/installation/install_success_admin.png)

ページにスタイルが表示されない場合は、[&#x200B; トラブルシューティング &#x200B;](https://support.magento.com/hc/en-us/articles/360032994352) を参照してください。

次のような 404 （Not Found） エラーが発生した場合は、[PHP version error or 404 when access Adobe Commerce in browser](https://support.magento.com/hc/en-us/articles/360033117152) を参照してください。

`The requested URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ was not found on this server.`
