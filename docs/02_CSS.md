### 基本

- 疑似要素（`::`）
  - [範囲選択した文字のデザイン（`::selection`）](#範囲選択した文字のデザイン)
  - [箇条書きの記号部分（`::marker`）](#箇条書きの記号部分)
  - [最初の1行目（`::first-line`）](#最初の1行目)

- 疑似クラス（`:`）
  - [子要素](#子要素)

- レイアウト
  - [角丸（`border-radius`）](#角丸)

- 他
  - [テキストの範囲選択（`user-select）](#テキストの範囲選択)
  - [アクセントカラー（`accent-color`）](#アクセントカラー)

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
    <li>項目1</li>
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

##

- ### 角丸

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
  - 左上のみ角丸（`top-left`）

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

  - 右上のみ角丸（`top-right`）

    ```css
    border-top-right-radius: 15px;
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
    
          border-top-right-radius: 15px
      }
      ```
    
      -->

  - 左下のみ角丸（`bottom-left`）

    ```css
    border-bottom-left-radius: 15px;
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
    
          border-bottom-left-radius: 15px
      }
      ```
    
      -->

  - 右下のみ角丸（`bottom-right`）

    ```css
    border-bottom-right-radius: 15px;
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
    
          border-bottom-right-radius: 15px
      }
      ```
    
      -->

## 他

- ### テキストの範囲選択

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
