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

魅力的な新機能やリリースの提供状況を確認し、それらを入手する方法については、アドビの [ 製品提供ページ ](https://devdocs.magento.com/release/availability.html) を参照してください。

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
        <td><ol><li>使用するコンポーネントのリストを含む Composer <em> プロジェクト </em> を作成します。</li>
            <li>Composer を使用してパッケージの依存関係を更新します。<code>composer create-project</code> を使用して Composer メタパッケージを取得します。</li>
            <li><a href="../advanced.md"> コマンドライン </a> を使用してアプリケーションをインストールします。</li>
        <li><a href="../../upgrade/implementation/perform-upgrade.md"> コマンドライン </a> を使用してアプリケーションと拡張機能をアップグレードします。</li></ol></td>
        <td><p><a href="../composer.md">メタパッケージを入手する</a></p></td>
    </tr>
    <tr>
        <td><p>貢献する開発者</p></td>
        <td><p>Magento Open Sourceのコードベース、ファイルのバグ、アプリケーションのカスタマイズに役立ちます。 高度な技術を持ち、独自の開発サーバーを持ち、Composer と GitHub を理解しています。</p>
            <p>実稼動環境 <em> はアプリケーションを使用できません </em>。</p>
      <p><a href="../../upgrade/developer/git-installs.md">Composer コマンドと Git コマンド </a> を使用してアップグレードする必要があります。</p></td>
        <td><ol><li>GitHub リポジトリを複製します。</li>
            <li>Composer を使用してパッケージの依存関係を更新します。</li>
            <li><a href="../advanced.md"> コマンドライン </a> を使用してアプリケーションをインストールします。</li>
            <li><a href="../../upgrade/developer/git-installs.md">Composer および Git コマンド </a> を使用してアプリケーションをアップグレードします。</li>
            <li><code>app/code</code> ディレクトリの下のコードをカスタマイズします。</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">GitHub リポジトリのクローン</a></p></td>
    </tr>
    </tbody>
</table>

## 役に立つ情報

ページの左側にあるリンクを使用して、インストールの各部分のトピックを移動します。

## 必要なサーバー権限

UNIX システムでは、Web サーバーや PHP などのソフトウェアをインストールおよび設定するために `root` 権限が必要です。 このソフトウェアをインストールする必要がある場合は、アクセス権があ `root` ことを確認します。

Web サーバーがこれらのファイルを操作できない可能性があるので *web サーバーの docroot にアプリケーションを `root` ユーザーとしてインストールし* いでください。

[ ファイルシステム所有者 ](file-system/overview.md) を作成し、その所有者を web サーバーのグループに追加するには、`root` 権限が必要です。 ファイルシステムの所有者を使用して、コマンドラインから `bin/magento` コマンドを実行したり、タスクをスケジュールする cron ジョブを設定したりできます。
