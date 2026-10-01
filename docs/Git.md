### 設定

- [ダウンロード方法](#ダウンロード方法)
- [GitHub CLIとの連携](#github-cliとの連携)
- [名前・メールアドレスの設定](#名前メールアドレスの設定)

### 基本

- [VSCodeのGit の "変更ステータス" を表す記号](#vscodeのgit-の-変更ステータス-を表す記号)

- ブランチ関連
  - [現在のブランチを確認（`git branch`）](#現在のブランチを確認)
  - [現在いるブランチの名前の変更](#現在いるブランチの名前の変更)
  - [ブランチを切り替える](#ブランチを切り替える)
  - [ブランチを作成](#ブランチを作成)

- sparse-checkout関連
  - [新たにsparse-checkoutを設定する場合](#新たにsparse-checkoutを設定する場合)
  - [すでにsparse-checkoutが設定されている場合](#すでにsparse-checkoutが設定されている場合)
  - [設定ファイルで直接編集](#設定ファイルで直接編集)
  - [設定ファイルを直接編集した場合](#設定ファイルを直接編集した場合)
  - [確認する方法](#確認する方法)


### 応用

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

## ブランチ関連

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

## sparse-checkout関連

- ### 新たにsparse-checkoutを設定する場合
  `.github`フォルダと`README.md`ファイルを除外する場合
  ```bash
  git sparse-checkout init --no-cone
  git sparse-checkout set "/*" "!/.github/" "!/README.md"
  ```
  `set`は、既存のルールに追加するのではなく、ルール全体を設定し直す

  ---

- ### すでにsparse-checkoutが設定されている場合
  現在の対象にファイルやフォルダを追加する場合
  ```bash
  git sparse-checkout add /src/main.js
  git sparse-checkout add /CHANGELOG.md
  ```
  `add`は、現在のsparse-checkoutのルールに対象を追加する

  ※ `set`とは異なり、現在のルールを置き換えない

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

- ### 設定ファイルを直接編集した場合
  編集した内容を作業フォルダに反映する必要がある
  ```bash
  git sparse-checkout reapply
  ```
  `reapply` は、現在のsparse-checkoutのルールを作業フォルダに再適用する。

  ---

- ### 現在のルールを確認
  ```bash
  git sparse-checkout list
  ```
