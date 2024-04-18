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

Web ブラウザーでストアフロントに移動します。 例えば、インストールベース URL がの場合 `http://www.example.com`を選択し、ブラウザーのアドレスまたはロケーションバーに入力します。

次の図は、ストアフロントページのサンプルを示しています。 次のように表示される場合、インストールは成功です。

![Luma テーマを使用したストアフロント](../../assets/installation/install-success_store-luma.png)

## ストアフロントの検証（サンプルデータなし）

Web ブラウザーでストアフロントに移動します。 例えば、インストールベース URL がの場合 `http://www.example.com`を選択し、ブラウザーのアドレスまたはロケーションバーに入力します。

次の図は、ストアフロントページのサンプルを示しています。 次のように表示される場合、インストールは成功です。

![インストールが正常に完了したことを確認するストアフロント](../../assets/installation/install-success_store.png)

ページに「」と表示される場合 `404 (Not Found)` エラーが発生したか、スタイルが表示されません。を参照してください [トラブルシューティング](https://support.magento.com/hc/en-us/articles/360032994352).

## 管理者の確認

Web ブラウザーで管理者に移動します。 例えば、インストールベース URL がの場合 `http://www.example.com`管理 URI はです。 `admin_au1nT`、と入力します `http://www.example.com/admin_au1nT` ブラウザーのアドレスまたはロケーションバーで上書きできます。

（管理 URI は値 `backend-frontname` インストールパラメーター）。

プロンプトが表示されたら、管理者としてログインします。

次の図に、管理ページのサンプルを示します。 次のように表示される場合、インストールは成功です。

![インストールが成功したことを確認する管理者](../../assets/installation/install_success_admin.png)

ページにスタイルが表示されない場合は、を参照してください [トラブルシューティング](https://support.magento.com/hc/en-us/articles/360032994352).

次のような 404 （見つかりません）エラーが発生した場合は、を参照してください。 [ブラウザーでAdobe Commerceにアクセスする際に PHP バージョンエラーまたは 404。](https://support.magento.com/hc/en-us/articles/360033117152).

`The requested URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ was not found on this server.`
