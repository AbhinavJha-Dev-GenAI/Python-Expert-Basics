# Pandas Manipulation & Performance 🐼

Pandas is the workhorse of ETL (Extract, Transform, Load) in Python.

## 1. Indexing & Multi-Indexing
Indices are the "labels" of your data.
- **`.loc`**: Label-based indexing.
- **`.iloc`**: Integer-position-based indexing.
- **MultiIndex**: Hierarchical indexing for high-dimensional data in 2D.

```python
df.set_index(['year', 'month'], inplace=True)
# Access data for Jan 2023
df.loc[(2023, 1)]
```

## 2. GroupBy: Split-Apply-Combine
The most powerful tool for data aggregation.
```python
# Complex aggregation
df.groupby('category').agg({
    'price': ['mean', 'std'],
    'quantity': 'sum'
})
```

## 3. Reshaping Data
- **`pivot_table`**: Similar to Excel pivot tables.
- **`melt`**: "Unpivoting" from wide layout to long layout.
- **`stack` / `unstack`**: Moving index levels to columns and vice versa.

## 4. Handling Time Series
Pandas has exceptional support for dates.
```python
df['date'] = pd.to_datetime(df['date'])
df.resample('M', on='date').sum() # Monthly aggregation
```

## 5. Performance Optimization ⚡
- **Vectorization**: Avoid `.iterrows()` at all costs. Use `.apply()` only if necessary. Vectorized NumPy-based operations are fastest.
- **Categorical Data**: Convert low-cardinality strings to `category` type to save significant memory.
```python
df['category'] = df['category'].astype('category')
```
- **Chunking**: Use `chunksize` in `pd.read_csv()` for massive datasets that don't fit in RAM.
