---
source-git-commit: 8013e6339d42108dbefbbafa5db7f9ffc5288c4f
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---
# ベストプラクティス：コンテンツ作成ワークフロー

https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html?lang=jaこのドキュメントでは、*[3&rbrace;Adobe Commerce実装プレイブック &rbrace; の ] ベストプラクティス &rbrace;* コンテンツに対する変更または追加をリクエストするユーザーワークフローについて説明 *ます。*

## リクエストを作成できるユーザー

Adobeは、次のグループに属する個人を含む（ただし、これに限定されない）内部および外部の関係者からのリクエストを受け入れます。

- Adobeパートナー
- AdobeCTAG （カスタマーテクニカルアドバイザリグループ）、カスタマーサポート、カスタマーサクセス、エンジニアリングチーム

## リクエストを作成するにはどうすればよいですか？

**内部の関係者** は、COMDOX プロジェクトで Jira の問題を開いてリクエストを送信できます。 **外部の関係者** は、このリポジトリで [GitHub イシュー ](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) を開くことで、リクエストを送信できます。

次のタイプのリクエストを送信できます。

- 新しいコンテンツのアイデア
- 既に公開済みのコンテンツに対する更新
- 関係者またはコミュニティから提供されたPublishの新しいコンテンツ

## 全体的なプロセスはどのようなものですか？


**Jira チケットまたはイシューの作成** – 内部の関係者が、COMDOX プロジェクトで Jira チケットを作成します。 外部の関係者が GitHub イシューを送信します。 Jira または [GitHub の問題 ](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) の完全な詳細を含めることで、チームがコンテキストを理解し、リクエストの優先順位を付けるのに役立ちます。

**Adobeプロジェクトチームは、リクエストを評価し、優先順位を付けます**。チームはリクエストを定期的にモニタリングし、優先度を判断したり、リクエストされた変更内容を評価して実装プレイブックのベストプラクティスに含めたりします。 例えば、新しいベストプラクティストピックを作成する代わりに、要求されたコンテンツをExperience LeagueまたはAdobe Developer サイト上の既存の製品ドキュメントに追加すべきだと判断する場合があります。

リクエストに十分な情報が提供されていない場合、チームはリクエスターに追加情報をリクエストします。 要求者が 14 日以内に応答しない場合、チームは要求をクローズします。

**コンテンツの作成または更新** - [Adobe Experience League投稿者ガイドに記載されているプロセスに従って、コンテンツの作成作業が完了します ](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html?lang=ja)。 リクエストに応じて、新しいコンテンツを Markdown に変換したり、トピックを作成したり、既存のトピックを更新したりすることが可能です。

**コンテンツのレビュー、承認および公開** - トピックの作成または更新中に、コンテンツがレビューおよび編集されます。[GitHub プルリクエスト ](https://experienceleague.adobe.com/docs/contributor/contributor-guide/setup/git-fundamentals.html?lang=ja#pull-requests)。 すべてのコンテンツは、エディトリアルレビューを経る必要があります。 テクニカルレビューはオプションであり、コンテンツによって異なります。 技術的な確認が必要ない場合は、編集上の確認のみでプロセスが続行されます。 このプロセスは、コンテンツが承認されるまで数回の繰り返しになります。

記事が承認されたら、プルリクエストを実稼動ブランチに結合できます。 結合は作成者が行う必要があります。 トピックを統合したら、手動のプロセスを使用してすぐに実稼動環境に公開することも、次に公開ジョブを実行するときに自動的に公開することもできます。 公開ジョブは通常、2 時間ごとに実行されます。

**新しいコンテンツ通知**-Adobeでは、*ベストプラクティスの概要* トピックの「新機能 [&#128279;](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html?lang=ja) の節が提供され、最近公開または更新されたトピックに関する情報を常にユーザーに提供できます。 また、Adobeは、マーケティングや社内コミュニケーションなどの既存のチャネルを使用して、新しいベストプラクティスコンテンツを促進します。

## バックログとかんばんボード

重複を避けるために、作成され、優先順位が付けられたリクエストは、COMDOX プロジェクトと [GitHub Issues プロジェクト ](https://github.com/orgs/AdobeDocs/projects/6/views/1) の Jira バックログに表示されます。 内部の関係者は、Jira の投票システムに参加して、必要または関連性があると考えるリクエストに投票することをお勧めします。 また、投票は、ベストプラクティスプロジェクトチームが、関係者が期待するコンテンツのタイプと価値を理解するのにも役立ちます。 優先順位付けとレビューが保留されているリクエストは、かんばんボードのアクティブなレーンに移動されるまでバックログに表示されます。

内部ユーザーは、かんばんボードにアクセスして、作業中のコンテンツや進行状況を表示（または監視）できます。 このボードには、アクティブなリクエストのみが表示されます。
