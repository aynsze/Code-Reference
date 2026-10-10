### 基本

- 文字系
  - [強調](#強調)
  - [上付き・下付き](#上付き下付き)
  - [コード（`<code>`）](#コード)

- 文書構造
  - [折りたたみ](#折りたたみ)

- フォーム（`<input>`）
  - [ラベルと入力欄を関連づける](#ラベルと入力欄を関連づける)
  - [種類（`type`）](#種類type)
  - [属性](#属性)

# 基本

## 文字系

- ### 強調
  - `<strong>`

    ```html
    テキストを<strong>強調</strong>する
    ```

    <!-- demo -->

  - `<b>`

    ```html
    テキストを<b>強調</b>する
    ```

    <!-- demo -->
    ---

- ### 上付き、下付き
  - 上付き：`<sup>`

    ```html
    10の2乗は、10<sup>2</sup>
    ```

    <!-- demo -->

  - 下付き：`<sub>`

    ```html
    水の分子記号は、H<sub>2</sub>O
    ```

    <!-- demo -->
    ---

- ### コード
  `<code>`
  ```html
  JavaScript で変数 num に値 5 を代入するには、<code>num = 5;</code>と記述する
  ```
  <!-- demo -->



## 文書構造

- ### 折りたたみ
  - 基本
    ```html
    <details>
      <summary>タイトル</summary>
      中身
    </details>
    ```
    <!-- demo -->

  - デフォルトを開いた状態にする（属性：`open`）
    ```html
    <details open>
      <summary>タイトル</summary>
      中身
    </details>
    ```
    <!-- demo -->

  - 複数あるうち、開くのは一つのみにする（属性：`name`）
    ```html
    <details name="questions">
      <summary>タイトル➀</summary>
      中身➀
    </details>
    <details name="questions">
      <summary>タイトル➁</summary>
      中身➁
    </details>
    ```
    <!-- demo -->

## フォーム（`<input>`）
`<input type="種類" 属性>`
- ### ラベルと入力欄を関連づける
  例：「名前」をクリックすると、入力欄にフォーカスが移動する
  - `<label>`タグで囲む方法
  
    前に表示
    ```html
    <label>名前
      <input type="text">
    </label>
    ```
    <!-- demo -->

    後に表示
    ```html
    <label>
      <input type="text">名前
    </label>
    ```
    <!-- demo -->

  - `for` 属性と `id` 属性を使用する方法：ラベルと入力欄を離れた位置に記述したい場合にも使える

    `input` の `id` 属性と、`label` の `for` 属性に同じ値を指定する
    ```html
    <label for="name">名前</label>
    <input type="text" id="name">
    ```
    <!-- demo -->

- ### 種類（`type`）
  | 種類           | 説明                     |
  | -------------- | ------------------------ |
  | フィールド系   |                          |
  | `text`         | テキストを入力           |
  | `password`     | パスワードを入力         |
  | `file`         | ファイルを入力           |
  | `search`       | 検索値を入力             |
  | `hidden`       | 表示しない               |
  | `tel`          | 電話番号を入力           |
  | `url`          | URLを入力                |
  | `email`        | メールアドレスを入力     |
  | `date`         | 日付を入力               |
  | `time`         | 時刻を入力               |
  | `number`       | 数値を入力               |
  | `range`        | 範囲を指定               |
  | `color`        | 色を入力                 |
  | `month`        | 年と月を入力             |
  | `week`         | 年と週を入力             |
  | 選択・ボタン系 |                          |
  | `button`       | 汎用                     |
  | `checkbox`     | チェックボックス         |
  | `radio`        | ラジオボタン             |
  | `submit`       | フォームの送信           |
  | `reset`        | 初期状態に戻す           |
  | `image`        | 画像を使ったフォーム送信 |

  <!-- demo
  ```html
  <table>
      <tr><td>テキスト</td><td><input type="text"></td></tr>
      <tr><td>パスワード</td><td><input type="password"></td></tr>
      <tr><td>ファイル</td><td><input type="file"></td></tr>
      <tr><td>検索</td><td><input type="search"></td></tr>
      <tr><td>隠し</td><td><input type="hidden"></td></tr>
      <tr><td>電話番号</td><td><input type="tel"></td></tr>
      <tr><td>URL</td><td><input type="url"></td></tr>
      <tr><td>メールアドレス</td><td><input type="email"></td></tr>
      <tr><td>日付</td><td><input type="date"></td></tr>
      <tr><td>時刻</td><td><input type="time"></td></tr>
      <tr><td>数値</td><td><input type="number"></td></tr>
      <tr><td>範囲</td><td><input type="range"></td></tr>
      <tr><td>色</td><td><input type="color"></td></tr>
      <tr><td>年月</td><td><input type="month"></td></tr>
      <tr><td>年・週</td><td><input type="week"></td></tr>
      <tr><td>ボタン</td><td><input type="button"></td></tr>
      <tr><td>チェックボックス</td><td><input type="checkbox"></td></tr>
      <tr><td>ラジオボタン</td><td><input type="radio"></td></tr>
      <tr><td>送信</td><td><input type="submit"></td></tr>
      <tr><td>リセット</td><td><input type="reset"></td></tr>
      <tr><td>画像ボタン</td><td><input type="image"></td></tr>
  </table>
  ```
  -->
---

- ### 属性
  | 属性                 | 説明                                                         |
  | -------------------- | ------------------------------------------------------------ |
  | 基本                 | 対象部品：すべて                                             |
  | `type="種類名"`      | 種類を指定                                                   |
  | `name="名前"`        | 名前を指定                                                   |
  | `value="値"`         | 初期値を指定                                                 |
  | 共通                 |                                                              |
  | `form="id名"`        | フォーム要素のidを指定                                       |
  | `disabled`           | 無効化（操作できない状態）                                   |
  | `required`           | 必須                                                         |
  | テキスト関連         | 対象部品：text, password, search, tel, url, email            |
  | `size=数値`          | 入力フィールドの横幅（文字数の目安）を指定                   |
  | `maxlength=数値`     | 最大入力文字数を指定                                         |
  | `minlength=数値`     | 最小入力文字数を指定                                         |
  | `placeholder="値"`   | プレースホルダとして入力欄に薄文字などで表示する文字列を指定 |
  | `readonly`           | 読み取り専用（編集を禁止）                                   |
  | 数値・日付関連       | 対象部品：date, time, number, range                          |
  | `max=数値`           | 最大値を指定                                                 |
  | `min=数値`           | 最小値を指定                                                 |
  | `step=数値`          | 数値・時刻を増減させる際のステップ値を指定                   |
  | チェック・ラジオ関連 | 対象部品：checkbox, radio                                    |
  | `checked`            | チェックした状態にする                                       |
  | 画像ボタン関連       | 対象部品：image                                              |
  | `src="url"`          | 表示する画像ファイルの URL を指定                            |
  | `alt="文字列"`       | 画像の代わりに表示する代替テキストを指定                     |
  | `height=数値`        | 画像ボタンの高さを指定                                       |
  | `width=数値`         | 画像ボタンの横幅を指定                                       |
  | ファイル関連         |                                                              |
  | `multiple`           | 複数選択を可能にする                                         |
