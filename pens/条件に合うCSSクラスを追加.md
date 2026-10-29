材料のグループが「A」なら、HTML要素に「group-A」というクラスを追加
```html
<div id="ingredient" class="ingredient-item">小麦粉</div>
```
<!-- demo -->

# 基本
## 1. クラス名を作成
```js
// 1. HTMLのid名「ingredient」を取得
const row = document.getElementById("ingredient");

// 2. グループ名を定義
const group = "A";

// 3. ➁を使用して、クラス名を作成
const groupClass = `group-${group}`;

console.log(groupClass);
// => group-A
```
<!-- demo
```html
<div id="ingredient" class="ingredient-item">小麦粉</div>
```
-->

## 2. クラスを追加
[`変数名.classList.add("クラス名")`](../docs/03_2.%20JavaScript_応用.md#クラス属性の操作classlist)

```js
// 1. HTMLのid名「ingredient」を取得
const row = document.getElementById("ingredient");

// 2. グループ名を定義
const group = "A";

// 3. ➁を使用して、クラス名を作成
const groupClass = `group-${group}`;

// ➀に➂のクラスを追加
row.classList.add(groupClass);

console.log(row.className);
// => ingredient-item group-A
```
<!-- demo
```html
<div id="ingredient" class="ingredient-item">小麦粉</div>
```
-->

# 応用
あらかじめ決めたクラス名だけを許可するようにする

[`配列.includes("指定した値")`](../docs/03_1.%20JavaScript_基本.md#文字列の判定)（`文字列.includes("検索値")`）：配列に指定した値が含まれているか判定

```js
// 1. 追加を許可するクラス名を配列で定義
const GROUP_CLASSES = [
  "group-A",
  "group-B",
  "group-C",
  "group-D"
];

// 2. HTMLのid名「ingredient」を取得
const row = document.getElementById("ingredient");

// 3. グループ名を定義
const group = "X";

// 4. ➂を使用して、クラス名を作成
const groupClass = `group-${group}`;

// ➀に➃のクラス名「group-X」が含まれている場合に実行
if (GROUP_CLASSES.includes(groupClass)) {

  // ➀に➃のクラスを追加
  row.classList.add(groupClass);
}

console.log(row.className);
// 「group-X」は、含まれていないので追加されない
// => ingredient-item
```
<!-- demo
```html
<div id="ingredient" class="ingredient-item">小麦粉</div>
```
-->