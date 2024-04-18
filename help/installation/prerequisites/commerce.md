---
title: Adobe Commerce ソフトウェアの入手
description: Adobe Commerce ソフトウェアのダウンロード方法について説明します。
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Adobe Commerce ソフトウェアの入手

あなたは、私たちの e コマースソフトウェアに信頼を置く世界中の 240,000 の商人の中の 1 つです。 インストールを開始する際に役立つ情報を収集しました。

## ソフトウェアの入手方法

エキサイティングな新機能やリリースの可用性を確認し、それらをアドビで入手する方法を学びます [製品の可用性ページ](https://devdocs.magento.com/release/availability.html).

Adobe Commerceのインストールの概要については、次の表を参照してください。

<table>
    <tbody>
        <tr>
            <th>ユーザーのニーズ</th>
            <th>説明</th>
            <th>インストールとアップグレードの手順の概要</th>
            <th>「基本を学ぶ」リンク</th>
        </tr>
    <tr>
        <td><p>インテグレーター、パッケージャー</p></td>
        <td><p>インストールされているすべてのコンポーネントを完全に制御したい、アプリケーションサーバーにアクセスできる、非常に技術的な、他のコンポーネントとMagento Open Sourceを再パッケージ化する可能性があります。</p>
        </td>
        <td><ol><li>コンポーザーを作成します <em>プロジェクト</em> 使用するコンポーネントのリストが含まれます。</li>
            <li>Composer を使用してパッケージの依存関係を更新します。を使用します。 <code>composer create-project</code> Composer メタパッケージを取得します。</li>
            <li>を使用してアプリケーションをインストールします <a href="../advanced.md">コマンドライン</a>.</li>
        <li>を使用してアプリケーションおよび拡張機能をアップグレードします。  <a href="../../upgrade/implementation/perform-upgrade.md">コマンドライン</a>.</li></ol></td>
        <td><p><a href="../composer.md">メタパッケージを入手する</a></p></td>
    </tr>
    <tr>
        <td><p>貢献する開発者</p></td>
        <td><p>Magento Open Sourceのコードベース、ファイルのバグ、アプリケーションのカスタマイズに役立ちます。 高度な技術を持ち、独自の開発サーバーを持ち、Composer と GitHub を理解しています。</p>
            <p>あなた <em>できません</em> 実稼動環境でアプリケーションを使用します。</p>
      <p>を使用してアップグレードする必要があります <a href="../../upgrade/developer/git-installs.md">Composer コマンドと Git コマンド</a>.</p></td>
        <td><ol><li>GitHub リポジトリを複製します。</li>
            <li>Composer を使用してパッケージの依存関係を更新します。</li>
            <li>を使用してアプリケーションをインストールします。 <a href="../advanced.md">コマンドライン</a>.</li>
            <li>を使用してアプリケーションをアップグレードします。 <a href="../../upgrade/developer/git-installs.md">Composer コマンドと Git コマンド</a>.</li>
            <li>以下のコードをカスタマイズします <code>app/code</code> ディレクトリ。</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">GitHub リポジトリのクローン</a></p></td>
    </tr>
    </tbody>
</table>

## 役に立つ情報

ページの左側にあるリンクを使用して、インストールの各部分のトピックを移動します。

## 必要なサーバー権限

UNIX システムでは次が必要 `root` web サーバー、PHP などのソフトウェアをインストールおよび設定する権限。 このソフトウェアをインストールする必要がある場合は、次のことを確認してください `root` アクセス。

実行 *ではない* web サーバーの docroot にアプリケーションをとしてインストールします `root` ユーザー：web サーバーがこれらのファイルを操作できない可能性があるためです。

必要です `root` を作成するための権限 [ファイルシステム所有者](file-system/overview.md) その所有者を web サーバーのグループに追加します。 ファイルシステムの所有者を使用して実行します `bin/magento` コマンドをコマンドラインから実行し、cron ジョブを設定して、タスクのスケジュールを設定します。
