# 06. Interactive Web Apps: Streamlit 🎈🎨

Streamlit is the fastest way to build and share data apps. It allows you to turn Python scripts into interactive web dashboards in minutes, without knowing HTML, CSS, or JavaScript.

## 1. The Streamlit Magic ✨

You write standard Python, and Streamlit converts it into a UI.
*   `st.write()`: Think of it as a superpowered `print()` that can render tables, charts, and Markdown.
*   `st.sidebar`: Easily add filters and settings to a side navigation bar.

---

## 2. Interactive Widgets 🎛️

Widgets allow users to interact with your AI model in real-time.
- `st.slider()`: For numerical ranges.
- `st.selectbox()`: For categorical choices.
- `st.text_input()`: For text-based queries.
- `st.file_uploader()`: For images, CSVs, or PDFs.

---

## 3. Session State 🧠

Streamlit scripts rerun from top to bottom every time a user interacts. **Session State** lets you store information (like the current login or prediction history) so it persists across reruns.

---

## 🛠️ Essential Snippet (ML Model Explorer)

```python
import streamlit as st
import pandas as pd

st.title("AI Model Dashboard 🤖")

# 1. User Input
user_text = st.text_input("Enter text to analyze:")

# 2. Add a Button
if st.button("Run Prediction"):
    # Mock prediction logic
    st.success(f"Result: The sentiment is Positive!")
    
# 3. Sidebar for settings
threshold = st.sidebar.slider("Confidence Threshold", 0.0, 1.0, 0.5)
```

---

## 🌍 Summary
Streamlit is for **Prototyping**. It is the industry standard for Internal AI Tools and EDA dashboards. If you need a custom UI for your complex AI research in 15 minutes, Streamlit is the answer.
