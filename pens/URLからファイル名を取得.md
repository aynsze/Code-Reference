## 1. `/` で分割して配列にする
```js
// 1. URLを定義
const url = "https://example.com/images/cover.jpg";

// 2. ➀を「/」で分割して、配列にする
const parts = url.split("/");

console.log(parts);
// => ["https:","","example.com","images","cover.jpg"]
```
<!-- demo -->

## 2. `pop()` で配列の最後の要素を取得
```js
// 1. URLを定義
const url = "https://example.com/images/cover.jpg";

// 2. ➀を「/」で分割して、配列にする
const parts = url.split("/");

// 3. ➁の最後の1つの要素を取得
const filename = parts.pop();

console.log(filename);
// => cover.jpg
```
<!-- demo -->

- 以下でも可能
  ```js
  // ➁&➂
  // ➀を「/」で分割して、最後の1つの要素を取得
  const filename = url.split("/").pop();
  ```