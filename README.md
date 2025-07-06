<p align="center">
  <a href="https://github.com/BSakura-Miku/clean-jpg-cleaner/stargazers">
    <img src="https://img.shields.io/github/stars/BSakura-Miku/clean-jpg-cleaner?style=social" alt="GitHub stars">
  </a>
  <a href="https://github.com/BSakura-Miku/clean-jpg-cleaner/blob/main/LICENSE">
    <img src="https://img.shields.io/github/license/BSakura-Miku/clean-jpg-cleaner" alt="License">
  </a>
  <img src="https://img.shields.io/badge/language-shell-green.svg" alt="Language">
  <img src="https://img.shields.io/badge/status-active-brightgreen" alt="Status">
</p>

---
# 🧹 clean-jpg-cleaner (Python version)

一个 **跨平台** 的命令行工具，用于自动清理重复的 `.jpg` 或 `.jpeg` 文件（如果有相同主文件存在，如 `.cr2` / `.nef` 等）。支持 dry-run 模拟、废纸篓删除、多线程加速、日志记录等功能。

---

## ✨ 功能亮点

- 🔍 自动检测重复 JPG 文件（与非 JPG 同名）
- 🗑️ 可选择 **移入废纸篓** 或 **永久删除**
- 🤖 `--dry-run`：仅显示将要删除的文件，不实际执行删除
- 📝 日志记录所有删除文件（含时间戳）
- ⚡ 并发处理（多线程加速）

---

## 📦 安装依赖

本工具依赖 Python 3.7+，并需要安装一个跨平台的“废纸篓”库：

```bash
pip install send2trash
```

---

## 🚀 使用方式

```bash
python3 clean_jpg_cleaner.py [目标目录] [参数...]
```

### 📌 参数说明：

| 参数             | 说明 |
|------------------|------|
| `[目标目录]`      | 要清理的目标文件夹，默认当前目录 `.` |
| `--dry-run`       | 不实际删除，仅预览将删除哪些 `.jpg` 文件 |
| `--force`         | 永久删除文件，不移动到废纸篓 |
| `--log <路径>`    | 指定日志文件名（默认自动生成） |
| `--threads <数量>`| 设置并发线程数（默认 4） |

---

## 🧪 示例

```bash
# 只预览不删除
python3 clean_jpg_cleaner.py /Volumes/Drive/Pictures --dry-run

# 移入废纸篓（默认）
python3 clean_jpg_cleaner.py ~/Photos

# 永久删除且使用 8 个线程处理
python3 clean_jpg_cleaner.py ~/DCIM --force --threads 8
```

---

## 📝 日志输出

脚本默认将所有被删除（或预期删除）的 `.jpg/.jpeg` 文件记录在日志文件中，如：

```
clean_jpg_log_2021-05-12.txt
```

---

## 🧾 删除逻辑

对于目录中每个 `.jpg` 或 `.jpeg` 文件：

1. 提取文件名（不含扩展名）
2. 检查是否存在同名但非 `.jpg/.jpeg` 的主文件（如 `.cr2`, `.arw`, `.dng` 等）
3. 若有，认定为重复，执行删除操作（可选废纸篓 / 永久 / dry-run）

---

## ✅ 兼容系统

- ✅ macOS (10.14+)
- ✅ Windows (10+)
- ✅ Linux / WSL

---

## 📄 License

MIT License © 2025 [BSakura-Miku](https://github.com/BSakura-Miku)

欢迎 PR / Issue 反馈与改进建议 ⭐️
