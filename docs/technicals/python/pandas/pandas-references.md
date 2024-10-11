---
title: Pandas 参考
tags:
  - Python
  - Pandas
  - Reference
---

## 快捷链接

- [Pandas 官网](https://pandas.pydata.org/docs/index.html)
- [Pandas Github](https://github.com/pandas-dev/pandas)

## 概念

Pandas 的主要数据结构是 `Series` （一维数据）与 `DataFrame`（二维数据）。

- `Series` 是一种类似于一维数组的对象，它由一组数据（各种 Numpy 数据类型）以及一组与之相关的数据标签（即索引）组成。

- `DataFrame` 是一个表格型的数据结构，它含有一组有序的列，每列可以是不同的值类型（数值、字符串、布尔型值）。`DataFrame` 既有行索引也有列索引，它可以被看做由 `Series` 组成的字典（共同用一个索引）。

<figure markdown="span">
    ![DataFrame](https://pandas.pydata.org/docs/_images/01_table_dataframe.svg)
    <figcaption><b>图 1.</b> <code>Data Frame</code></figcaption>
</figure>

<figure markdown="span">
    ![Series](https://pandas.pydata.org/docs/_images/01_table_series.svg)
    <figcaption><b>图 2.</b> <code>Series</code></figcaption>
</figure>

## 安装和导入

**从 pip 安装**

```shell
pip install pandas
```

**导入 pandas**

```python
import pandas as pd
```

## 读写数据

=== "从文件读取：`read_*()`"

    ```python
    # read .csv file
    data = pd.read_csv("/path/to/data/data.csv")

    # read .tsv file
    data = pd.read_csv("/path/to/data/data.tsv", sep="\t")

    # read .excel file
    data = pd.read_excel("/path/to/data/data.excel")
    ```

=== "写入到文件：`to_*()`"

    ```python
    # df: DataFrame
    # write to .excel file
    df.to_excel("data.xlsx", sheet_name="sheet1", index=False)

    # write to .sqlite file
    import sqlite3
    connect = sqlite3.connect("/path/to/database/data.sqlite")
    df.to_sql("table_name", connect, if_exists="replace", index=False)
    connect.close
    ```
