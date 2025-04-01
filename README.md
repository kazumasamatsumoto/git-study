# git-study

# Git 入門ガイド：PC 操作に不慣れな新人社員向け

## はじめに：Git とは何か？

Git は「バージョン管理システム」と呼ばれるソフトウェアで、プログラムやドキュメントの変更履歴を記録し、管理するためのツールです。これを使うと：

- ファイルの変更履歴を時系列で確認できる
- 以前のバージョンに戻すことができる
- 複数の人が同時に同じプロジェクトで作業できる
- 誰がいつどのような変更をしたのか、記録される

スマホで写真を撮影するとき、写真がスマホに保存されるように、Git は変更を記録・保存するシステムだと考えてください。

## コマンドとは何か？

コマンドとは、コンピュータに対して「これをしてください」と指示するための命令文です。

- スマホで例えると：アプリのボタンを押す操作に相当します
- Git では「コマンドライン」と呼ばれる、文字を入力する画面からコマンドを入力します

## コマンドラインインターフェース（CLI）とは？

CLI とは「Command Line Interface（コマンドライン・インターフェース）」の略で、マウスではなく、キーボードで文字を打ち込んでコンピュータを操作する方法です。

- スマホで例えると：マウスやタッチ操作ではなく、文字メッセージを送るようにコンピュータと会話する方法です
- Windows では「コマンドプロンプト」や「PowerShell」、Mac では「ターミナル」と呼ばれるアプリケーションを使います

## Git の始め方

### 1. Git のインストール

Git を使うには、まず PC にインストールする必要があります。

- Windows の場合：[Git for Windows](https://gitforwindows.org/)からダウンロードしてインストール
- Mac の場合：ターミナルを開き、`git --version`と入力。インストールされていなければ、インストールするよう促されます

### 2. 自分の情報を設定する

Git を初めて使うときは、自分の名前とメールアドレスを設定します。これは、あなたが行った変更を識別するためのものです。

```
git config --global user.name "あなたの名前"
git config --global user.email "あなたのメールアドレス"
```

## 基本的な Git コマンド（実践編）

### リポジトリを作成する - `git init`

リポジトリ（保管庫）とは、プロジェクトの全ファイルとその変更履歴を保存する場所です。

1. フォルダを作成し、そのフォルダに移動します
2. 次のコマンドを入力します：
   ```
   git init
   ```
3. これで、そのフォルダが Git リポジトリになりました

### 変更を記録する準備 - `git add`

ファイルを変更した後、その変更を記録するには：

1. 変更したファイルを Git の「ステージングエリア」に追加します：
   ```
   git add ファイル名
   ```
2. すべてのファイルを追加したい場合：
   ```
   git add .
   ```

### 変更を記録（確定）する - `git commit`

ステージングエリアに追加した変更を実際に記録します：

```
git commit -m "変更内容の説明"
```

この「変更内容の説明」は、後で振り返ったときに変更内容を思い出せるよう、わかりやすい説明を書きましょう。

### 変更履歴を確認する - `git log`

これまでの変更履歴を見るには：

```
git log
```

各変更（コミット）について、誰がいつ何を変更したかが表示されます。

## リモートリポジトリを使ったチーム作業（GitHub 編）

### リモートリポジトリとは？

リモートリポジトリは、インターネット上に保存される Git リポジトリです。これにより：

- チームメンバーと共同作業ができる
- 自分の作業を複数のコンピュータで同期できる
- コードのバックアップになる

GitHub は、リモートリポジトリを提供する最も有名なサービスです。

### リモートリポジトリからコピーを取得する - `git clone`

GitHub などにあるプロジェクトのコピーを自分の PC に取得するには：

```
git clone リポジトリのURL
```

### 自分の変更をリモートリポジトリに送信する - `git push`

自分が行った変更を GitHub などのリモートリポジトリに送信するには：

```
git push origin main
```

### リモートリポジトリの最新の状態を取得する - `git pull`

チームメンバーの変更を取り込むには：

```
git pull origin main
```

## よくある問題と解決方法

### ファイルの競合（コンフリクト）

同じファイルの同じ部分を複数の人が変更すると、競合が発生することがあります。その場合：

1. `git pull`を実行すると競合が表示されます
2. 該当するファイルを開き、競合している部分を修正します
3. 修正後、`git add`と`git commit`を実行して解決します

### 変更を取り消したい場合

- コミット前の変更を取り消す：
  ```
  git checkout -- ファイル名
  ```
- 直前のコミットを取り消す：
  ```
  git reset --soft HEAD~1
  ```

## 実践的な使い方：シナリオ例

### シナリオ 1：新しいプロジェクトを始める

1. フォルダを作成：`mkdir プロジェクト名`
2. フォルダに移動：`cd プロジェクト名`
3. Git リポジトリを初期化：`git init`
4. ファイルを作成・編集
5. 変更を追加：`git add .`
6. 変更を記録：`git commit -m "最初のコミット"`

### シナリオ 2：チームプロジェクトに参加する

1. プロジェクトをコピー：`git clone リポジトリのURL`
2. プロジェクトフォルダに移動：`cd プロジェクト名`
3. 最新の状態を取得：`git pull origin main`
4. ファイルを編集
5. 変更を追加：`git add .`
6. 変更を記録：`git commit -m "機能Aを追加"`
7. 変更を送信：`git push origin main`

## 発展的な Git コマンド

基本コマンドに慣れてきたら、次のようなコマンドも覚えておくと便利です。

### ブランチを使った開発 - `git branch`, `git checkout`

ブランチ（branch）とは、メインの開発ラインから分岐して、独立して作業できる環境のことです。

- 新しいブランチを作成する：

  ```
  git branch ブランチ名
  ```

- ブランチを切り替える：

  ```
  git checkout ブランチ名
  ```

- ブランチを作成して同時に切り替える（よく使われます）：

  ```
  git checkout -b ブランチ名
  ```

- 現在のブランチを確認する：
  ```
  git branch
  ```

### ブランチの統合 - `git merge`

別のブランチでの変更を、現在のブランチに統合します：

```
git merge 統合したいブランチ名
```

例えば、feature ブランチの変更を main ブランチに統合する場合：

1. `git checkout main` で main ブランチに切り替え
2. `git merge feature` で feature ブランチの変更を統合

### 変更の一時保存 - `git stash`

作業の途中で別の作業に切り替えたい時、現在の変更を一時的に保存します：

- 変更を一時保存する：

  ```
  git stash
  ```

- 保存した変更を戻す：

  ```
  git stash pop
  ```

- 保存した変更の一覧を見る：
  ```
  git stash list
  ```

### リモートリポジトリの情報を確認・更新する - `git remote`

- リモートリポジトリの一覧を表示：

  ```
  git remote -v
  ```

- リモートリポジトリを追加：
  ```
  git remote add 名前 リポジトリのURL
  ```

### 特定のファイルやフォルダの状態を確認する - `git diff`

ファイルがどのように変更されたかを確認します：

```
git diff ファイル名
```

### コミット履歴を整理する - `git rebase`

複数のコミットをきれいに整理したい場合に使います（上級者向け）：

```
git rebase -i HEAD~3  # 直近3つのコミットを整理
```

### タグをつける - `git tag`

特定のコミットに目印（タグ）をつけます。リリースバージョンなどを管理するのに便利です：

```
git tag -a v1.0 -m "バージョン1.0"
```

### 変更を取り消す他の方法

- コミットメッセージを修正する：

  ```
  git commit --amend
  ```

- 特定のコミットを取り消す新しいコミットを作成：
  ```
  git revert コミットID
  ```

## 実践的なワークフロー例

### GitFlow ワークフロー

大きなプロジェクトでよく使われる開発の流れです：

1. メインブランチ（`main`）から開発ブランチ（`develop`）を作成
2. 機能開発時は `develop` から機能ブランチ（`feature/機能名`）を作成
3. 機能完成後、`develop` にマージ
4. リリース準備時、`develop` からリリースブランチ（`release/バージョン`）を作成
5. リリース後、`main` と `develop` にマージ

コマンド例：

```
git checkout -b feature/login  # 機能ブランチを作成
# 作業後...
git add .
git commit -m "ログイン機能を実装"
git checkout develop
git merge feature/login  # developにマージ
```

### GitHub Flow

シンプルなワークフロー：

1. `main` ブランチからトピックブランチを作成
2. 変更をコミット
3. GitHub 上でプルリクエストを作成
4. レビュー後、`main` にマージ

コマンド例：

```
git checkout -b fix-bug-123  # バグ修正用ブランチを作成
# 作業後...
git add .
git commit -m "バグ#123を修正"
git push origin fix-bug-123  # GitHubにプッシュ
# その後GitHubでプルリクエストを作成
```

## おわりに

Git の基本的なコマンドと発展的なコマンドを紹介しました。最初は複雑に感じるかもしれませんが、実際に使ってみることで徐々に慣れていきます。何か問題があれば、先輩や同僚に質問してみましょう。また、インターネットには Git に関する多くの学習リソースがあります。

覚えておきたい基本コマンド：

- `git init`：新しいリポジトリを作成
- `git add`：変更を記録する準備
- `git commit`：変更を記録（確定）
- `git push`：リモートリポジトリに変更を送信
- `git pull`：リモートリポジトリから変更を取得
- `git clone`：リモートリポジトリのコピーを取得
- `git status`：現在の状態を確認
- `git log`：変更履歴を確認

発展的なコマンド：

- `git branch`：ブランチの一覧表示・作成
- `git checkout`：ブランチの切り替え
- `git merge`：ブランチの統合
- `git stash`：作業の一時保存
- `git diff`：変更内容の確認
- `git rebase`：コミット履歴の整理
- `git tag`：タグ付け

# Git 雑学：知っておくと便利な追加コマンド集

## 1. Git ヘルプコマンド

```
git help <コマンド名>
```

困ったときは、このコマンドでヘルプを表示できます。例えば、`git help commit`と入力すると、commit コマンドの詳細な説明が表示されます。スマホでいえば、アプリのヘルプ画面を表示するようなものです。

## 2. サーバー管理者向けコマンド

### git gc（ガベージコレクション）

```
git gc
```

Git リポジトリの「掃除屋さん」です。不要なファイルを削除してリポジトリを最適化します。スマホのストレージ容量を確保するために不要なファイルを削除するアプリのようなものです。通常は自動的に実行されますが、手動で実行することもできます。

### git fsck

```
git fsck
```

リポジトリの「健康診断」を行います。問題や不整合がないか確認します。スマホのウイルススキャンのようなものです。

### git reflog

```
git reflog
```

「タイムマシン」のようなコマンドです。ブランチの移動履歴を記録しているので、誤って削除したコミットを復活させるときに使えます。スマホでいえば、削除した写真を「ゴミ箱」から復元するようなものです。

### git filter-branch

```
git filter-branch
```

リポジトリの歴史を大規模に書き換えることができる「タイムトラベル装置」です。例えば、全てのコミットから特定のファイルを削除したい場合などに使います。上級者向けのコマンドであり、使用には注意が必要です。

## 3. 高度な差分と検査コマンド

### git difftool

```
git difftool
```

変更の差分を外部ツールで表示します。より視覚的に差分を確認したい場合に便利です。スマホでいえば、写真の編集前と編集後を比較するアプリのようなものです。

### git blame

```
git blame <ファイル名>
```

各行が誰によっていつ変更されたかを表示します。「犯人探し」ではなく、特定のコードについて詳しい人を見つけるのに役立ちます。スマホで例えると、グループチャットで誰がどのメッセージを送ったかを確認するようなものです。

### git grep

```
git grep "検索文字列"
```

リポジトリ内のファイルから特定の文字列を検索します。スマホの「設定」アプリ内の検索機能のようなものです。

### git shortlog

```
git shortlog
```

コミット履歴を作者ごとにまとめて表示します。「誰が何件のコミットをしたか」が一目でわかるので、チームの活動報告を作るときに便利です。

### git describe

```
git describe
```

最も近いタグからの距離を含めた名前を生成します。ビルド番号の生成などに使用されます。

## 4. パッチ関連のコマンド

### git cherry-pick

```
git cherry-pick <コミットID>
```

特定のコミットの変更だけを現在のブランチに適用します。「いいとこどり」ができるコマンドです。スマホでいえば、友達の写真アルバムから特定の 1 枚だけをもらうようなものです。

### git revert

```
git revert <コミットID>
```

特定のコミットの変更を打ち消す新しいコミットを作成します。「取り消しボタン」のようなものですが、履歴は残ります。

### git apply

```
git apply <パッチファイル>
```

パッチファイルを適用します。メールで送られてきたパッチを適用するときなどに使います。

## 5. 外部システム連携コマンド

### git svn

```
git svn
```

Subversion というほかのバージョン管理システムと連携するためのコマンドです。古いシステムと新しいシステムの「通訳」のような役割を果たします。

### git fast-import

```
git fast-import
```

他の形式のデータを Git リポジトリにインポートするためのコマンドです。他のシステムから Git に移行するときの「引っ越し業者」のような役割です。

## 6. メール関連のコマンド

Git は Linux カーネルなど多くのオープンソースプロジェクトでメールベースの開発が行われていることから、メール関連の機能が充実しています。

### git format-patch

```
git format-patch <範囲>
```

コミットをメールで送れる形式（パッチ）に変換します。

### git send-email

```
git send-email <パッチファイル>
```

作成したパッチをメールで直接送信します。

### git request-pull

```
git request-pull <開始点> <URL> [<終了点>]
```

変更を取り込んでほしいというリクエストメッセージを生成します。「プルリクエスト」の元祖とも言えるコマンドです。

## 7. 底レベル（Plumbing）コマンド

Git は内部で多くの小さなコマンドを組み合わせて動作しています。これらの底レベルコマンドを直接使うことも可能です。

### git ls-remote

```
git ls-remote <リポジトリ>
```

リモートリポジトリの参照（ブランチやタグなど）を一覧表示します。

### git ls-files

```
git ls-files
```

ステージングエリア内のファイル一覧を表示します。

### git rev-parse

```
git rev-parse <参照名>
```

参照名（ブランチ名やタグ名など）をコミット ID に変換します。

## まとめ

これらのコマンドは、日常的には使わないかもしれませんが、特定の状況では非常に便利なツールです。Git の深い世界を探索する旅の参考になれば幸いです。
