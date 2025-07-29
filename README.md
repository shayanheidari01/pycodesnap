# PyCodeSnap

[![Python](https://img.shields.io/badge/python-3.7%2B-blue)](https://www.python.org/)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![PyPI](https://img.shields.io/badge/pypi-package-red)](https://pypi.org/)

A Python library to generate beautiful, modern code screenshots with rounded corners, syntax highlighting, and professional styling - similar to VS Code CodeSnap extension.

## 🌟 Features

- **High-Quality Output**: Generate crisp, clear code screenshots with customizable resolution
- **Modern Design**: Rounded corners, soft shadows, and sleek window controls
- **Syntax Highlighting**: Support for 300+ programming languages with multiple themes
- **Customizable Styling**: Adjustable colors, fonts, spacing, and dimensions
- **Professional Appearance**: Clean, minimal design perfect for documentation and presentations
- **Cross-Platform**: Works on Windows, macOS, and Linux

## 📦 Installation

```bash
pip install pycodesnap
```

### Requirements

- Python 3.7+
- Pillow (PIL)
- Pygments

```bash
pip install Pillow Pygments
```

## 🚀 Quick Start

```python
from pycodesnap import CodeSnap

# Your code snippet
code = '''
def fibonacci(n: int) -> int:
    """Calculate fibonacci number recursively."""
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

# Example usage
for i in range(10):
    print(f"fibonacci({i}) = {fibonacci(i)}")
'''

# Create beautiful code screenshot
snap = CodeSnap("python", code)
snap.create(
    width=800,
    font_size=16,
    line_numbers=True,
    style="github-dark"
)

# Save the result
snap.save("my_code.png")
```

## 🛠️ Advanced Usage

```python
from pycodesnap import CodeSnap

code = '''
// JavaScript example with modern styling
const fibonacci = (n) => {
    if (n <= 1) return n;
    return fibonacci(n - 1) + fibonacci(n - 2);
};

// Generate sequence
const sequence = Array.from({length: 10}, (_, i) => fibonacci(i));
console.log('Fibonacci sequence:', sequence);
'''

snap = CodeSnap("javascript", code)

# Create high-quality screenshot with custom styling
snap.create(
    width=1000,
    font_size=18,
    line_numbers=True,
    style="monokai",
    background_color="#1e1e1e",
    corner_radius=25,
    shadow=True,
    window_controls=True,
    padding=(40, 30),
    line_number_color="#666666",
    quality_factor=3,
    line_spacing=1.4
)

# Save with maximum quality
snap.save("javascript_code.png", quality=100)
```

## 🎨 Supported Languages

PyCodeSnap supports syntax highlighting for 300+ programming languages including:

- Python, JavaScript, TypeScript
- Java, C, C++, C#, Go, Rust
- HTML, CSS, SCSS, Less
- PHP, Ruby, Swift, Kotlin
- SQL, YAML, JSON, Markdown
- Shell, PowerShell, Dockerfile
- And many more...

## 🎯 Available Themes

- `default` - Standard Pygments theme
- `github-dark` - GitHub dark theme
- `monokai` - Popular dark theme
- `dracula` - Dracula color scheme
- `solarized-dark` - Solarized dark theme
- `solarized-light` - Solarized light theme
- `vim` - Vim editor theme
- `emacs` - Emacs editor theme

## 📐 API Reference

### CodeSnap Class

```python
CodeSnap(language: str, code: str)
```

**Parameters:**
- `language` (str): Programming language identifier
- `code` (str): Code content to render

### Methods

#### `create()`
Generate the code screenshot with specified parameters.

**Parameters:**
- `width` (int): Output image width (default: 1200)
- `font_size` (int): Base font size (default: 16)
- `line_numbers` (bool): Show line numbers (default: True)
- `style` (str): Syntax highlighting theme (default: "github-dark")
- `background_color` (str): Background color in hex (default: "#0d1117")
- `corner_radius` (int): Rounded corner radius (default: 20)
- `shadow` (bool): Add drop shadow (default: True)
- `window_controls` (bool): Show window controls (default: True)
- `padding` (tuple): (horizontal, vertical) padding (default: (30, 25))
- `line_number_color` (str): Line number color (default: "#6e7681")
- `max_height` (int): Maximum image height (default: 3000)
- `quality_factor` (int): Quality multiplier (default: 3)
- `line_spacing` (float): Line spacing multiplier (default: 1.3)
- `dpi` (int): Output resolution (default: 300)

#### `save()`
Save the generated image to file.

**Parameters:**
- `fp` (str/Path): File path
- `format` (str): Image format (default: "PNG")
- `optimize` (bool): Optimize image (default: True)
- `quality` (int): JPEG quality 1-100 (default: 100)
- `compress_level` (int): PNG compression 0-9 (default: 1)

#### `show()`
Display the image using system viewer.

#### `to_bytes()`
Convert image to bytes.

**Parameters:**
- `format` (str): Image format (default: "PNG")
- `optimize` (bool): Optimize image (default: True)
- `quality` (int): JPEG quality (default: 100)

#### `get_line_count()`
Get total number of lines in code.

## 📝 Examples

### Python Code Screenshot

```python
from pycodesnap import CodeSnap

python_code = '''
def quick_sort(arr):
    """Quick sort implementation with type hints."""
    if len(arr) <= 1:
        return arr
    
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    
    return quick_sort(left) + middle + quick_sort(right)

# Test the function
numbers = [64, 34, 25, 12, 22, 11, 90]
sorted_numbers = quick_sort(numbers)
print(f"Original: {numbers}")
print(f"Sorted: {sorted_numbers}")
'''

snap = CodeSnap("python", python_code)
snap.create(width=900, style="github-dark")
snap.save("python_example.png")
```

### Web Development Code

```python
from pycodesnap import CodeSnap

html_css_js = '''
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Modern Web App</title>
    <style>
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }
        
        .card {
            background: white;
            border-radius: 12px;
            box-shadow: 0 8px 32px rgba(0,0,0,0.1);
            padding: 2rem;
            margin: 1rem 0;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="card">
            <h1>Hello, World!</h1>
            <p>This is a modern web application.</p>
        </div>
    </div>
    
    <script>
        // Modern JavaScript with ES6 features
        const greet = (name) => {
            return `Hello, ${name}! Welcome to our app.`;
        };
        
        document.addEventListener('DOMContentLoaded', () => {
            const message = greet('Developer');
            console.log(message);
        });
    </script>
</body>
</html>
'''

# Create separate screenshots for different languages
html_snap = CodeSnap("html", html_css_js)
html_snap.create(width=1100, style="github-dark", line_numbers=True)
html_snap.save("web_code.png")
```

## 🎨 Customization Examples

### Minimal Style

```python
snap.create(
    width=700,
    font_size=14,
    line_numbers=False,
    style="default",
    background_color="#ffffff",
    corner_radius=10,
    shadow=False,
    window_controls=False,
    padding=(20, 15)
)
```

### Dark Theme with High Contrast

```python
snap.create(
    width=900,
    font_size=16,
    line_numbers=True,
    style="monokai",
    background_color="#000000",
    corner_radius=15,
    shadow=True,
    line_number_color="#888888",
    line_spacing=1.5
)
```

### High-Quality Print Ready

```python
snap.create(
    width=1500,
    font_size=18,
    line_numbers=True,
    style="github-dark",
    background_color="#0d1117",
    corner_radius=20,
    shadow=True,
    quality_factor=4,
    dpi=300,
    line_spacing=1.4
)
snap.save("print_ready.png", quality=100)
```

## 📤 Output Formats

Support for multiple image formats:

```python
# PNG (default - lossless)
snap.save("code.png")

# JPEG (compressed - smaller file size)
snap.save("code.jpg", format="JPEG", quality=95)

# WebP (modern format with excellent compression)
snap.save("code.webp", format="WEBP", quality=90)
```

## 🛡️ Error Handling

```python
from pycodesnap import CodeSnap

try:
    snap = CodeSnap("python", "print('Hello World')")
    snap.create()
    snap.save("output.png")
except ValueError as e:
    print(f"Error: {e}")
except Exception as e:
    print(f"Unexpected error: {e}")
```

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [Pygments](https://pygments.org/) - Syntax highlighting engine
- [Pillow](https://python-pillow.org/) - Python Imaging Library
- [VS Code CodeSnap](https://marketplace.visualstudio.com/items?itemName=adpyke.codesnap) - Inspiration for this project

## 📞 Support

If you encounter any issues or have questions, please [open an issue](https://github.com/shayanheidari01/pycodesnap/issues) on GitHub.

---

Made with ❤️ for developers who appreciate beautiful code presentation!
