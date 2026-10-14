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
  JavaScript では、<code>num = 5;</code>と記述する
  ```
  <!-- demo -->



## 文書構造

- ### 折りたたみ
  `<details>`の中に`<summary>`
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
`<input type="種類" 属性>`：空要素なので、`</input>`は不要
- ### ラベルと入力欄を関連づける
  例：「名前」をクリックすると、入力欄にフォーカスが移動する
  - `<label>` タグで囲む方法
  
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
  | 種類           | 説明                     | 例                      |
  | -------------- | ------------------------ | ----------------------- |
  | 入力系   |                          |                         |
  | `text`         | テキスト           | <input type="text">     |
  | `password`     | パスワード         | <input type="password"> |
  | `file`         | ファイル           | <input type="file">     |
  | `search`       | 検索値             | <input type="search">   |
  | `hidden`       | 表示しない               | <input type="hidden">   |
  | `tel`          | 電話番号           | <input type="tel">      |
  | `url`          | URL                | <input type="url">      |
  | `email`        | メールアドレス     | <input type="email">    |
  | `date`         | 日付               | <input type="date">     |
  | `time`         | 時刻               | <input type="time">     |
  | `number`       | 数値               | <input type="number">   |
  | `color`        | 色                 | <input type="color">    |
  | `month`        | 年と月             | <input type="month">    |
  | `week`         | 年と週             | <input type="week">     |
  | 選択・ボタン系 |                          |                         |
  | `range`        | 範囲を指定               | <input type="range">    |
  | `button`       | 汎用                     | <input type="button">   |
  | `checkbox`     | チェックボックス         | <input type="checkbox"> |
  | `radio`        | ラジオボタン             | <input type="radio">    |
  | `submit`       | フォームの送信           | <input type="submit">   |
  | `reset`        | 初期状態に戻す           | <input type="reset">    |
  | `image`        | 画像を使ったフォーム送信 | <input type="image">    |

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
