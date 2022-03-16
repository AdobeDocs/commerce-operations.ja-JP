---
title: SLA(Service Level Agreements)
description: Adobe Commerceの実装をサポートするための SLA(Service Level Agreement) の使用方法について説明します。
exl-id: 5da42dfa-e165-4142-a863-6f3ce7689478
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 1%

---

# SLA(Service Level Agreement)

SLA(Service Level Agreement) は、お客様がサービス・プロバイダから期待するサービス・レベルを定義し、そのサービスを測定するシンプルな指標と、合意に達しない場合の是正や罰則を定義します。

様々なタイプのインシデント重大に対する SLA は、契約、維持、測定が可能です。 また、応答タイプは、お客様が必要とするサービスのレベルに基づいて、複数の標準（ゴールド、プラチナ）を持つことができます。

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
    <td>サービスが停止しているか、使用できません</td>
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
    <td>エンドユーザーベース全体でサービスを使用できない</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>P2</td>
    <td>大きな影響</td>
    <td>サービスが著しく損なわれた</td>
    <td>2 時間/ 12 時間</td>
    <td>2 時間/ 8 時間</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>サービスのパフォーマンスが低下しています</td>
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
    <td>サービスが部分的に障害を持つ</td>
    <td>8 時間/ 16 時間</td>
    <td>8 時間/ 12 時間</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>エラーメッセージが生成され、エンドユーザーに目立つ影響がない</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Customer Launch で使用される機能に関する質問</td>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>

## 対象オプション

コミット済み SLA の対象オプションは、提供するサービスのタイプによって異なります。 通常、ゴールドとプラチナのサポートサービスの範囲は次のようになります。

![SLA 範囲オプションを示す解説図](../../assets/playbooks/sla-coverage-options.svg)
