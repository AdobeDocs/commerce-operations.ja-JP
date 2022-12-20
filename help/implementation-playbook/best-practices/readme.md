---
source-git-commit: 8013e6339d42108dbefbbafa5db7f9ffc5288c4f
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 0%

---
# ベストプラクティス：コンテンツ作成ワークフロー

このドキュメントでは、 *[ベストプラクティス](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html)* コンテンツ *Adobe Commerce Implementation Playbook*.

## リクエストを作成できるのは誰ですか？

Adobeは、以下のグループ内の個人を含む、内部および外部の関係者からの要求を受け入れます。

- Adobeパートナー
- AdobeCTAG（顧客技術諮問グループ）、カスタマーサポート、顧客成功、エンジニアリングチーム

## リクエストの作成方法

**内部の関係者** は、COMDOX プロジェクトで Jira の問題を開いてリクエストを送信できます。 **外部の関係者** は、 [GitHub の問題](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) をこのリポジトリに追加します。

次のタイプのリクエストを送信できます。

- 新しいコンテンツのアイデア
- 既に公開されているコンテンツの更新
- 関係者またはコミュニティから提供された新しいコンテンツの公開

## 全体的なプロセスは何ですか？


**Jira チケットまたはイシューの作成** — 内部の関係者が COMDOX プロジェクトに Jira チケットを作成します。 外部の関係者が GitHub の問題を提出します。 完全な詳細を Jira に含めるか、 [GitHub の問題](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) チームがコンテキストを理解し、リクエストを優先順位付けするのに役立ちます。

**Adobeプロジェクトチームがリクエストを評価し、優先順位を付けます** — チームはリクエストを定期的に監視し、優先度を判断し、実装プレイブックのベストプラクティスに含めるためにリクエストされた変更を評価します。 例えば、チームは、新しいベストプラクティストピックを作成する代わりに、リクエストするコンテンツをExperience LeagueまたはAdobe Developerサイト上の既存の製品ドキュメントに追加するように決定する場合があります。

リクエストで十分な情報が提供されない場合、チームはリクエスト元から追加情報をリクエストします。 要求者が 14 日以内に応答しなかった場合、チームはリクエストを閉じます。

**コンテンツを作成または更新** — コンテンツ作成作業は、 [Adobe Experience League Contributor Guide](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html). リクエストに応じて、新しいコンテンツの Markdown への変換、トピックの作成、既存のトピックの更新などを行うことができます。

**コンテンツのレビュー、承認および公開** — コンテンツは、トピックの作成中または次を使用して更新中にレビューおよび編集されます： [GitHub のプル要求](https://experienceleague.adobe.com/docs/contributor/contributor-guide/setup/git-fundamentals.html?lang=en#pull-requests). すべてのコンテンツは編集レビューを経る必要があります。 技術的なレビューはオプションで、内容に応じて異なります。 技術的なレビューが必要ない場合、プロセスは編集レビューのみで続行されます。 この処理では、コンテンツが承認されるまで何度か繰り返し処理がおこなわれます。

記事が承認されると、プルリクエストを実稼動ブランチにマージできます。 マージは作成者がおこなう必要があります。 トピックが結合された後、手動プロセスを使用してすぐに実稼動環境に公開できます。また、次回公開ジョブが実行されたときに自動的に公開することもできます。 公開ジョブは通常 2 時間ごとに実行されます。

**新しいコンテンツ通知**-Adobeが *最新情報* セクション [ベストプラクティスの概要](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html?lang=en) トピックを参照してください。 Adobeは、マーケティングや内部通信などの既存のチャネルを使用して、新しいベストプラクティスコンテンツも促進します。

## バックログおよびかんばんボード

重複を避けるために、作成され優先順位付けされたリクエストは、COMDOX プロジェクトの Jira バックログに表示され、 [GitHub Issues プロジェクト](https://github.com/orgs/AdobeDocs/projects/6/views/1). 内部の関係者は、必要と考えるか、関連すると考える投票要求を、Jira の投票システムに関与するよう奨励されます。 投票は、ベストプラクティスプロジェクトチームが、関係者が期待するコンテンツのタイプと価値を理解するのにも役立ちます。 優先順位付けとレビューが保留中の要求は、かんばんボードのアクティブなレーンに移動されるまで、バックログに表示されます。

かんばんボードには、内部ユーザーがアクセスして、作業中のコンテンツと進行状況を表示（または監視）できます。 アクティブなリクエストのみがこのボードに表示されます。
