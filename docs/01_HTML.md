### 基本

- 文字系
  - [強調](#強調)
  - [上付き・下付き](#上付き下付き)
  - [コード（`<code>`）](#コード)

- 文書構造
  - [折りたたみ](#折りたたみ)

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
