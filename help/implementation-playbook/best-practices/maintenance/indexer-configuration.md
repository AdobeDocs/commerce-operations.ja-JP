---
title: インデクサーの設定のベストプラクティス
description: インデクサー設定のベストプラクティスに従って、サイトパフォーマンスを維持および最適化します。
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%
---
# インデクサー設定のベストプラクティス

サイトのパフォーマンスを最適化および維持するには、この記事で説明するパフォーマンスのベストプラクティスを使用して、インデクサー設定を確認および更新します。

## 影響を受ける製品とバージョン

[&#x200B; サポートされているすべてのバージョン &#x200B;](../../../release/versions.md) /:

- Adobe Commerce on cloud infrastructure
- Adobe Commerce オンプレミス

## スケジュールに基づいて更新するインデクサーの設定

Adobe Commerceには、2種類のインデクサーモードがあります：[!UICONTROL Update on Save]と[!DNL Update on Schedule]。

- **[!UICONTROL Update on Save]** モードは、カタログまたはその他のデータが変更されるたびに、インデックスを即座に更新します。 例えば、管理者ユーザーがカテゴリに新しい製品を追加した場合、更新が保存されると、カテゴリ製品インデックスが直ちにインデックス付けされます。

- **[!UICONTROL Update on Schedule]** モードでは、データ更新に関する情報が保存され、インデックス再作成操作とインデックス更新は、スケジュールされた間隔でバックグラウンドで実行されるcron ジョブによって管理されます。 cron ジョブは、実行するたびにインデックスを再作成するとは限りません。 インデックスの変更ログに新しいエントリがある場合にのみインデックスを再作成します（例えば、インデックスにバックログがある場合）。

複数の管理者がバックエンドで作業している大規模なストアがある、またはトリガーのインポートとエクスポートが多い、インデックスの更新が頻繁におこなわれる。 サイトインデックス設定が[!UICONTROL Update on Save] モードに設定されている場合、頻繁なインデックス再作成によってデータベースのパフォーマンスが低下し、サイトのパフォーマンスが低下し、特に大規模なストアの場合、インデックス再作成プロセスに長い遅延が発生します。

サイトパフォーマンスを最大化するには、インデックス作成に関する次のベストプラクティスに従います。

- インデックス設定を確認します。
- 大規模なサイトや、頻繁な更新と大量のトラフィックを伴うサイトでは、インデックスを&#x200B;_[!UICONTROL Update on Schedule]_&#x200B;に設定します。 [&#x200B; インデックス管理](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management#change-the-index-mode)を参照してください。
- インデックスの管理については、[&#x200B; パフォーマンスのベストプラクティス &#x200B;](../../../performance/configuration.md)に従ってください。

>[!IMPORTANT]
>
>2.4.8で[!DNL Customer Grid] インデクサーの動作が変更されました。
>
>- **2.4.8**&#x200B;以前：[!DNL Customer Grid] インデクサーは[!UICONTROL Update on Save] オプションを使用してのみインデックスを再作成でき、[!UICONTROL Update by Schedule] オプションはサポートしていません。
>- **2.4.8以降**: [!DNL Customer Grid] インデクサーは[!UICONTROL Update on Save]と[!UICONTROL Update by Schedule] モードの両方をサポートし、デフォルトは[!UICONTROL Update by Schedule]です。

## 追加情報

- [管理者ユーザーのインデックス管理](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Magento CLIを使用したインデックス管理](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [開発者向けインデックス作成の概要](https://developer.adobe.com/commerce/php/development/components/indexing/)
