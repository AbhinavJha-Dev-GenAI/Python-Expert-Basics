# State and Caching 💾

Because Streamlit reruns the script on every interaction, you need a way to persist data and avoid redundant computations.

## 1. Session State (`st.session_state`)
Session State is a dictionary-like object that persists throughout the session. Use it to keep track of user selections, login status, or multi-step workflow progress.

```python
import streamlit as st

if 'authenticated' not in st.session_state:
    st.session_state.authenticated = False

if st.button('Login'):
    st.session_state.authenticated = True

if st.session_state.authenticated:
    st.success("Welcome back!")
```

## 2. Caching: `@st.cache_data`
Use this for functions that load or compute data.
- **Behavior**: Streamlit stores the result. If the function is called with the same arguments again, it returns the cached result instantaneously.
- **Use Case**: `pd.read_csv`, complex queries, heavy data cleaning.

```python
@st.cache_data
def get_huge_data():
    return pd.read_csv("heavy.csv")
```

## 3. Caching: `@st.cache_resource`
Use this for global "resources" that should be initialized only once and shared across the app.
- **Use Case**: Database connections, Machine Learning models (PyTorch/TensorFlow).

```python
@st.cache_resource
def load_llm():
    return load_heavy_model_from_disk()
```

## 4. Cache Clearing
You can clear the cache manually via the Streamlit UI (top right menu) or programmatically via `st.cache_data.clear()`.

## 5. Input Mutation Check
Streamlit caches are "smart". If the source file or the code inside the cached function changes, the cache is automatically invalidated.
