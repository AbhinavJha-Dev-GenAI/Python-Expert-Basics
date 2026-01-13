# Project 2: Interactive Data Explorer 📊

Create a Streamlit dashboard that allows users to perform EDA (Exploratory Data Analysis) visually.

## 1. Objectives
- Allow users to upload CSV/Excel files.
- Display summary statistics.
- Generate dynamic charts (Histograms, Scatters, Correlations).
- Filter data interactively based on user-selected columns.

## 2. Implementation Steps

### Step 1: File Uploader
```python
import streamlit as st
import pandas as pd

uploaded_file = st.file_uploader("Choose a CSV file", type="csv")
if uploaded_file:
    df = pd.read_csv(uploaded_file)
    st.write(df.head())
```

### Step 2: Dynamic Filters
```python
target_col = st.sidebar.selectbox("Select Target Column", df.columns)
filter_val = st.sidebar.slider("Min Value", float(df[target_col].min()), float(df[target_col].max()))
filtered_df = df[df[target_col] >= filter_val]
```

### Step 3: Visualization
```python
import seaborn as sns
import matplotlib.pyplot as plt

fig, ax = plt.subplots()
sns.histplot(filtered_df[target_col], ax=ax)
st.pyplot(fig)
```

## 3. Pro Tips
- Use `@st.cache_data` for the CSV loading function.
- Add a "Download filtered data" button using `st.download_button`.
- Use `st.columns` to display multiple metrics (Mean, Median, Std) in a single row.
