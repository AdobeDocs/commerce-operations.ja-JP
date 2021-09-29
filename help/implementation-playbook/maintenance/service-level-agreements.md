---
title: SLA(Service Level Agreement)
description: SLA(Service Level Agreement) と、それらを使用してAdobe・コマースの実装をサポートする方法について説明します。
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 1%

---


# SLA(Service Level Agreement)

SLA(Service Level Agreement) は、サービス・プロバイダからのお客様が期待するサービス・レベルを定義し、そのサービスを測定するシンプルな指標と、合意に基づいたサービス・レベルを達成できない場合の是正や罰則を定義します。

様々なタイプのインシデントクリティカルに対する SLA は、契約、保守、測定が可能です。 また、お客様が必要とするサービスレベルに応じて、応答タイプに複数の標準（ゴールド、プラチナ）を設定することもできます。

次の表に、複数のサービスレベルを持つ一般的な SLA 指標の分類を示します。

<table>
<thead>
  <tr>
    <th>問題のタイプ</th>
    <th>影響</th>
    <th>例</th>
    <th colspan="2">サポート対象営業時間中の応答/復元時間</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td colspan="3"></td>
    <td>ゴールド</td>
    <td>プラチナ</td>
  </tr>
  <tr>
    <td>P1</td>
    <td>重大な影響</td>
    <td>サービスが停止したか、使用できない</td>
    <td>1 時間/4 時間</td>
    <td>1 時間/4 時間</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>サービスを利用できません</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>エンド・ユーザー・ベース全体でサービスを使用できない</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>P2</td>
    <td>大きな影響</td>
    <td>サービスが著しく損なわれる</td>
    <td>2 時間/12 時間</td>
    <td>2 時間/8 時間</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>サービスのパフォーマンスが低下</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>サービスは利用可能だが、重大なエラーメッセージが発生する</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>P3</td>
    <td>中程度の影響</td>
    <td>サービスが部分的に損なわれている</td>
    <td>8 時間/ 16 時間</td>
    <td>8 時間/ 12 時間</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>エラーメッセージが生成され、エンドユーザーに影響を及ぼさない</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>お客様向けリリースで使用される機能に関する質問</td>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>

## 有効範囲オプション

コミット済み SLA の対象オプションは、異なるタイプの提供によって異なります。 通常、ゴールドおよびプラチナのサポートサービスの範囲は次のようになります。

![SLA 適用範囲オプションを示す解説図](../../assets/playbooks/sla-coverage-options.svg)
