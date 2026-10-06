### 基本

- 疑似要素（`::`）
  - [範囲選択した文字のデザイン（`::selection`）](#範囲選択した文字のデザイン)
  - [箇条書きの記号部分（`::marker`）](#箇条書きの記号部分)
  - [最初の1行目（`::first-line`）](#最初の1行目)
  - [最初の1文字目（`::first-letter`）](#最初の1文字目)

- 疑似クラス（`:`）
  - [子要素](#子要素)
  - [ユーザー操作](#ユーザー操作)

- レイアウト
  - [余白](#余白)
  - [角丸（`border-radius`）](#角丸)

- 色
  - [文字色（`color`）](#文字色)
  - [アクセントカラー（`accent-color`）](#アクセントカラー)

- フォント
  - [太さ（`font-weight`）](#太さ)

- テキスト
  - [範囲選択（`user-select）](#範囲選択)

# 基本

## 疑似要素

- ### 範囲選択した文字のデザイン

  `::selection`

  ```css
  div::selection {
    background-color: blue;
  }
  ```

  <!-- demo

  ```html
  <div>文字を選択する</div>
  ```

  -->

- ### 箇条書きの記号部分

  `::marker`

  ```css
  li::marker {
    content: "✝  ";
  }
  ```

  <!-- demo

  ```html
  <ul>
    <li>項目1タイトル<br>項目1本文</li>
    <li>項目1タイトル<br>項目1本文</li>
  </ul>
  ```

  -->

- ### 最初の1行目

  `::first-line`

  ```css
  li::first-line {
    color: red;
  }
  ```

  <!-- demo

  ```html
  <ul>
    <li>項目1タイトル<br>項目1本文</li>
    <li>項目1タイトル<br>項目1本文</li>
  </ul>
  ```

  -->

- ### 最初の1文字目

  `::first-letter`

  ```css
  li::first-letter {
    color: red;
  }
  ```

  <!-- demo

  ```html
  <ul>
    <li>項目1タイトル<br>項目1本文</li>
    <li>項目1タイトル<br>項目1本文</li>
  </ul>
  ```

  -->


## 疑似クラス

- ### 子要素

  例：マッチする場合に赤色にしたい場合

  ```html
  <div class="parent">
    <div class="child">1</div>
    <div class="child">2</div>
    <div class="child">3</div>
    <div class="child">4</div>
    <div class="child">5</div>
    <div class="child">6</div>
  </div>
  ```

  - 最初の子要素（`:first-child`）

    その要素が、親要素から見て、最初の子要素である場合にマッチ

    ```css
    .child:first-child {
      background-color: red;
    }
    ```

    <!-- demo

    ```html
    <div class="parent">
      <div class="child">1</div>
      <div class="child">2</div>
      <div class="child">3</div>
      <div class="child">4</div>
      <div class="child">5</div>
      <div class="child">6</div>
    </div>
    ```

    ```css
    .parent {
      display: flex;
      gap: 6px;
    }

    .child {
      width: 30px;
      height: 30px;
      background-color: gray;
      text-align: center;
    }

    .child:first-child {
      background-color: red;
    }
    ```

    -->

  - 最後の子要素（`:last-child`）

    その要素が、親要素から見て、最後の子要素である場合にマッチ

    ```css
    .child:last-child {
      background-color: red;
    }
    ```

    <!-- demo

    ```html
    <div class="parent">
      <div class="child">1</div>
      <div class="child">2</div>
      <div class="child">3</div>
      <div class="child">4</div>
      <div class="child">5</div>
      <div class="child">6</div>
    </div>
    ```

    ```css
    .parent {
      display: flex;
      gap: 6px;
    }

    .child {
      width: 30px;
      height: 30px;
      background-color: gray;
      text-align: center;
    }

    .child:last-child {
      background-color: red;
    }
    ```

    -->

  - n番目の子要素（`:nth-child(n)`）

    その要素が、親要素から見て、n番目の子要素である場合にマッチ

    ```css
    .child:nth-child(3) {
      background-color: red;
    }
    ```

    <!-- demo

    ```html
    <div class="parent">
      <div class="child">1</div>
      <div class="child">2</div>
      <div class="child">3</div>
      <div class="child">4</div>
      <div class="child">5</div>
      <div class="child">6</div>
    </div>
    ```

    ```css
    .parent {
      display: flex;
      gap: 6px;
    }

    .child {
      width: 30px;
      height: 30px;
      background-color: gray;
      text-align: center;
    }

    .child:nth-child(3) {
      background-color: red;
    }
    ```

    -->

  - 奇数の子要素（`:nth-child(odd)`）

    その要素が、親要素から見て、奇数の子要素である場合にマッチ

    ```css
    .child:nth-child(odd) {
      background-color: red;
    }
    ```

    <!-- demo

    ```html
    <div class="parent">
      <div class="child">1</div>
      <div class="child">2</div>
      <div class="child">3</div>
      <div class="child">4</div>
      <div class="child">5</div>
      <div class="child">6</div>
    </div>
    ```

    ```css
    .parent {
      display: flex;
      gap: 6px;
    }

    .child {
      width: 30px;
      height: 30px;
      background-color: gray;
      text-align: center;
    }

    .child:nth-child(odd) {
      background-color: red;
    }
    ```

    -->

  - 偶数の子要素（`:nth-child(even)`）

    その要素が、親要素から見て、偶数の子要素である場合にマッチ

    ```css
    .child:nth-child(even) {
      background-color: red;
    }
    ```

    <!-- demo

    ```html
    <div class="parent">
      <div class="child">1</div>
      <div class="child">2</div>
      <div class="child">3</div>
      <div class="child">4</div>
      <div class="child">5</div>
      <div class="child">6</div>
    </div>
    ```

    ```css
    .parent {
      display: flex;
      gap: 6px;
    }

    .child {
      width: 30px;
      height: 30px;
      background-color: gray;
      text-align: center;
    }

    .child:nth-child(even) {
      background-color: red;
    }
    ```

    -->
    ---
    
- ### ユーザー操作

  - マウスを乗せているとき（`:hover`）
    ```css
    input:hover {
      background-color: red;
    }
    ```

    <!-- demo

    ```html
    <input type="text">
    ```

    ```css
    input:hover {
      background-color: red;
    }
    ```

    -->

  - フォーカス中（`:focus`）
    ```css
    input:focus {
      background-color: red;
    }
    ```

    <!-- demo

    ```html
    <input type="text">
    ```

    ```css
    input:focus {
      background-color: red;
    }
    ```

    -->

  - 押した瞬間（`:active`）
    ```css
    input:active {
      background-color: red;
    }
    ```

    <!-- demo

    ```html
    <input type="text">
    ```

    ```css
    input:active {
      background-color: red;
    }
    ```

    -->


## レイアウト

- ### 余白
  上から時計周り
  | 例                                         | 説明                              |
  | ------------------------------------------ | --------------------------------- |
  | `margin: 20px;`<!-- copy -->               | 全方向に 20px                     |
  | `margin: 20px 32px;`<!-- copy -->          | 上下に 20px、左右に 32px          |
  | `margin: 20px 32px 10px;`<!-- copy -->     | 上に 20px、左右に 32px、下に 10px |
  | `margin: 20px 32px 10px 5px;`<!-- copy --> | 上・右・下・左の順                |
  ---

- ### 角丸
  `border-radius`

  ```css
  border-radius: 15px;
  ```

  <!-- demo

  ```html
  <div></div>
  ```

  ```css
  div {
    width: 80px;
    height: 50px;
    background-color: red;

    border-radius: 15px
  }
  ```

  -->

  - 他
    |　値 | 説明|
    | --- | --- |
    | `top-left` | 左上のみ |
    | `top-right` | 右上のみ |
    | `bottom-left` | 左下のみ |
    | `bottom-right` | 右下のみ |

    ```css
    border-top-left-radius: 15px;
    ```

    <!-- demo
  
    ```html
    <div></div>
    ```
  
    ```css
    div {
      width: 80px;
      height: 50px;
      background-color: red;

      border-top-left-radius: 15px
    }
    ```
  
    -->

## 色
- ### 文字色
  `color`
  ```css
  color: red;
  ```

  <!-- demo

  ```html
  <div>文字の色</div>
  ```

  -->
  ---

- ### アクセントカラー
  `accent-color`：チェックボックス、ラジオボタン、レンジ、プログレスバーなどの色を指定

  ```css
  input {
    accent-color: red;
  }
  ```

  <!-- demo

  ```html
  <input type="checkbox" checked>チェックボックス</input>
  ```

  -->

## フォント

- ### 太さ
  `font-weight`
  ```css
  font-weight: bold;
  ```

  | 値 | 説明 | 例 |
  | --- | --- | --- |
  | `100` |  数値：細い | <span style="font-weight: 100">フォント</span> |
  | `lighter` |  より細く | <span style="font-weight: lighter">フォント</span> |
  | `normal` | 通常の太さ | <span style="font-weight: normal">フォント</span> |
  | `bold` | 太字 | <span style="font-weight: bold">フォント</span> |
  | `bolder` |  より太く | <span style="font-weight: bolder">フォント</span> |
  | `900` |  数値：太い | <span style="font-weight: 900">フォント</span> |

  数値
  ```css
  font-weight: 400;
  ```
  <span style="font-weight: 100">100</span> 
  <span style="font-weight: 200">200</span> 
  <span style="font-weight: 300">300</span> 
  <span style="font-weight: 400">400</span> 
  <span style="font-weight: 500">500</span> 
  <span style="font-weight: 600">600</span> 
  <span style="font-weight: 700">700</span> 
  <span style="font-weight: 800">800</span> 
  <span style="font-weight: 900">900</span> 


## テキスト

- ### 範囲選択

  `user-select`
  - 全選択（`all`）

    ```css
    user-select: all;
    ```

    <!-- demo

    ```html
    <div>クリックすると、テキストのすべてを範囲選択</div>
    ```

    -->

  - 選択可能にする（`text`）

    ```css
    user-select: text;
    ```

    <!-- demo

    ```html
    <div>選択可能</div>
    ```

    -->

  - 選択不可（`none`）

    ```css
    user-select: none;
    ```

    <!-- demo

    ```html
    <div>選択不可</div>
    ```

    -->
