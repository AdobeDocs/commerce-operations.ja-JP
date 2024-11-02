---
title: インデクサーの設定のベストプラクティス
description: インデクサー設定のベストプラクティスに従って、サイトのパフォーマンスを維持および最適化します。
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# インデクサー設定のベストプラクティス

サイトのパフォーマンスを最適化して維持するには、この記事で説明されているパフォーマンスのベストプラクティスを使用して、インデクサー設定を確認および更新します。

## 影響を受ける製品とバージョン

[ サポートされているすべてのバージョン ](../../../release/versions.md):

- クラウドインフラストラクチャー上のAdobe Commerce
- Adobe Commerce オンプレミス

## スケジュールに従って更新するインデクサーの設定

Adobe Commerceには、[!UICONTROL Update on Save] と [!DNL Update on Schedule] という 2 種類のインデクサーモードがあります。

- **[!UICONTROL Update on Save]** モードでは、カタログまたは他のデータが変更されるたびにインデックスを直ちに更新します。 例えば、管理者ユーザーがカテゴリに新しい製品を追加した場合、更新を保存すると、カテゴリの製品インデックスが直ちに再インデックス化されます。

- **[!UICONTROL Update on Schedule]** モードはデータの更新に関する情報を保存し、インデックスの再作成操作と更新は、スケジュールされた間隔でバックグラウンドで実行される cron ジョブによって管理されます。 cron ジョブは、実行されるたびに再インデックスを実行するとは限りません。 インデクサーの変更ログに新しいエントリがある場合（例えば、インデクサーのバックログがある場合）にのみインデックスを再作成します。

複数の管理者を含む大規模なストアがバックエンドで動作している、または、多くの読み込みと書き出しのトリガーが頻繁にインデックスを更新している。 サイトインデックス設定が [!UICONTROL Update on Save] モードに設定されている場合、頻繁なインデックス再作成はデータベースのパフォーマンスを低下させ、サイトのパフォーマンスが低下し、特に大規模なストアでインデックス再作成プロセスに長い遅延が発生します。

サイトのパフォーマンスを最大化するには、インデックス作成に関する次のベストプラクティスに従います。

- インデックス設定を確認します。
- 大規模なサイトや、頻繁に更新が行われ、トラフィックが多いサイトでは、インデクサーを _[!UICONTROL Update on Schedule]_に設定します。 [ インデックス管理 ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management#change-the-index-mode) を参照してください。
- インデックス管理については、[ パフォーマンスのベストプラクティス ](../../../performance/configuration.md) に従ってください。

>[!IMPORTANT]
>
>[!DNL Customer Grid] のインデックスは、[!UICONTROL Update on Save] オプションを使用してのみ再作成できます。 このインデックスは、`Update by Schedule` オプションをサポートしていません。

## 追加情報

- [管理者ユーザー向けのインデックス管理](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [MagentoCLI を使用したインデックス管理 ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [ 開発者向けのインデックス作成の概要 ](https://developer.adobe.com/commerce/php/development/components/indexing/)
