
# PyExecutable

A lightweight, configurable **PyInstaller wrapper** for Python developers who want to package their scripts into standalone executables using Python code instead of CLI.

> Part of the Anvil Desktop Project  (unofficial)  
> Author: [its-me-abi](https://github.com/its-me-abi)  
> Date: May 14, 2025

---

## 📦 What is this?

`pyexecutable.py` provides a `builder` class to programmatically invoke PyInstaller with custom configurations,  
by doing it we can turn a python script into a executable file   
supporting:

- One-file / one-dir builds
- Hidden imports
- Data folder mapping
- Custom icons and console toggling
- Clean builds and custom PyInstaller flags

---
## 🤝 Documentation
[https://github.com/its-me-abi/pyexecutable/blob/main/documentation.md](https://github.com/its-me-abi/pyexecutable)  
## 🛠 Installation

Install PyInstaller if not already installed:

```bash
pip install pyinstaller
```
download this project by git comand (or download by browser as zip and extract )
```
git clone https://github.com/its-me-abi/pyexecutable.git
```

---

## 🚀 Quick Start

```python
from pyexecutable import builder

b = builder("your_script.py")
b.set_console(False)
b.set_onedir(True)
b.set_icon("icon.ico")
b.set_loglevel("DEBUG")
b.set_data_folders("assets", "assets")
b.set_hidden_import("your_dynamic_module")

if b.build_executable():
    print("✅ Build succeeded!")
else:
    print("❌ Build failed.")
```

---

## 🔧 Features

- ✅ No CLI required
- 📂 Cross-platform data folder support
- 🪄 Hidden import handling
- 🖼 Set icon with `.ico` file
- 🧵 Toggle between GUI and console mode
- 🔍 Control build verbosity via log levels
- 🧹 Optional clean builds

---

## 📂 Project Structure

```
pyexecutable/
├── pyexecutable.py        # Main module
├── README.md              # This file
├── documentation.md       # Full API documentation
```

---

## 🤝 Contributing

Contributions are welcome! Please fork and submit a pull request on [GitHub](https://github.com/its-me-abi/pyexecutable).

---

## 🪪 License

MIT License – See `LICENSE.md` for details.
