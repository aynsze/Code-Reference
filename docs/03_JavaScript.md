### 基本

- メッセージ表示
  - [ダイアログ（`alert`）](#ダイアログ)
  - [コンソール（`console`）](#コンソール)

- 文字列出力
  - [変数を用いる場合](#変数を用いる場合)

### 数学系
- 数学関数
  - [繰り上げ（`ceil`）](#繰り上げceil)
  - [繰り下げ（`floor`）](#繰り下げfloor)
  - [四捨五入（`round`）](#四捨五入round)
  - [小数点以下を削除（`trunc`）](#小数点以下を削除trunc)

- 演算子
  - [算術演算子](#算術演算子)
  - [インクリメント演算子](#インクリメント演算子)
  - [複合・論理代入演算子](#複合論理代入演算子)

### 文字列
- 基本
  - [文字列の長さを取得（`length`）](#文字列の長さを取得length)

- 文字列の置換
  - [通常の置換](#通常の置換)
  - [大文字・小文字に置換](#大文字小文字に置換)

- 文字列の部分取り出し
  - [取り除く（`trim`）](#取り除くtrim)

### オブジェクト
- プロパティ
  - [配列を返す](#配列を返す)



# 基本

## メッセージ表示

- ### ダイアログ
  `alert`
  ```js
  alert("Hello");
  ```

- ### コンソール
  `console`
  ```js
  console.log("Hello");
  ```
  <!-- demo -->

## 文字列出力

- ### 変数を用いる場合

  文字列全体をバッククォート「\`」で囲んで、`${変数名}`

  ```js
  let name = "花子";
  console.log(`こんにちは、${name}です！`);
  ```

  <!-- demo -->

# 数学系

## 数学関数
`Math.`
| 意味 | 値|
| --- | --- |
| 繰り上げ | `ceil` |
| 繰り下げ | `floor` |
| 四捨五入 | `round` |
| 小数点以下を削除 | `trunc` |

- ### 繰り上げ（`ceil`）
  `Math.ceil(n)` ：n の小数点以下を繰り上げた整数値を返す

  ```js
  Math.ceil(3.2);   // 4
  ```
  <!-- demo -->

  ```js
  Math.ceil(-3.6);    // -3
  ```
  <!-- demo -->
  ---

- ### 繰り下げ（`floor`）
  `Math.floor(n)` ：n の小数点以下を繰り下げた整数値を返す

  ```js
  Math.floor(3.6);    // 3
  ```
  <!-- demo -->

  ```js
  Math.floor(-3.6);   // -4
  ```
  <!-- demo -->
  ---

- ### 四捨五入（`round`）
  `Math.round(n)` ：n の四捨五入した整数値を返す

  ```js
  Math.round(3.2);    // 3
  ```
  <!-- demo -->

  ```js
  Math.round(-3.6);   // -4
  ```
  <!-- demo -->
  ---

- ### 小数点以下を削除（`trunc`）
  `Math.trunc(n)` ：n の小数点以下を削除した整数部分を返す

  ```js
  Math.trunc(3.2);    // 3
  ```
  <!-- demo -->

  ```js
  Math.trunc(-3.6);   // -3
  ```
  <!-- demo -->

## 演算子
- ### 算術演算子
  | 説明 | 算術演算子 |
  | --- | --- |
  | 足し算 | `+` |
  | 引き算 | `-` |
  | 掛け算 | `*` |
  | 割り算 | `/` |
  | 割った余り | `%` |
  | べき乗 | `**` |

  - 足し算
    ```js
    10 + 3   // 10 + 3 = 13
    ```
    <!-- demo -->

  - 引き算
    ```js
    10 - 3   // 10 - 3 = 7
    ```
    <!-- demo -->

  - 掛け算
    ```js
    10 * 3    // 10 × 3 = 30
    ```
    <!-- demo -->

  - 割り算
    ```js
    10 / 3    // 10 ÷ 3 = 3.3333333333333335
    ```
    <!-- demo -->

  - 割った余り
    ```js
    10 % 3    // 10 ÷ 3の余り = 1
    ```
    <!-- demo -->

  - べき乗
    ```js
    10 ** 3   // 10の3乗 = 1000
    ```
    <!-- demo -->
  ---

- ### インクリメント
  | 説明 | 演算子|
  | --- | --- |
  | 増やしてから使う | `++変数名` |
  | 減らしてから使う | `++変数名` |
  | 使ってから増やす | `変数名++` |
  | 使ってから減らす | `変数名--` |

  前置インクリメント
    - 増やしてから使う（`++変数名`）
      ```js
      a = 5;
      console.log(++a);   // 5 + 1 = 6
      ```
      <!-- demo -->

    - 減らしてから使う（`--変数名`）
      ```js
      a = 5;
      console.log(--a);   // 5 - 1 = 4
      ```
      <!-- demo -->
    ---

  後置インクリメント
    - 使ってから増やす（`変数名++`）
      ```js
      a = 5;
      a++;    // 5 + 1 で6になる
      console.log(a);   // 6
      ```
      <!-- demo -->
      ⚠ 以下では、使用されていないため、そのまま
      ```js
      a = 5;
      console.log(a++);   // 5
      ```
      <!-- demo -->

    - 使ってから減らす（`変数名--`）
      ```js
      a = 5;
      a--;    // 5 - 1 で4になる
      console.log(a);   // 4
      ```
      <!-- demo -->
  ---

- ### 複合・論理代入演算子
  | 説明 | 演算子 | 複合・論理代入演算子 |
  | --- | --- | --- |
  | 足し算 | `+` | `+=` |
  | 引き算 | `-` | `-=` |
  | 掛け算 | `*` | `*=` |
  | 割り算 | `/` | `/=` |
  | 割った余り | `%` | `%=` |
  | べき乗 | `**` | `**=` |

  - 足し算
    ```js
    a = 10;
    a += 3;   // a = a + 3; と同じ
    console.log(a);
    ```
    <!-- demo -->

## 数値

- ### 小数点の設定（toFixed）
  `数値.toFixed(桁数)`

  桁数が無記入の場合は、整数
  ```js
  1.2345.toFixed();   // 1
  ```
  <!-- demo -->

  桁数が `2` の場合は、小数点第2位まで表示
  ```js
  const num = 1.2345;
  console.log(num.toFixed(2));    // 1.23
  ```
  <!-- demo -->



# 文字列

## 基本
- ### 文字列の長さを取得（`length`）
  `文字列.length` ：文字列の文字の個数を返す

  ```js
  let address = "東京都";
  console.log(address.length);  // 3
  ```
  <!-- demo -->

  ```js
  "あいうえお".length;  // 5
  ```
  <!-- demo -->
  ---

## 文字列の置換
- ### 通常の置換
  - 最初の1件だけ置換（`replace`）

    `文字列.replace(置換前, 置換後)`

    例：「a pen」のみ「pen」を「book」に置換
    ```js
    "There is a pen, a pencil case, a red pen, and a book.".replace("pen", "book");
    ```
    <!-- demo -->

  - 全件置換（`replaceAll`）

    `文字列.replaceAll(置換前, 置換後)`

    例：「a pen」と「a pencil」と「a red pen」の「pen」を「book」に置換
    ```js
    "There is a pen, a pencil case, a red pen, and a book.".replaceAll("pen", "book");
    ```
    <!-- demo -->
  ---

- ### 大文字・小文字に置換
  - 大文字に置換（`toUpperCase`）

    `文字列.toUpperCase()` ：小文字のアルファベットを大文字に変換した新しい文字列を返す

    ```js
    "Hello".toUpperCase();    // HELLO
    ```
    <!-- demo -->

  - 小文字に置換（`toLowerCase`）

    `文字列.toLowerCase()` ：大文字のアルファベットを小文字に変換した新しい文字列を返す

    ```js
    "Hello".toLowerCase();    // hello
    ```
    <!-- demo -->


## 文字列の部分取り出し
- ### 取り除く（`trim`）
  - 先頭&末尾の空白を取り除く（`trim`）

    `文字列.trim()` ：文字列の先頭および末尾から空白を取り除いた文字列を返す

    ```js
    "   Hello   ".trim();   // 「Hello」
    ```
    <!-- demo 
    ```js
    console.log("   Hello   ".trim());
    ```
    -->

  - 先頭の空白を取り除く（`trimStart`）

    `文字列.trimStart()` ：文字列の先頭から空白を取り除いた文字列を返す

    ```js
    "   Hello   ".trimStart();   // 「Hello   」
    ```
    <!-- demo 
    ```js
    console.log("   Hello   ".trimStart());
    ```
    -->

  - 末尾の空白を取り除く（`trimEnd`）

    `文字列.trimEnd()` ：文字列の末尾から空白を取り除いた文字列を返す

    ```js
    "   Hello   ".trimEnd();    // 「   Hello」
    ```
    <!-- demo 
    ```js
    console.log("   Hello   ".trimEnd());
    ```
    -->

# オブジェクト
`key: value`
```js
const obj = {
  width: 160,
  height: 120
};
```

## プロパティ
- ### 配列を返す
  - 名前を返す（`keys`）

    `Object.keys（変数名）`
    ```js
    Object.keys(obj);   // ["width","height"]
    ```
    <!-- demo
    ```js
    const obj = {
      width: 160,
      height: 120
    };

    console.log(Object.keys(obj));
    ```
    -->

  - 値を返す（`values`）

    `Object.values（変数名）`
    ```js
    Object.values(obj);   // [160,120]
    ```
    <!-- demo
    ```js
    const obj = {
      width: 160,
      height: 120
    };

    console.log(Object.values(obj));
    ```
    -->

  - 配列全体を返す（`entries`）

    `Object.entries（変数名）`
    ```js
    Object.entries(obj);    // [["width",160],["height",120]]
    ```
    <!-- demo
    ```js
    const obj = {
      width: 160,
      height: 120
    };

    console.log(Object.entries(obj));
    ```
    -->
