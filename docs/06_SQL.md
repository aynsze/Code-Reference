### 基本
- 基本
  - [型](#型)
  - [制約（オプション）](#制約オプション)
  - [演算子](#演算子)

- テーブルの作成・変更・削除
  - [通常作成（`CREATE TABLE`）](#通常作成create-table)
  - [存在しなければ作成（`IF NOT EXISTS`）](#存在しなければ作成if-not-exists)
  <!-- - [テーブルの変更（`ALTER TABLE`）](#テーブルの変更)
  - [テーブルの削除（`DROP TABLE`）](#テーブルの削除) -->

- データの取得・絞り込み・並び替え
  - [データを取り出す（`SELECT`）](#データを取り出すselect)
  - [条件に一致するデータを取得（`WHERE`）](#条件に一致するデータを取得where)
  - [文字列の部分一致（`LIKE`）](#文字列の部分一致like)
  - [NULLの判定](#nullの判定)
  - [データの並び替え（`ORDER BY`）](#データの並び替えorder-by)
  - [最大で何件取得するか（`LIMIT`）](#最大で何件取得するかlimit)
  - [重複データを除く（`DISTINCT`）](#重複データを除くdistinct)

- データの集計・加工
  - [合計を計算（`SUM`）](#合計を計算sum)
  - [平均を計算（`AVG`）](#平均を計算avg)
  - [件数を数える（`COUNT`）](#件数を数えるcount)
  - [最大値を求める（`MAX`）](#最大値を求めるmax)
  - [最小値を求める（`MIN`）](#最小値を求めるmin)
  <!-- - [グループごとに集計（`GROUP BY`）](#グループごとに集計group-by)
  - [データ型を変換（`CAST`）](#データ型を変換cast) -->

<!-- - データの追加・変更・削除
  - [データの追加（`INSERT`）](#データの追加insert)
  - [データの変更（`UPDATE`）](#データの変更update)
  - [データの削除（`DELETE`）](#データの削除delete)

- インデックス・パフォーマンス最適化
  - [インデックスの作成（`CREATE INDEX`）](#インデックスの作成create-index)
  - [実行計画の確認（`EXPLAIN QUERY PLAN`）](#実行計画の確認explain-query-plan) -->

# 基本

## 基本
文字列はシングルクォーテーション（`'`）で囲む

- ### 型
  | SQL       | 意味     |
  | --------- | -------- |
  | `TEXT`    | 文字列型 |
  | `INTEGER` | 整数型   |
  ---
  
- ### 制約（オプション）
  | SQL             | 意味                  |
  | --------------- | --------------------- |
  | `PRIMARY KEY`   | 主キー                |
  | `NOT NULL`      | `NULL` 禁止（= 必須） |
  | `UNIQUE`        | 重複禁止              |
  | `AUTOINCREMENT` | 自動採番              |
  | `DEFAULT 値`    | 初期値                |
  | `CHECK 条件`    | 条件                  |
  ---
  
- ### 演算子
  | 演算子      | 意味                        |
  | ----------- | --------------------------- |
  | 列名 `=` B  | 列の値がBと等しい           |
  | 列名 `>` B  | 列の値がBより大きい         |
  | 列名 `<` B  | 列の値がBより小さい（未満） |
  | 列名 `>=` B | 列の値がB以上               |
  | 列名 `<=` B | 列の値がB以下               |
  | 列名 `!=` B | 列の値がBと等しくない       |
  | 列名 `<>` B | 列の値がBと等しくない       |


## テーブルの作成・変更・削除

- ### 通常作成（`CREATE TABLE`）
  `CREATE TABLE <テーブル名>`
  ```sql
  CREATE TABLE <テーブル名> (
    <列名> <型>,
    <列名> <型> <制約>
  );
  ```
  例：テーブル名「`users`」を作成し、その中に `id`、`name`、`age` という3つの列を作る
  ```sql
  CREATE TABLE users (
    id INTEGER PRIMARY KEY,
    name TEXT,
    age INTEGER DEFAULT 0
  );
  ```
  　↓　結果：列は作成されるが、データはまだ入っていない。
  | id  | name | age |
  | --- | ---- | --- |

  ---

  制約例：
  - `age` 列に0未満の値を登録できない（`NULL` は許可される）
    ```sql
    age INTEGER CHECK (age >= 0)
    ```
  - `name` 列に値を指定しなければ、既定値として「anonymous」を設定
    ```sql
    name TEXT DEFAULT 'anonymous'
    ```
  - `name` 列に値を `NULL` にできない
    ```sql
    name TEXT NOT NULL
    ```
  - `name` 列に重複する値を登録できない
    ```sql
    name TEXT UNIQUE
    ```
  ---

- ### 存在しなければ作成（`IF NOT EXISTS`）
    `CREATE TABLE IF NOT EXISTS <テーブル名>`：同名のテーブルがすでに存在する場合、新しく作成しない。
    
    ⚠ 既存テーブルの列を変更する機能ではない。

    例：テーブル名「`users`」が存在しなければ作る
    ```sql
    CREATE TABLE IF NOT EXISTS users (
      id INTEGER,
      name TEXT,
      age INTEGER
    );
    ```
  ---


## データの取得・絞り込み・並び替え
SELECT文は、次の順番で記述する（使用しない句は省略できる）。

| 順  | 句         |
| --- | ---------- |
| 1   | `SELECT`   |
| 2   | `FROM`     |
| 3   | `WHERE`    |
| 4   | `ORDER BY` |
| 5   | `LIMIT`    |

- 以降の例では、次のテーブルを使用する。

  テーブル名：`ingredients`

  | id  | name     | category | price |
  | --- | -------- | -------- | ----- |
  | 1   | 鶏もも肉 | 肉       | 250   |
  | 2   | にんじん | 野菜     | NULL  |
  | 3   | 豚こま肉 | 肉       | 80    |
  | 4   | 玉ねぎ   | 野菜     | 80    |
  | 5   | 鶏むね肉 | 肉       | 180   |

- ### データを取り出す（`SELECT`）

  - 列名を指定する

    列の順番は `SELECT` で指定した順番になる（テーブル定義の順番とは無関係）
    ```sql
    SELECT 列名, 列名, ...
    FROM テーブル名;
    ```
    例
    ```sql
    SELECT category, id
    FROM ingredients;
    ```
    　↓　結果
    | category | id  |
    | -------- | --- |
    | 肉       | 1   |
    | 野菜     | 2   |
    | 肉       | 3   |
    | 野菜     | 4   |
    | 肉       | 5   |

  - すべて

    すべての列を取り出したいときは、列名の代わりにアスタリスク（`*`）を使用
    ```sql
    SELECT *
    FROM テーブル名;
    ```
    例
    ```sql
    SELECT *
    FROM ingredients;
    ```
    　↓　結果
    | id  | name     | category | price |
    | --- | -------- | -------- | ----- |
    | 1   | 鶏もも肉 | 肉       | 250   |
    | 2   | にんじん | 野菜     | NULL  |
    | 3   | 豚こま肉 | 肉       | 80    |
    | 4   | 玉ねぎ   | 野菜     | 80    |
    | 5   | 鶏むね肉 | 肉       | 180   |

    1文でも同じ
    ```sql
    SELECT * FROM テーブル名;
    ```
  ---

- ### 条件に一致するデータを取得（`WHERE`）
  ```sql
  WHERE 条件;
  ```
  例：`price` 列で `200` 以上のデータを取得
  ```sql
  SELECT * FROM ingredients
  WHERE price >= 200;
  ```
  　↓　結果
  | id  | name     | category | price |
  | --- | -------- | -------- | ----- |
  | 1   | 鶏もも肉 | 肉       | 250   |
  ---

- ### 文字列の部分一致（`LIKE`）

  | 記号 | 意味                    |
  | ---- | ----------------------- |
  | `%`  | 0文字以上の任意の文字列 |
  | `_`  | 任意の1文字             |

  ```sql
  WHERE 列名 LIKE 'パターン';
  ```

  - 文字列xを含む（`%x%`）
    ```sql
    LIKE '%x%'
    ```

  - 前方一致（`x%`）

    `x` で始まる
    ```sql
    LIKE 'x%'
    ```
    例：`name` 列で「鶏」で始まるデータを取得
    ```sql
    SELECT * FROM ingredients
    WHERE name LIKE '鶏%';
    ```
    　↓　結果
    | id  | name     | category | price |
    | --- | -------- | -------- | ----- |
    | 1   | 鶏もも肉 | 肉       | 250   |
    | 5   | 鶏むね肉 | 肉       | 180   |

  - 後方一致（`%x`）

    `x` で終わる
    ```sql
    LIKE '%x'
    ```
    例：`name` 列で「肉」で終わるデータを取得
    ```sql
    SELECT * FROM ingredients
    WHERE name LIKE '%肉';
    ```
    　↓　結果
    | id  | name     | category | price |
    | --- | -------- | -------- | ----- |
    | 1   | 鶏もも肉 | 肉       | 250   |
    | 3   | 豚こま肉 | 肉       | 80    |
    | 5   | 鶏むね肉 | 肉       | 180   |

  - 任意の1文字（`_`）

    `_` 1個につき任意の1文字に一致する（個数分）
    ```sql
    LIKE 'x_'
    ```
    例：`category` 列で「野」で始まり、その後に1文字あるデータを取得
    ```sql
    SELECT * FROM ingredients
    WHERE category LIKE '野_';
    ```
    　↓　結果
    | id  | name     | category | price |
    | --- | -------- | -------- | ----- |
    | 2   | にんじん | 野菜     | NULL  |
    | 4   | 玉ねぎ   | 野菜     | 80    |

- ### NULLの判定
  `NULL` とは、値が存在しない、または不明であることを表す。

  ⚠ 空文字（`''`）や数値の `0` とは異なる  

  - NULLのデータを取得（`IS NULL`）
  
    ⚠ `= NULL` ではない
    ```sql
    WHERE 列名 IS NULL;
    ```
    例：`price` 列が `NULL` のデータ
    ```sql
    SELECT * FROM ingredients
    WHERE price IS NULL;
    ```
    　↓　結果
    | id  | name     | category | price |
    | --- | -------- | -------- | ----- |
    | 2   | にんじん | 野菜     | NULL  |
    ---

  - NULLではないデータを取得（`IS NOT NULL`）

    ⚠  `!= NULL` ではない
    ```sql
    WHERE 列名 IS NOT NULL;
    ```
    例：`price` 列が `NULL` ではないデータ
    ```sql
    SELECT * FROM ingredients
    WHERE price IS NOT NULL;
    ```
    　↓　結果
    | id  | name     | category | price |
    | --- | -------- | -------- | ----- |
    | 1   | 鶏もも肉 | 肉       | 250   |
    | 3   | 豚こま肉 | 肉       | 80    |
    | 4   | 玉ねぎ   | 野菜     | 80    |
    | 5   | 鶏むね肉 | 肉       | 180   |
  ---

- ###  データの並び替え（`ORDER BY`）

  | 値     | 意味                    | `NULL` の位置 |
  | ------ | ----------------------- | ------------- |
  | `ASC`  | 昇順（小さい順：A → Z） | 先頭          |
  | `DESC` | 降順（大きい順：Z → A） | 末尾          |

  ```sql
  ORDER BY 列名 値;
  ```

  - 昇順（`ASC`）

    例：`price` 列で価格の安い順
    ```sql
    SELECT * FROM ingredients
    ORDER BY price ASC;
    ```
    　↓　結果：`NULL` は先頭
    | id  | name     | category | price |
    | --- | -------- | -------- | ----- |
    | 2   | にんじん | 野菜     | NULL  |
    | 3   | 豚こま肉 | 肉       | 80    |
    | 4   | 玉ねぎ   | 野菜     | 80    |
    | 5   | 鶏むね肉 | 肉       | 180   |
    | 1   | 鶏もも肉 | 肉       | 250   |
    ---

  - 降順（`DESC`）

    例：`price` 列で価格の高い順
    ```sql
    SELECT * FROM ingredients
    ORDER BY price DESC;
    ```
    　↓　結果：`NULL` は末尾
    | id  | name     | category | price |
    | --- | -------- | -------- | ----- |
    | 1   | 鶏もも肉 | 肉       | 250   |
    | 5   | 鶏むね肉 | 肉       | 180   |
    | 3   | 豚こま肉 | 肉       | 80    |
    | 4   | 玉ねぎ   | 野菜     | 80    |
    | 2   | にんじん | 野菜     | NULL  |
  ---

- ### 最大で何件取得するか（`LIMIT`）
  ```sql
  LIMIT 数値;
  ```
  例：最大3件取得
  ```sql
  SELECT * FROM ingredients
  LIMIT 3;
  ```
  　↓　結果
  | id  | name     | category | price |
  | --- | -------- | -------- | ----- |
  | 1   | 鶏もも肉 | 肉       | 250   |
  | 2   | にんじん | 野菜     | NULL  |
  | 3   | 豚こま肉 | 肉       | 80    |
  ---

- ### 重複データを除く（`DISTINCT`）
  `DISTINCT 列名`：指定した列の重複する値を除く
  ```sql
  SELECT DISTINCT 列名 FROM テーブル名
  ```
  例：`price` 列の重複する値を除く
  ```sql
  SELECT DISTINCT price FROM ingredients;
  ```
  　↓　結果
  | price |
  | ----- |
  | 250   |
  | NULL  |
  | 80    |
  | 180   |





## データの集計・加工
`関数(列名)`

- ### 合計を計算（`SUM`）
  `SUM(列名)`：列の値の合計を計算する（`NULL` は無視される）
  ```sql
  SELECT SUM(列名) FROM テーブル名;
  ```
  例：`price` 列を合計を計算
  ```sql
  SELECT SUM(price) FROM ingredients;
  ```
  　↓　結果
  | SUM(price) |
  | ---------- |
  | 590        |
  ---

- ### 平均を計算（`AVG`）
  `AVG(列名)`：列の値の平均を計算する（`NULL` は無視される）
  ```sql
  SELECT AVG(列名) FROM テーブル名;
  ```
  例：`price` 列の平均を計算
  ```sql
  SELECT AVG(price) FROM ingredients;
  ```
  　↓　結果
  | AVG(price) |
  | ---------- |
  | 147.5      |

- ### 件数を数える（`COUNT`）
  - 列名を指定する

    指定した列の `NULL` ではない値の件数を数える
    ```sql
    SELECT COUNT(列名) FROM テーブル名;
    ```
    例：`name` 列のデータ数
    ```sql
    SELECT COUNT(name) FROM ingredients;
    ```
    　↓　結果：`name` 列には `NULL` がないので、結果は `5`
    | COUNT(name) |
    | ----------- |
    | 5           |

    - ⚠ 列名を指定した場合、`NULL` の値は数えない
    
      例：`price` 列のデータ数
      ```sql
      SELECT COUNT(price) FROM ingredients;
      ```
      　↓　結果
      | COUNT(price) |
      | ------------ |
      | 4            |

  - すべて（レコード数）
    列の値の数ではなく、レコードの数を数える（`NULL` の有無に関係なし）

    ⚠ `COUNT(*)` の `*` は、すべての列を取得するという意味ではなく、すべてのレコードを数えるという意味。`SELECT *` の `*` とは使い方が異なる。
    ```sql
    SELECT COUNT(*) FROM テーブル名;
    ```
    例
    ```sql
    SELECT COUNT(*) FROM ingredients;
    ```
    　↓　結果
    | COUNT(*) |
    | -------- |
    | 5        |
  ---

- ### 最大値を求める（`MAX`）
  ```sql
  MAX(列名)
  ```
  例：`price` 列の最大値
  ```sql
  SELECT MAX(price) FROM ingredients;
  ```
  　↓ 結果
  | MAX(price) |
  | ---------- |
  | 250        |
  ---

- ### 最小値を求める（`MIN`）
  ```sql
  MIN(列名)
  ```
  例：`price` 列の最小値
  ```sql
  SELECT MIN(price) FROM ingredients;
  ```
  　↓ 結果
  | MIN(price) |
  | ---------- |
  | 80         |

