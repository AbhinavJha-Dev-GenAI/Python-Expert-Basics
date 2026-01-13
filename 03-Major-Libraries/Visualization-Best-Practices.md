# Visualization Best Practices 📊

Good visualization is about storytelling. Matplotlib and Seaborn are your tools.

## 1. The Matplotlib Hierarchy
- **Figure**: The overall window/page.
- **Axes**: The actual plot/chart area.
- **Axis**: The x/y lines and ticks.

```python
fig, ax = plt.subplots(figsize=(10, 6))
ax.plot(x, y)
ax.set_title("Professional Title")
```

## 2. Seaborn: Statistical Viz
Seaborn simplifies complex plots and handles Pandas DataFrames natively.
- **`sns.relplot`**: Relationships (scatter, line).
- **`sns.catplot`**: Categorical (bar, box, violin).
- **`sns.heatmap`**: Correlation matrices.

## 3. Design Principles
- **Color Palettes**: Use `sns.set_palette` or dedicated palettes like `viridis` or `rocket`.
- **Theme**: Use `sns.set_theme(style="whitegrid")` for a cleaner look.
- **Clutter**: Remove unnecessary borders (spines) using `sns.despine()`.

## 4. Interactive Alternatives
While Matplotlib/Seaborn produce static images, consider these for dashboards:
- **Plotly**: For zooming and hover effects.
- **Altair**: Declarative statistical visualization.

## 5. Exporting for Publication
Always use high DPI for saving plots.
```python
plt.savefig('plot.png', dpi=300, bbox_inches='tight')
```
