例
```json
{
  "title": "タコの酢の物",
  "source": "arranged",
  "category": "副菜",
  "rating": 4,
  "image": "https://img-global-jp.cpcdn.com/recipes/2357754/640x640sq80/photo.webp",
  "url": "https://cookpad.com/jp/recipes/19043944",
  "ingredients": [
    {
      "group": null,
      "name": "茹でタコ",
      "amount": 100,
      "unit": "g"
    },
    {
      "group": "A",
      "name": "砂糖",
      "amount": 3,
      "unit": "小さじ"
    },
    {
      "group": "A",
      "name": "醤油",
      "amount": 1,
      "unit": "小さじ"
    },
    {
      "group": "A",
      "name": "酢",
      "amount": 6,
      "unit": "小さじ"
    }
  ],
  "preparation": [],
  "steps": [
    "タコを切る",
    "ボウルの中でAを砂糖が溶けるまでよく混ぜておく"
  ],
  "memo": "酢：砂糖：醤油は、6：3：1の割合"
}
```

# URLを指定してJSONを読み込む
[`await 変数名.json()`](../docs/03_2.%20JavaScript_応用.md#Fetch)

```js
async function fetchData() {
  // 1. JSONファイルのURLを定義
  const url = "https://raw.githubusercontent.com/aynsze/Recipe/refs/heads/main/data/タコの酢の物.json";

  // 2. ➀からファイルを取得
  const response = await fetch(url);

  // 3. ➁をJSONとして解析し、オブジェクトに変換
  const recipe = await response.json();

  console.log(recipe);
}

fetchData();
```
<!-- demo -->

# JSONからデータを取り出す
[`変数名[n]`](../docs/03_1.%20JavaScript_基本.md#配列の取り出し)：0始まり

| コード                       | 種類         | 理由                          |
| :--------------------------- | :----------- | :---------------------------- |
| `recipe`                     | オブジェクト | `{}` で囲まれたデータ全体     |
| `recipe.ingredients`         | 配列         | `[]` で囲まれた材料の一覧     |
| `recipe.ingredients[0]`      | オブジェクト | 1つ目の材料の情報             |
| `recipe.ingredients[0].name` | 文字列       | 1つ目の材料の情報のうちの名前 |
| `recipe.steps`               | 配列         | 手順の一覧                    |
| `recipe.steps[0]`            | 文字列       | 1つ目の手順                   |


## 基本
```js
async function fetchData() {
  // 1. JSONファイルのURLを定義
  const url = "https://raw.githubusercontent.com/aynsze/Recipe/refs/heads/main/data/タコの酢の物.json";

  // 2. ➀からファイルを取得
  const response = await fetch(url);

  // 3. ➁をJSONとして解析し、オブジェクトに変換
  const recipe = await response.json();

  // ➂からレシピ名を取得
  console.log(recipe.title);
  // => タコの酢の物

  // ➂から評価を取得
  console.log(recipe.rating);
  // => 4
}

fetchData();
```
<!-- demo -->

## JSON内に配列がある場合
- ### 配列を取得
  ```js
  // ➂から手順を取得
  recipe.steps
  // => ["タコを切る","ボウルの中でAを砂糖が溶けるまでよく混ぜておく"]
  ```
  <!-- demo
  ```js
  async function fetchData() {
    const url = "https://raw.githubusercontent.com/aynsze/Recipe/refs/heads/main/data/タコの酢の物.json";
    const response = await fetch(url);
    const recipe = await response.json();
    console.log(recipe.steps);
  }

  fetchData();
  ```
  -->

- ### 1つの要素を取り出す
  ```js
  // ➂から手順の1つ目を取得
  recipe.steps[0]
  // => タコを切る
  ```
  <!-- demo
  ```js
  async function fetchData() {
    const url = "https://raw.githubusercontent.com/aynsze/Recipe/refs/heads/main/data/タコの酢の物.json";
    const response = await fetch(url);
    const recipe = await response.json();
    console.log(recipe.steps[0]);
  }

  fetchData();
  ```
  -->

## JSON内に階層構造がある場合
- ### 配列を取得
  ```js
  // ➂から材料を取得
  recipe.ingredients
  // => [{"group":null,"name":"茹でタコ","amount":100,"unit":"g"},...,{"group":"A","name":"酢","amount":6,"unit":"小さじ"}]
  ```
  <!-- demo
  ```js
  async function fetchData() {
    const url = "https://raw.githubusercontent.com/aynsze/Recipe/refs/heads/main/data/タコの酢の物.json";
    const response = await fetch(url);
    const recipe = await response.json();
    console.log(recipe.ingredients);
  }

  fetchData();
  ```
  -->

- ### 1つの要素を取り出す
  ```js
  // ➂から材料の名前を取得
  // （ingredients配列の1つ目の要素のうち、nameプロパティを取得）
  recipe.ingredients[0].name
  // => 茹でタコ
  ```
  <!-- demo
  ```js
  async function fetchData() {
    const url = "https://raw.githubusercontent.com/aynsze/Recipe/refs/heads/main/data/タコの酢の物.json";
    const response = await fetch(url);
    const recipe = await response.json();
    console.log(recipe.ingredients[0].name);
  }

  fetchData();
  ```
  -->
