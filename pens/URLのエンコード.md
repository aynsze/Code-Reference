# エンコードされたURLを文字列に変換
[`decodeURI(エンコードされた値)`](../docs/03_2.%20JavaScript_応用.md#エンコード)

```js
// 1. JSONファイルのURLを定義
const url = "https://raw.githubusercontent.com/aynsze/Recipe/refs/heads/main/data/%E3%82%BF%E3%82%B3%E3%81%AE%E9%85%A2%E3%81%AE%E7%89%A9.json";

// 2. ➀を文字列に変換
const decode = decodeURI(url);

console.log(decode);
// => 省略.../タコの酢の物.json
```
<!-- demo -->