# Building AI Dashboards 🤖

Tips and tricks for creating professional-grade AI dashboards with Streamlit.

## 1. Structure of an AI App
A typical Streamlit AI app follows this flow:
1. **Config**: Set page title, layout (wide/centered), and icons.
2. **Model Loading**: Use `@st.cache_resource` to load the model once.
3. **Sidebar**: User inputs (hyperparameters, file uploads, sliders).
4. **Main Panel**: Visualization and prediction outputs.

## 2. Handling File Uploads
Streamlit simplifies file input significantly.
```python
uploaded_file = st.file_uploader("Upload Image", type=["jpg", "png"])
if uploaded_file:
    image = Image.open(uploaded_file)
    st.image(image, caption="Uploaded Image")
```

## 3. Dynamic Progress UI
- **`st.spinner`**: Displays a message while background work happens.
- **`st.progress`**: A visual progress bar.
- **`st.status`**: (New in 1.24+) For grouping multiple background steps.

```python
with st.status("Analyzing...") as status:
    st.write("Preprocessing data...")
    time.sleep(1)
    st.write("Running AI model...")
    time.sleep(2)
    status.update(label="Complete!", state="complete")
```

## 4. Advanced Visualization
Integrate libraries like **Plotly** or **Altair** for interactive charts that allow users to zoom and hover over data points.
```python
import plotly.express as px
fig = px.scatter(df, x='gdp', y='life_exp')
st.plotly_chart(fig)
```

## 5. Security for AI Apps
- Use `st.secrets` to hide API keys (e.g., OpenAI, HuggingFace).
- Never display raw database credentials on the screen.
- Sanitize user inputs if you are using them in prompts (SQL injection but for LLMs).
