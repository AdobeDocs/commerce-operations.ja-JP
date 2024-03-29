---
title: インデクサーの設定のベストプラクティス
description: インデクサー設定のベストプラクティスに従って、サイトのパフォーマンスを維持および最適化します。
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: af66d47279245f8ee105030bbb33d77b1b35c3e5
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# インデクサー設定のベストプラクティス

サイトのパフォーマンスを最適化および維持するには、この記事で説明するパフォーマンスのベストプラクティスを使用して、インデクサーの設定を確認および更新します。

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure
- Adobe Commerceオンプレミス

## スケジュールに従って更新するインデクサーを設定します

Adobe Commerceには次の 2 種類のインデクサーモードがあります。 [!UICONTROL Update on Save] （デフォルト設定）および [!DNL Update on Schedule].

- **[!UICONTROL Update on Save]** mode は、カタログや他のデータが変更された場合には常にインデックスを直ちに更新します。 例えば、管理者ユーザーが新しい製品をカテゴリに追加した場合、カテゴリ製品インデックスは、更新が保存されるとすぐに再インデックスされます。

- **[!UICONTROL Update on Schedule]** mode は、データの更新に関する情報を格納し、インデックス再作成操作とインデックス更新は、スケジュールされた間隔でバックグラウンドで実行される cron ジョブによって管理されます。 cron ジョブは、実行するたびに再インデックスを実行するわけではありません。 インデクサ変更ログに新しいエントリが存在する場合（たとえば、インデクサにバックログが存在する場合）にのみインデックスを再作成します。

複数の管理者を含む大規模なストアがバックエンドで作業している場合、または多数のインポートとエクスポートのトリガーが頻繁にインデックスの更新をおこなっています。 サイトのインデックス設定が [!UICONTROL Update on Save] モード、頻繁にインデックスを再作成すると、データベースのパフォーマンスが低下し、サイトのパフォーマンスが低下し、特に大規模なストアでのインデックス再作成プロセスに長時間の遅延が生じます。

サイトのパフォーマンスを最大化するには、インデックス作成に関する次のベストプラクティスに従います。

- インデックス設定を確認します。
- インデクサーをに設定します。 _[!UICONTROL Update on Schedule]_大規模なサイト、頻繁な更新と大量のトラフィックを含むサイトの場合に使用します。 詳しくは、 [インデックス管理](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).
- フォロー [パフォーマンスのベストプラクティス](../../../performance/configuration.md) を参照してください。

>[!IMPORTANT]
>
>The [!DNL Customer Grid] は、 [!UICONTROL Update on Save] オプション。 このインデックスは、 `Update by Schedule` オプション。

## 追加情報

- [管理者ユーザー向けのインデックス管理](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [MagentoCLI を使用したインデックス管理](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [開発者向けのインデックス作成の概要](https://developer.adobe.com/commerce/php/development/components/indexing/)
