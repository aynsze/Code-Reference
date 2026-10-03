### 基本

- テーブル作成（`CREATE TABLE`）
  - [通常作成](#通常作成)
  - [存在しなければ作成](#存在しなければ作成)

# 基本

- ### 型
    | SQL | 意味|
    | --- | --- |
    | `TEXT` | 文字列型 |
    | `INTEGER` | 整数型 |

- ### 制約（オプション）
    | SQL             | 意味                    |
    | --------------- | --------------------- |
    | `PRIMARY KEY`   | 主キー  |
    | `NOT NULL`      | `NULL` 禁止（= 必須）    |
    | `UNIQUE`        | 重複禁止   |
    | `AUTOINCREMENT` | 自動採番     |
    | `DEFAULT 値`    | 初期値 |
    | `CHECK 条件`    | 条件        |

    ---

## テーブル作成

- ### 通常作成
    `CREATE TABLE <テーブル名>`
    ```sql
    CREATE TABLE <テーブル名> (
        <列名> <型>,
        <列名> <型> <制約>
    );
    ```
    例：`users` というテーブルを作って、その中に `id`、`name`、`age` という3つの列を作る
    ```sql
    CREATE TABLE users (
        id INTEGER PRIMARY KEY,
        name TEXT,
        age INTEGER DEFAULT 0
    );
    ```
    　↓　結果
    | id | name | age |
    | :-: | :----: | :--: |
    |    |      |  0  |
    ---

    他の制約
    - 0以上の整数
        ```sql
        age INTEGER CHECK (age >= 0)
        ```
    - 指定しなければ初期値「active」
        ```sql
        status TEXT DEFAULT 'active'
        ```
    ---

- ### 存在しなければ作成
    `CREATE TABLE IF NOT EXISTS <テーブル名>`

    例：`users` というテーブルが存在しなければ作る
    ```sql
    CREATE TABLE IF NOT EXISTS users (
        id INTEGER,
        name TEXT,
        age INTEGER
    );
    ```
    ---
