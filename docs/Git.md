### 設定

- [ダウンロード方法](#ダウンロード方法)
- [GitHub CLIとの連携](#github-cliとの連携)
- [名前・メールアドレスの設定](#名前メールアドレスの設定)

### 基本

- [VSCodeのGit の "変更ステータス" を表す記号](#vscodeのgit-の-変更ステータス-を表す記号)

- ブランチ関連（`branch`）
  - [現在のブランチを確認](#現在のブランチを確認)
  - [現在いるブランチの名前の変更](#現在いるブランチの名前の変更)
  - [ブランチを切り替える](#ブランチを切り替える)
  - [ブランチを作成](#ブランチを作成)

- sparse-checkout関連（`sparse-checkout`）
  - [新たにsparse-checkoutを設定する場合](#新たにsparse-checkoutを設定する場合)
  - [すでにsparse-checkoutが設定されている場合（`add`）](#すでにsparse-checkoutが設定されている場合add)
  - [設定ファイルで直接編集](#設定ファイルで直接編集)
  - [設定ファイルを直接編集した場合（`reapply`）](#設定ファイルを直接編集した場合reapply)
  - [現在のルールを確認（`list`）](#現在のルールを確認list)

- タグ（`tag`）
  - [新規タグを作成](#新規タグを作成)
  - [既存タグを上書き](#既存タグを上書き)

- 他
  - [現在の状態を確認（`status`）](#現在の状態を確認status)
  - [変更内容を見る（`diff`）](#変更内容を見るdiff)
  - [コミット履歴だけを表示（`log`）](#コミット履歴だけを表示log)
  - [全履歴を表示（`reflog`）](#全履歴を表示reflog)

### 応用

- [リポジトリと紐づける方法](#リポジトリと紐づける方法)
- [前回と前々回のpushを元に戻すコミットメッセージも削除する方法](#前回と前々回のpushを元に戻すコミットメッセージも削除する方法)

---

## 設定

- ### ダウンロード方法
  1. 新規ウィンドウで `ターミナル` を開いて、以下を実行
      ```bash
      git --version
      ```
  2. ダウンロードされていなかったら、以下を実行して、インストールする
      ```bash
      winget install --id Git.Git -e --source winget
      ```
  3. インストールが完了したら、**VS Code自体を一度終了**して、再度起動する
  4. 新しいターミナルを開いて、➀を実行
  5. `git version 2.51.0.windows.1` のように表示されたらOK
  6. さらに、以下を実行する
      ```bash
      where.exe git
      ```
  7. `C:\Program Files\Git\cmd\git.exe` のような結果が出ればOK
  ---

- ### GitHub CLIとの連携
  1. Gitが認識されるようになったら、以下を実行
      ```bash
      gh auth setup-git
      ```
  2. そのあと、以下で確認
      ```bash
      gh auth status
      ```
  ---

- ### 名前・メールアドレスの設定
  1. ターミナルで、以下を実行（メールアドレスは、GitHubの `noreply` でもOK）
      ```bash
      git config --global user.name "あなたの名前"
      git config --global user.email "あなたのメールアドレス"
      ```
  2. そのあと、以下で確認
      ```bash
      git config --global user.name
      git config --global user.email
      ```
  ---

# 基本

### VSCodeのGit の "変更ステータス" を表す記号

| 記号                            | 意味                                                       |
| ------------------------------- | ---------------------------------------------------------- |
| `A` = Added（新規追加）         | `新しく作ったファイルがステージされている状態              |
| `U` = Unmerged（未解決の競合）  | マージコンフリクトが発生しているファイル                   |
| `M` = Modified（変更あり）      | 既存ファイルを編集した状態                                 |
| `D` = Deleted（削除）           | ファイルを削除した状態                                     |
| `R` = Renamed（名前変更）       | ファイル名を変更した状態                                   |
| `C` = Copied（コピー）          | Git が「これはコピーされたファイルだ」と判断したときに出る |
| `?` = Untracked（Git に未登録） | 新規ファイルだが、まだ `git add` していない状態            |

---

## ブランチ関連（`branch`）

- ### 現在のブランチを確認
  ```bash
  git branch
  ```
  　↓　結果：`main` branchにいるなら
  ```text
  * main
  ```
  と表示される

  ---

- ### 現在いるブランチの名前の変更
  `main` に変更
  ```bash
  git branch -M main
  ```
  ---

- ### ブランチを切り替える
  `main` ブランチに切り替える
  ```bash
  git switch main
  ```
  ---

- ### ブランチを作成
  `test` ブランチを作成して、そのブランチへ切り替える
  ```bash
  git switch -c test
  ```

## sparse-checkout関連（`sparse-checkout`）

- ### 新たにsparse-checkoutを設定する場合
  `.github` フォルダと `README.md` ファイルを除外する場合
  ```bash
  git sparse-checkout init --no-cone
  git sparse-checkout set "/*" "!/.github/" "!/README.md"
  ```
  `set` は、既存のルールに追加するのではなく、ルール全体を設定し直す

  ---

- ### すでにsparse-checkoutが設定されている場合（`add`）
  現在の対象にファイルやフォルダを追加する場合
  ```bash
  git sparse-checkout add /src/main.js
  git sparse-checkout add /CHANGELOG.md
  ```
  `add` は、現在のsparse-checkoutのルールに対象を追加する

  ※ `set` とは異なり、現在のルールを置き換えない

  ---

- ### 設定ファイルで直接編集
  設定は `.git/info/sparse-checkout` ファイルに保存されるため、直接編集することもできる
  ```text
  /*
  !/README.md
  ```
  　↓
  ```text
  /*
  !/README.md
  !/USAGE.md
  ```
  のように `!/USAGE.md` を追加することで、`USAGE.md` も除外できる。

  ---

- ### 設定ファイルを直接編集した場合（`reapply`）
  編集した内容を作業フォルダに反映する必要がある
  ```bash
  git sparse-checkout reapply
  ```
  `reapply` は、現在のsparse-checkoutのルールを作業フォルダに再適用する。

  ---

- ### 現在のルールを確認（`list`）
  ```bash
  git sparse-checkout list
  ```

## タグ（`tag`）

- ### 新規タグを作成
  ```bash
  git tag <タグ名>
  git push origin <タグ名>
  ```
  ---

- ### 既存タグを上書き
  ```bash
  git tag -d <タグ名>
  git push origin :refs/tags/<タグ名> # リモートタグ削除
  git tag <タグ名>                    # 新しいタグ作成
  git push origin <タグ名>            # リモートへ反映
  ```
  例：`0.0.0` を上書き
  ```bash
  git tag -d 0.0.0
  git push origin :refs/tags/0.0.0
  git tag 0.0.0
  git push origin 0.0.0
  ```

## コミットの削除

hard > soft > mixed

- ### ファイル自体も過去の状態に戻す（`--hard`）
  コミットを取り消して、ステージングも解除して、ファイルの変更も消したい（⚠ 一番大きく戻す）

  例：2つ前のコミットまで戻す
  ```bash
  git reset --hard HEAD~2
  ```

  例：特定のコミットまで戻す
  ```bash
  git reset --hard <戻したいコミットのハッシュ>
  ```
  ---

- ### ステージング状態に戻す（`--soft`）
  コミットだけ取り消したい

  例：2つ前のコミットまで戻す
  ```bash
  git reset --soft HEAD~2
  ```
  ---

- ### 非ステージング状態に戻す（`--mixed`）
  コミットを取り消して、ステージングも解除したい

  例：2つ前のコミットまで戻す
  ```bash
  git reset --mixed HEAD~2
  ```
  ---


## 他

- ### 現在の状態を確認（`status`）
  ```bash
  git status
  ```
  　↓　結果
  ```text
  Your branch is up to date with 'origin/main'.

  Changes not staged for commit:
  modified: main.js

  Untracked files:
  memo.md
  ```
  のように表示される

  ---


- ### 変更内容を見る（`diff`）
  何を変更したのかを確認できる
  ```bash
  git diff
  ```
  　↓　結果
  ```diff
  - const width = 100;
  + const width = 120;
  ```
  と表示される

  ---

- ### コミット履歴だけを表示（`log`）
  ```bash
  git log
  ```
  　↓　結果
  ```text
  commit 5c... (HEAD -> main, origin/main)
  Author: ...
  Date:   ...

    <コミットメッセージ>

  commit 55...
  ...
  ```
  と表示される

  ---

- ### 全履歴を表示（`reflog`）
  reset や checkout、merge、pull などの操作も記録
  ```bash
  git reflog
  ```
  　↓　結果
  ```text
  68f4352 HEAD@{3}: pull --tags ...
  ```
  と表示される


# 応用

## 前回と前々回のpushを元に戻す&コミットメッセージも削除する方法

1. 現在の履歴を確認
    ```bash
    git log --oneline -5
    ```
    　↓
    ```text
    c3c3c3c 前回のcommit
    b2b2b2b 前々回のcommit
    a1a1a1a その前のcommit
    ...
    ```
    この場合、`c3c3c3c` と `b2b2b2b` を元に戻して、`c3c3c3c` と `b2b2b2b` のコミットメッセージも削除する

2. 2つ前のコミットまで戻す（→ [コミットの削除](#コミットの削除)）
    ```bash
    git reset --mixed HEAD~2
    ```

3. GitHubも同じ状態にする
    ```bash
    git push --force-with-lease
    ```

これでGitHubも、`a1a1a1a` まで戻る

---

## リポジトリと紐づける方法

1. 紐づいているか確認
   ```bash
   git remote -v
   ```

2. 何も表示されていない場合、以下を実行
   ```bash
   git remote add origin https://github.com/aynsze/<リポジトリ名>.git
   ```
   以下で確認して
   ```bash
   git remote -v
   ```
   以下になったらOK
   ```text
   origin  https://github.com/aynsze/<リポジトリ名>.git (fetch)
   origin  https://github.com/aynsze/<リポジトリ名>.git (push)
   ```

3. ローカル `main` をリモート `main` に合わせて作り直す
   ```bash
   git fetch origin
   git reset --hard origin/main
   ```

4. 必要に応じて、[sparse-checkout](#新たにsparse-checkoutを設定する場合)を設定する

---