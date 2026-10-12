---
title: デプロイメントの前提条件
description: Commerceを開発、ビルド、または実稼動システムにデプロイするための前提条件の一覧を参照してください。
feature: Configuration, Deploy
exl-id: 9ea0eeff-e0f8-4532-887c-5d7f07d89ddd
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
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
source-wordcount: '162'
ht-degree: 0%
---
# 開発、ビルド、および実稼動システムの前提条件

ファイルの権限と所有権は、開発、ビルド、本番システムをまたいで一貫性を持たせる必要があります。 それを実現するには、次のことをおこなう必要があります。

- 次の機能をすべて利用できます。

  - すべてのシステムで同じファイルシステム所有者のユーザー名を設定する
  - Web サーバーがすべてのシステムで同じユーザーとして実行されていることを確認します
  - ファイルシステムの所有者がすべてのシステムのweb サーバーグループにあることを確認します

- 次のガイドラインに従って、必要に応じて各システムのCommerce ファイルシステムの権限と所有権を変更します。

  - 開発とビルド：[ インストール前の所有権と権限を設定（2人のユーザー） ](file-system-permissions.md#set-up-two-owners-for-default-or-developer-mode)
  - 実稼動環境：[開発環境と実稼動環境におけるCommerceの所有権と権限](file-system-permissions.md)

>[!INFO]
>
>この方法を選択する場合は、ビルドシステムからコードを取得するたびにファイルシステムの権限と所有権を設定する必要があります（ビルドシステムでファイルシステムの所有者またはweb サーバーユーザーが異なる場合）。
