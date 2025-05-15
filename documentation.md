
# pyexecutable.py

A programmatic PyInstaller wrapper for building standalone Python executables with flexible options.

> Part of the Anvil Desktop Project  
> Author: [github.com/its-me-abi](https://github.com/its-me-abi)  
> Date: May 14, 2025

---

## 📌 Overview

The `builder` class provides a Pythonic interface for configuring and invoking PyInstaller builds. 
This simplifies packaging Python scripts into executables while supporting advanced features like:
- Hidden imports
- Data folder inclusion
- Onefile or onedir modes
- Logging and console behavior
- Custom build paths

---

## 🧱 Class: `builder`

### Constructor

```python
builder(script_path, dist_path="./dist", build_path="./build")
```

- **script_path**: Path to your main Python script.
- **dist_path**: Output directory for the built executable.
- **build_path**: Directory for intermediate build artifacts.

---

## 🔧 Configuration Methods

### `set_confirm(val: bool)`
- Enables or disables the `--noconfirm` flag.

### `set_console(val: bool)`
- Set whether the application runs with a console window (`True`) or as a GUI app (`False`).

### `set_icon(val: str)`
- Specify a `.ico` file to use as the application icon.

### `set_onedir(val: bool)`
- `True` for one-directory mode (`--onedir`), `False` for one-file mode (`--onefile`).

### `set_loglevel(val: str)`
- Set PyInstaller log level (`INFO`, `DEBUG`, `ERROR`, etc.).

### `set_clean(val: bool)`
- Include `--clean` flag to remove previous build cache.

### `setr_extra_args(args: list[str])`
- Append additional raw arguments to the PyInstaller command.

### `set_data_folders(src: str, dest: str)`
- Map data folders to bundle into the executable.  
  The `src` is the local path, `dest` is the target path within the package.

### `set_hidden_import(name: str)`
- Add a module name for PyInstaller to include via `--hidden-import`.

---

## 🔍 Internal Helpers

### `get_data_folders() -> list[str]`
- Returns properly formatted `--add-data` strings for all registered folders.

### `get_hidden_Import() -> list[str]`
- Returns all `--hidden-import` entries.

### `get_logLevel() -> list[str]`
- Returns `--log-level=<level>`

---

## 🧮 PyInstaller Command

### `get_full_command_list() -> list[str]`
- Constructs the full list of arguments to pass to PyInstaller, including:
  - Script path
  - Build and dist paths
  - Data folders
  - Hidden imports
  - Logging level
  - Execution mode (console/no-console, onefile/onedir)
  - Icon (if provided)
  - Extra args
  - Confirm behavior

---

## 🚀 Build Method

### `build_executable() -> bool`
- Runs PyInstaller with the assembled argument list.
- Returns `True` on success; logs warning and returns `False` on failure.

---

## ✅ Example Usage

```python
from pyexecutable import builder

b = builder("main.py")
b.set_console(False)
b.set_onedir(False)
b.set_icon("icon.ico")
b.set_loglevel("DEBUG")
b.set_hidden_import("some_dynamic_module")
b.set_data_folders("assets", "assets")
b.set_clean(True)

if b.build_executable():
    print("Build completed successfully.")
else:
    print("Build failed.")
```

---

## 🧠 Notes

- Avoid using the same folder for both hidden imports and data folders.
- Use `logging.basicConfig(level=logging.INFO)` in your main script to see logs.

---

## 📂 Output Layout

| Artifact      | Path              |
|---------------|-------------------|
| Executable    | `./dist/`         |
| Build Cache   | `./build/`        |
| Data Folders  | Bundled as assets |

---

## 🪪 License

MIT License – See LICENSE if available.
