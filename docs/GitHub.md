- [Web上からアップロード](#web上からアップロード)
- [Pagesの有効化](#pagesの有効化)
- [画像が表示されない場合](#画像が表示されない場合)

##

- ### Web上からアップロード
  フォルダも作成したい場合、URLを以下にする
  ```text
  https://github.com/<ユーザー名>/<リポジトリ名>/upload/main/<フォルダ名>
  ```
  ---

- ### Pagesの有効化
  1. Settings → Pages
  2. Build and deployment → `Source`
  3. `Deploy from a branch` を選ぶ
  4. `main` / `root` に設定
  5. Actionsで `pages build and deployment` を実行していることを確認

  - docsフォルダ内をPagesにしたい場合  
    - ➃で `main` / `docs` に設定  
    - docsにしても、urlに `docs/` は付かない
  ---

- ### 画像が表示されない場合
  `user-attachments` にすると画像が表示されないことがあるため、以下にする
  1. 公開リポジトリに画像ファイルを作成
  2. URLを以下にする
      ```md
      ![代替テキスト](https://raw.githubusercontent.com/<ユーザー名>/<画像を保存しているリポジトリ名>/main/image.png)
      ```
  ---

