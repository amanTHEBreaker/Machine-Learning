# Pandas

There are two core objects in pandas: the **DataFrame** and the **Series**.

### **DataFrame**

A DataFrame is a table. It contains an array of individual *entries*, each of which has a certain *value*. Each entry corresponds to a row (or *record*) and a *column*.

**Example 1:** 

```python
pd.DataFrame({'Yes': [50, 21], 'No': [131, 2]})
```

**Output**

| Yes | No |
| --- | --- |
| 0 | 50 |
| 1 | 21 |
|  |  |

**Example 2 :**

```python
pd.DataFrame({'Bob': ['I likeytd it.', 'It was awful.'],
              'Sue': ['Pretty good.', 'Bland.']},
             index=['Product A', 'Product B'])
```

**Output :**

|  | Bob | Sue |
| --- | --- | --- |
| Product A | I liked it. | Pretty good. |
| Product B | It was awful. | Bland. |
|  |  |  |

### Series

A Series is, in essence, a single column of a DataFrame. So you can assign row labels to the Series the same way as before, using an `index` parameter. However, a Series does not have a column name, it only has one overall `name`:

```python
pd.Series([30, 35, 40], index=['2015 Sales', '2016 Sales', '2017 Sales'], name='Product A')
```

Outpu :

`2015 Sales    30
2016 Sales    35
2017 Sales    40
Name: Product A, dtype: int64`

## Reading Operations

```python
wine_reviews = pd.read_csv("../input/wine-reviews/winemag-data-130k-v2.csv")
reviews = pd.read_csv("../input/wine-reviews/winemag-data_first150k.csv", index_col=0)
```

## Saving Operations

```python
animals.to_csv("cows_and_goats.csv")
```

## Operations

```python
wine_reviews.shape #  shape attribute to check how large the resulting DataFrame is:
wine_reviews.head() # inlist first 5 rows of the table
wine_reviews.tail() # inlist last 5 rows of the table
```

Getting single Specific columns 

```python
desc = reviews['description']
```

# **Indexing in pandas**

**Getting the Single specific columns only first row**

```python
reviews.description.loc[0]
reviews.description[0]
reviews.description.iloc[0]
```

**Selecting the first 10 values from the `single`column** 

**Getting only specific rows all columns**

```python
sample_reviews = reviews.iloc[[1,2,3,5,8]]
```

**Getting only specific columns and rows**

```python
df = reviews.loc[[0,1,10,100], ['country', 'province', 'region_1','region_2']]
```

**Getting till 100th rows with specific columns**

```python
df = reviews.loc[:99, ['country', 'variety']]
# or 
cols_idx = [0, 11]
df = reviews.iloc[:100, cols_idx]
```

**Condition Based Operations** 

```python
top_oceania_wines = reviews.loc[(reviews.points >= 95) &((reviews.country == "Australia") | (reviews.country == "New Zealand"))]
```