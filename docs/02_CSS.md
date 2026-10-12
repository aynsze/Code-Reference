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
  - [範囲選択（`user-select`）](#範囲選択)
  - [単語間の隙間（`word-spacing`）](#単語間の隙間)
  - [文字間の隙間（`letter-spacing`）](#文字間の隙間)

- サイズ
  - [アスペクト比（`aspect-ratio`）](#アスペクト比)

- ユーザーインターフェース
  - [カーソル（`cursor`）](#カーソル)

### 配置

- グリッド
  - [ギャップ（`gap`）](#ギャップ)


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
  | 例                                          | 説明                              |
  | ------------------------------------------- | --------------------------------- |
  | `margin: 20px;` <!-- copy -->               | 全方向に 20px                     |
  | `margin: 20px 32px;` <!-- copy -->          | 上下に 20px、左右に 32px          |
  | `margin: 20px 32px 10px;` <!-- copy -->     | 上に 20px、左右に 32px、下に 10px |
  | `margin: 20px 32px 10px 5px;` <!-- copy --> | 上・右・下・左の順                |
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
    | 値             | 説明     |
    | -------------- | -------- |
    | `top-left`     | 左上のみ |
    | `top-right`    | 右上のみ |
    | `bottom-left`  | 左下のみ |
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

  | 値        | 説明       | 例                                                 |
  | --------- | ---------- | -------------------------------------------------- |
  | `100`     | 数値：細い | <span style="font-weight: 100">フォント</span>     |
  | `lighter` | より細く   | <span style="font-weight: lighter">フォント</span> |
  | `normal`  | 通常の太さ | <span style="font-weight: normal">フォント</span>  |
  | `bold`    | 太字       | <span style="font-weight: bold">フォント</span>    |
  | `bolder`  | より太く   | <span style="font-weight: bolder">フォント</span>  |
  | `900`     | 数値：太い | <span style="font-weight: 900">フォント</span>     |

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
  ---

- ### 単語間の隙間
  `word-spacing`：1.5em や 10px のような長さの単位で指定

  - 自動調整（`normal`）
    ```css
    word-spacing: normal;
    ```
    <!-- demo
    ```html
    <div>A VSCode extension that adds demo features to Markdown Preview.</div>
    ```
    -->

  - 指定する場合
    ```css
    word-spacing: 10px;
    ```
    <!-- demo
    ```html
    <div>A VSCode extension that adds demo features to Markdown Preview.</div>
    ```
    -->

- ### 文字間の隙間
  `letter-spacing`：1.5em や 10px のような長さの単位で指定

  - 自動調整（`normal`）
    ```css
    letter-spacing: normal;
    ```
    <!-- demo
    ```html
    <div>A VSCode extension that adds demo features to Markdown Preview.</div>
    ```
    -->

  - 指定する場合
    ```css
    letter-spacing: 10px;
    ```
    <!-- demo
    ```html
    <div>A VSCode extension that adds demo features to Markdown Preview.</div>
    ```
    -->

## サイズ
- ### アスペクト比
  `aspect-ratio`：縦横比を `2/1` のように指定

  `3/4` の場合、`横幅：縦幅 = 3:4`
  ```css
  /* 横3:縦4 */
  aspect-ratio: 3/4;
  ```
  <!-- demo
  ```html
  <div></div>
  ```
  ```css
  div {
    background-color: red;
    width: 50px;
    aspect-ratio: 3/4;
  }
  ```
  -->

  縦幅の `/1` は省略可能（省略時は `n/1` と同じ）
  ```css
  /* 2/1（横2:縦1）と同じ */
  aspect-ratio: 2;
  ```
  <!-- demo
  ```html
  <div></div>
  ```
  ```css
  div {
    background-color: red;
    width: 50px;
    aspect-ratio: 2;
  }
  ```
  -->

## ユーザーインタフェース
- ### カーソル
  `cursor`：マウスカーソルの形状を指定
  ```css
  cursor: pointer;
  ```

  | 値                                                        | 内容                                             |
  | --------------------------------------------------------- | ------------------------------------------------ |
  | <div style="cursor:auto">`auto`</div>                     | 状況に応じてブラウザーが決定                     |
  | <div style="cursor:default">`default`</div>               | そのプラットフォームにおけるデフォルトのカーソル |
  | <div style="cursor:none">`none`</div>                     | 表示しない                                       |
  | <div style="cursor:context-menu">`context-menu`</div>     | コンテキストメニュー                             |
  | <div style="cursor:help">`help`</div>                     | ヘルプカーソル                                   |
  | <div style="cursor:pointer">`pointer`</div>               | リンクポインタ                                   |
  | <div style="cursor:cell">`cell`</div>                     | セル選択カーソル                                 |
  | <div style="cursor:crosshair">`crosshair`</div>           | 十字線カーソル                                   |
  | <div style="cursor:alias">`alias`</div>                   | エイリアス作成カーソル                           |
  | <div style="cursor:copy">`copy`</div>                     | コピーカーソル                                   |
  | <div style="cursor:move">`move`</div>                     | 移動カーソル                                     |
  | <div style="cursor:all-scroll">`all-scroll`</div>         | 全方向へのスクロールが可能                       |
  | 状態                                                      |                                                  |
  | <div style="cursor:progress">　`progress`</div>           | 実行中カーソル                                   |
  | <div style="cursor:wait">　`wait`</div>                   | 待機状態カーソル                                 |
  | テキスト選択                                              |                                                  |
  | <div style="cursor:text">　`text`</div>                   | 横書き                                           |
  | <div style="cursor:vertical-text">　`vertical-text`</div> | 縦書き                                           |
  | 禁止                                                      |                                                  |
  | <div style="cursor:no-drop">　`no-drop`</div>             | その場所のドロップカーソル                       |
  | <div style="cursor:not-allowed">　`not-allowed`</div>     | 禁止カーソル                                     |
  | グラブ（ドラッグ）                                        |                                                  |
  | <div style="cursor:grab">　`grab`</div>                   | グラブ（ドラッグ）可能                           |
  | <div style="cursor:grabbing">　`grabbing`</div>           | グラブ（ドラッグ）中                             |
  | リサイズ                                                  |                                                  |
  | <div style="cursor:n-resize">　`n-resize`</div>           | 上（north：北）                                  |
  | <div style="cursor:s-resize">　`s-resize`</div>           | 下（south：南）                                  |
  | <div style="cursor:e-resize">　`e-resize`</div>           | 右（east：東）                                   |
  | <div style="cursor:w-resize">　`w-resize`</div>           | 左（west：西）                                   |
  | <div style="cursor:ne-resize">　`ne-resize`</div>         | 右上                                             |
  | <div style="cursor:nw-resize">　`nw-resize`</div>         | 左上                                             |
  | <div style="cursor:se-resize">　`se-resize`</div>         | 右下                                             |
  | <div style="cursor:sw-resize">　`sw-resize`</div>         | 左下                                             |
  | <div style="cursor:ew-resize">　`ew-resize`</div>         | 左右                                             |
  | <div style="cursor:ns-resize">　`ns-resize`</div>         | 上下                                             |
  | <div style="cursor:nesw-resize">　`nesw-resize`</div>     | 右上-左下                                        |
  | <div style="cursor:nwse-resize">　`nwse-resize`</div>     | 左上-右下                                        |
  | リサイズ（カラム）                                        |                                                  |
  | <div style="cursor:col-resize">　`col-resize`</div>       | 列を左右にリサイズ                               |
  | <div style="cursor:row-resize">　`row-resize`</div>       | 行を上下にリサイズ                               |
  | ズーム                                                    |                                                  |
  | <div style="cursor:zoom-in">　`zoom-in`</div>             | ズームイン                                       |
  | <div style="cursor:zoom-out">　`zoom-out`</div>           | ズームアウト                                     |


# 配置

## グリッド

- ### ギャップ
  `gap`：アイテム間の隙間サイズ（ギャップ）を指定

  - 縦横同じサイズ
    ```css
    gap: 縦横方向の隙間サイズ;
    ```
    ```css
    .parent {
      display: grid;
      grid: 30px 30px / 50px 50px 50px;
      gap: 20px;
    }
    ```
    <!-- demo
    ```html
    <div class="parent">
      <div class="itemA" style="background: lightblue;">A</div>
      <div class="itemB" style="background: lightpink;">B</div>
      <div class="itemC" style="background: lightgreen;">C</div>
      <div class="itemD" style="background: lightgray;">D</div>
      <div class="itemC" style="background: lightcoral;">E</div>
      <div class="itemD" style="background: lightcyan;">F</div>
    </div>
    ```
    -->

  - 縦横別々のサイズ
    ```css
    gap: 縦方向の隙間サイズ 横方向の隙間サイズ;
    ```
    ```css
    .parent {
      display: grid;
      grid: 30px 30px / 50px 50px 50px;
      gap: 20px 4px;
    }
    ```
    <!-- demo
    ```html
    <div class="parent">
      <div class="itemA" style="background: lightblue;">A</div>
      <div class="itemB" style="background: lightpink;">B</div>
      <div class="itemC" style="background: lightgreen;">C</div>
      <div class="itemD" style="background: lightgray;">D</div>
      <div class="itemC" style="background: lightcoral;">E</div>
      <div class="itemD" style="background: lightcyan;">F</div>
    </div>
    ```
    -->