# pmpl - Pretty Matplotlib

**Create presentation-ready plots with minimal effort.**

`pmpl` (Pretty Matplotlib) is a Python library that provides clean, consistent styling for matplotlib plots. Perfect for creating client-ready visualizations in Jupyter notebooks with just a few lines of code.

## Features

- 🎨 **Pre-configured styles** for common plot types (horizontal, vertical, base)
- 🔄 **Context managers** for temporary style application
- 🎯 **Direct formatters** for fine-grained control
- 📊 **Presentation-ready** defaults optimized for clarity
- 🔧 **Extensible** - easy to add custom styles
- ⚡ **Lightweight** - minimal dependencies

## Installation

```bash
pip install pmpl
```

Or with uv:
```bash
uv add pmpl
```

## Quick Start

### Using Context Managers

Perfect for applying styles temporarily:

```python
import pmpl
import matplotlib.pyplot as plt

# Horizontal plots (e.g., bar charts)
with pmpl.style('horizontal'):
    fig, ax = plt.subplots()
    ax.barh(['Product A', 'Product B', 'Product C'], [23, 45, 67])
    ax.set_xlabel('Sales ($M)')
    plt.show()

# Vertical plots (e.g., line charts)
with pmpl.style('vertical'):
    fig, ax = plt.subplots()
    ax.plot([1, 2, 3, 4], [10, 25, 30, 45])
    ax.set_ylabel('Revenue ($M)')
    plt.show()
```

### Using Direct Formatters

Apply formatting to existing axes:

```python
import pmpl
import matplotlib.pyplot as plt

fig, ax = plt.subplots()
ax.barh(['Q1', 'Q2', 'Q3', 'Q4'], [100, 120, 140, 160])

# Format after plot creation
pmpl.format_horizontal(ax)
plt.show()
```

### Setting Global Defaults

Apply a style for the entire session:

```python
import pmpl

# All subsequent plots will use vertical style
pmpl.set_defaults('vertical')
```

## Available Styles

### `horizontal`
- Shows **left spine** only
- **Vertical gridlines** (for x-axis)
- Perfect for: horizontal bar charts, horizontal plots

### `vertical`
- Shows **bottom spine** only
- **Horizontal gridlines** (for y-axis)
- Perfect for: line charts, vertical bar charts, scatter plots

### `base`
- **No spines**
- Customizable gridlines
- Perfect for: minimal plots, custom layouts

## Style Features

All styles include presentation-ready defaults:
- Clean Arial font
- Optimized DPI (95) for screen display
- Subtle gridlines (30% opacity)
- No tick marks on gridded axes
- Frameless legends
- Titles and labels sized for readability

## Examples

Check out the [examples directory](./examples/) for a complete demo notebook showcasing all features.

## Advanced Usage

### Custom Overrides

```python
# Override specific parameters
with pmpl.style('vertical', **{'figure.dpi': 150, 'grid.alpha': 0.5}):
    fig, ax = plt.subplots()
    ax.plot(data)
```

### Formatter Options

```python
# Customize grid appearance
pmpl.format_vertical(ax, grid=True, grid_alpha=0.2)

# Disable grid
pmpl.format_horizontal(ax, grid=False)

# Base formatter with custom grid axis
pmpl.format_base(ax, grid_axis='both')
```

### Accessing Style Dictionaries

For advanced users who want to customize or create new styles:

```python
import pmpl

# View available styles
print(pmpl.STYLES.keys())  # ['base', 'horizontal', 'vertical']

# Access style parameters
base_params = pmpl.BASE_STYLE
horizontal_params = pmpl.HORIZONTAL_STYLE
```

## Requirements

- Python ≥ 3.12
- matplotlib ≥ 3.10.8

## Development

This project uses:
- [uv](https://github.com/astral-sh/uv) for dependency management
- [ruff](https://github.com/astral-sh/ruff) for linting and formatting
- [pre-commit](https://pre-commit.com/) for code quality checks
- [semantic-release](https://python-semantic-release.readthedocs.io/) for versioning

```bash
# Clone the repository
git clone https://github.com/RensterMaat/pmpl.git
cd pmpl

# Install with dev dependencies
uv sync

# Install pre-commit hooks
uv run pre-commit install

# Run tests (example notebook)
jupyter lab examples/test_pmpl.ipynb
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

MIT License - see [LICENSE](LICENSE) file for details.

## Credits

Created by [RensterMaat](https://github.com/RensterMaat)

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for version history.
