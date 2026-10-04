## 実行

```python
python main.py
```

## インポート
例：`from PySide6.QtWidgets import QApplication`

| from PySide6. |      import                    |                    |
| ------------- | ------------------------------ | ------------------ |
| `QtWidgets`   | QApplication                   |                    |
|   | QMainWindow                   |                    |
|               | [QWidget](#ウィジェットを設定-qwidget) | ウィジェットを設定 |
|               | [QVBoxLayout](#上下に配置-qvboxlayout)   | 上下に配置         |
|               | [QHBoxLayout](#左右に配置-qhboxlayout)   | 左右に配置         |
|               | [QLabel](#ラベル-qlabel)        |ラベル|
|               | QScrollArea                    |
|               | [QPushButton](#ボタン-qpushbutton)         | ボタン             |
|               | [QTableWidget](#表作成-qtablewidget)     | 表作成             |
|               | QTableWidgetItem               |
|               | QSizePolicy                    |
|               | QCheckBox                      | チェックボックス   |
|               | QComboBox                      |
|               | QStyledItemDelegate            |
|               | QSplitter                      |
|               | QHeaderView                    |
|               | QDialog                        |
|               | QButtonGroup                   |
|               | QMessageBox                    |メッセージボックス
|               | QAbstractItemView                    |
|               | QFileDialog                        |ファイルダイアログ
|               | QProgressDialog                        |プログレスダイアログ
|               | QButtonGroup                   |
| `QtCore`      | Qt                             |
|               | QTimer                         | タイマー           |
|               | QRect                          |
|               | QDate                          |
|               | QDateTime                      |
| `QtGui`       | QPainter                       |
|               | QColor                         | 色                 |
|               | QPen                           |
|               | QBrush                         |
|               | QAction                         |

## init

`__init__` 内に入れる

- ### Windowタイトル（`.setWindowTitle`）
  「サンプル」という名前のウィンドウタイトルを設定
  ```python
  self.setWindowTitle("サンプル")
  ```

- ### Windowサイズ（`.resize`）
  横800、縦600のウィンドウサイズを設定
  ```python
  self.resize(800, 600)
  ```

## メニューバー

- ### メニュー作成（`.addMenu`）
  「表示」というメニューを作成
  ```python
  menu_bar.addMenu("表示")
  ```

## 基本

- ### ショートカットキー➀（`.setShortcut`）

  関数名「undo_action」に`Ctrl+Z`を設定

  ```python
  undo_action.setShortcut("Ctrl+Z")
  ```


- ### ラベル（`= QLabel`）

  関数名「subject_label」に `科目` という名前のラベル

  ```python
  subject_label = QLabel("科目")
  ```

- ### ボタン（`= QPushButton`）

  関数名「self.start_button」に `勉強開始` という名前のボタン

  ```python
  self.start_button = QPushButton("勉強開始")
  ```

- ### 語尾に文字列を追加（`.setSuffix`）

  関数名「self.retention_spin」に `日` を最後に付ける

  ```python
  self.retention_spin.setSuffix("日")
  ```

## ウィジェット・レイアウト

- ### ウィジェットを設定（`= QWidget`）

  関数名「header_widget」にウィジェットを設定

  ```python
  header_widget = QWidget()
  ```

- ### ウィジェットに追加（`.addWidget`）

  関数名「button_layout」に「add_button」関数を追加

  ```python
  button_layout.addWidget(add_button)
  ```

- ### レイアウトに追加（`.addLayout`）

  関数名「main_layout」に「button_layout」関数を追加

  ```python
  main_layout.addLayout(button_layout)
  ```


- ### グループボックス（`= QGroupBox`）

  関数名「study_group」に「勉強記録」という名前のグループボックスを設定

  ```python
  study_group = QGroupBox("勉強記録")
  ```

- ### 左右に配置（`= QHBoxLayout`）

  関数名「button_layout」を左右に配置

  ```python
  button_layout = QHBoxLayout()
  ```

- ### 上下に配置（`= QVBoxLayout`）

  関数名「self.item_layout」を上下に配置

  ```python
  self.item_layout = QVBoxLayout()
  ```

## 表

- ### 表作成（`= QTableWidget`）

  関数名「self.records_table」にテーブルウィジェットを作成

  ```python
  self.records_table = QTableWidget()
  ```

- ### 表列の設定（`.setColumnCount`）

  関数名「self.records_table」の表列を5列にする

  ```python
  self.records_table.setColumnCount(5)
  ```

- ### ヘッダー行の設定（`.setHorizontalHeaderLabels`）
  関数名「self.records_table」にヘッダー `日付` - `科目` - `時間` を作成
  ```python
  self.records_table.setHorizontalHeaderLabels(
    ["日付", "科目", "時間"]
  )
  ```


## メッセージボックス

- ### 警告
  ```python
  QMessageBox.warning()
  ```

- ### 質問
  ```python
  QMessageBox.question()
  ```

- ### 情報
  ```python
  QMessageBox.information()
  ```

- ### about
  ```python
  QMessageBox.about()
  ```

## デザイン

- ### CSSを設定（`.setStyleSheet`）
  関数名「self.today_time_label」にCSSを設定
  ```python
  self.today_time_label.setStyleSheet(
    "font-size: 24px;"
  )
  ```

- ### 背景色

  - 関数名「item」に前景色を設定（`.setForeground`）
    ```python
    item.setForeground(QColor("#34B890"))
    ```

  - 関数名「item」に背景色を設定（`.setBackground`）
    ```python
    item.setBackground(QColor("#3C3C3C"))
    ```

## 余白・サイズ

- ### 余白（`.setContentsMargins`）

  関数名「operation_layout」に左10px、上15px、右20px、下25pxの余白を設定

  ```python
  operation_layout.setContentsMargins(10, 15, 20, 25)
  ```

