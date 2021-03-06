# 1. UPDATE 文について

## 1.1. 基本構文

```sql
UPDATE テーブル名
    SET 列名1=値1, 列名2=値2
(WHERE 修飾)
```

※修飾の部分はなくても動作する。

## 1.2. 実例

#### 1.2.0.1. 家計簿テーブル

| 日付       | 費目       | 　メモ         | 入金額 | 出金額 |
| ---------- | ---------- | -------------- | ------ | ------ |
| 2018-02-03 | 食費       | コーヒーを購入 | 0      | 380    |
| 2018-02-10 | 給料       | 1 月の給料     | 280000 | 0      |
| 2018-02-11 | 教養娯楽費 | 書籍を購入     | 0      | 2800   |
| 2018-02-14 | 交際費     | 同期会の会費   | 0      | 5000   |
| 2018-02-18 | 水道光熱費 | 1 月の電気代   | 0      | 7560   |

---

### 1.2.1. 条件指定無し

#### 1.2.1.1. 実行する SQL 文

```sql
UPDATE 家計簿
    SET 入金 = 99999
```

#### 1.2.1.2. 実行結果

| 日付       | 費目       | 　メモ         | 入金額    | 出金額 |
| ---------- | ---------- | -------------- | --------- | ------ |
| 2018-02-03 | 食費       | コーヒーを購入 | **99999** | 380    |
| 2018-02-10 | 給料       | 1 月の給料     | **99999** | 0      |
| 2018-02-11 | 教養娯楽費 | 書籍を購入     | **99999** | 2800   |
| 2018-02-14 | 交際費     | 同期会の会費   | **99999** | 5000   |
| 2018-02-18 | 水道光熱費 | 1 月の電気代   | **99999** | 7560   |

---

### 1.2.2. WHERE 句で条件を指定

#### 1.2.2.1. 実行する SQL 文

```sql
UPDATE 家計簿
    SET 入金 = 99999
WHERE 日付 = '2018-02-03'
```

#### 1.2.2.2. 実行結果

| 日付       | 費目       | 　メモ         | 入金額    | 出金額 |
| ---------- | ---------- | -------------- | --------- | ------ |
| 2018-02-03 | 食費       | コーヒーを購入 | **99999** | 380    |
| 2018-02-10 | 給料       | 1 月の給料     | 280000    | 0      |
| 2018-02-11 | 教養娯楽費 | 書籍を購入     | 0         | 2800   |
| 2018-02-14 | 交際費     | 同期会の会費   | 0         | 5000   |
| 2018-02-18 | 水道光熱費 | 1 月の電気代   | 0         | 7560   |

---
