# LLM Context Builder

🚀 **Export any project to a single text file optimized for LLM context**

Transform your entire codebase into clean, LLM-ready context with smart project detection and powerful customization options.

## ⚡ Quick Start

```bash
# Install once, use anywhere
pip install llm-context-builder

# Use in any project directory
cd /path/to/your/project
export_project

# 🎯 Output: ./project_export/PROJECT_NAME_TIMESTAMP.txt
```

## ✨ Features

- 🎯 **Zero Configuration** - Works out of the box in any directory
- 🧠 **LLM-Optimized** - Perfect formatting for AI context windows
- 🔍 **Smart Detection** - Auto-detects React, Python, Node.js, Flutter, Django, and more
- ⚡ **Lightning Fast** - Intelligent file filtering and exclusions
- 🎛 **Incredibly Flexible** - Powerful customization options for any workflow
- 🔤 **Token Counting** - Estimate context size for different LLM models
- 🔒 **Security-Aware** - Automatically excludes sensitive files like `.env`, secrets
- 📊 **Detailed Stats** - See exactly what was processed vs skipped

## 🎬 Demo

```bash
$ cd my-react-app
$ export_project

🚀 LLM Context Builder
📂 Source: /Users/dev/my-react-app
✅ Detected: React project  
📁 Output: ./project_export/my_react_app_20250602_143052.txt
📊 Files: 45 processed, 156 skipped
🔤 Tokens: ~12,500 (fits in GPT-4 context)
✅ Export completed in 0.3s
📁 Ready for LLM context: ./project_export/my_react_app_20250602_143052.txt
```

## 🎯 Smart Project Detection

Automatically detects your project type and applies optimal settings:

| Project Type | Auto-Detects | Includes | Excludes |
|-------------|-------------|----------|----------|
| **React/Vue/Angular** | `package.json`, React imports | `.js`, `.jsx`, `.ts`, `.tsx`, `.vue`, `.html`, `.css` | `node_modules`, `dist`, `build` |
| **Python** | `requirements.txt`, `.py` files | `.py`, `.md`, `.txt`, `.toml`, `.yml` | `__pycache__`, `venv`, `*.pyc` |
| **Node.js** | `package.json`, backend deps | `.js`, `.ts`, `.json`, `.md` | `node_modules`, lock files |
| **Flutter** | `pubspec.yaml` | `.dart`, `.yaml`, `.md` | `build/`, `.dart_tool` |
| **Django** | `manage.py` | `.py`, `.html`, `.css`, `.js` | `migrations/`, `static/` |
| **Documentation** | Multiple `.md` files | `.md`, `.rst`, `.txt`, `.html` | `_site`, `public` |

## 📋 Usage Examples

### Basic Usage
```bash
# Auto-detect and export current directory
export_project

# Export specific directory
export_project /path/to/project

# Use optimal preset for your project type
export_project --preset web      # React, Vue, Angular
export_project --preset python   # Django, Flask, FastAPI
export_project --preset node     # Express, NestJS
export_project --preset mobile   # React Native, Flutter
export_project --preset docs     # Documentation projects
```

### Custom Output
```bash
# Custom output location
export_project -o /custom/path/output.txt

# Disable timestamp in filename
export_project --no-timestamp

# Quiet mode (only output file path)
export_project --quiet
```

## 🎛 Powerful Customization Options

### File Type Control

#### Include Only Specific Extensions
```bash
# Only include source code files
export_project --include-ext .py .js .ts .jsx .tsx

# Documentation only
export_project --include-ext .md .rst .txt

# Configuration files only  
export_project --include-ext .json .yaml .yml .toml .cfg
```

#### Exclude Additional Extensions
```bash
# Exclude log and backup files
export_project --exclude-ext .log .backup .tmp

# Exclude test files
export_project --exclude-ext .test.js .spec.ts

# Exclude images (in addition to defaults)
export_project --exclude-ext .png .jpg .gif .svg
```

### Folder Control

#### Exclude Additional Folders
```bash
# Exclude custom directories
export_project --exclude-folders temp backup archive

# Pattern-based exclusions (supports wildcards)
export_project --exclude-folders "test_*" "backup_*" "old_*"

# Exclude development folders
export_project --exclude-folders coverage cypress e2e
```

### File Pattern Control

#### Exclude Specific Files
```bash
# Exclude temporary and draft files
export_project --exclude-files "*.tmp" "draft_*" "temp_*"

# Exclude test files
export_project --exclude-files "*.test.*" "*.spec.*" "*_test.py"

# Exclude sensitive files
export_project --exclude-files ".env*" "secrets*" "*.key"
```

### Size Control
```bash
# Skip files larger than 100KB
export_project --max-size 100000

# Skip files larger than 1MB  
export_project --max-size 1000000
```

## 🔥 Advanced Examples

### Security-Conscious Export
```bash
# Perfect for sharing code while protecting secrets
export_project \
  --exclude-files ".env*" "secrets*" "*.key" "*.pem" "credentials*" \
  --exclude-folders "secrets" "credentials" "private" \
  --exclude-ext .env
```

### Research/Analysis Export
```bash
# Source code only for analysis
export_project \
  --include-ext .py .js .java .cpp .c .h .go .rs \
  --exclude-folders "tests" "examples" "docs" \
  --max-size 50000
```

### Frontend Development Export
```bash
# React project excluding tests and builds
export_project --preset web \
  --exclude-folders "coverage" "cypress" "storybook-static" \
  --exclude-files "*.test.js" "*.spec.ts" "*.stories.js"
```

### Backend API Export  
```bash
# Python API with minimal files
export_project --preset python \
  --exclude-folders "migrations" "static" "media" "celerybeat-schedule" \
  --exclude-files "*.pyc" "local_settings.py" "*.log"
```

### Documentation Writer's Export
```bash
# Docs and configuration only
export_project \
  --include-ext .md .rst .txt .json .yaml .yml \
  --exclude-folders "_drafts" "old_docs" "archive" \
  --exclude-files "draft_*" "TODO.md"
```

### Minimal Export for Large Projects
```bash
# Essential files only
export_project --preset minimal \
  --include-ext .py .js .md .json \
  --max-size 25000 \
  --exclude-folders "vendor" "examples"
```

### Ultimate Custom Export
```bash
# Combine everything for maximum control
export_project \
  --preset python \
  --include-ext .py .md .yml .toml \
  --exclude-folders "migrations" "static" "test_*" \
  --exclude-files "*.pyc" "local_*" "secret_*" \
  --exclude-ext .log .tmp \
  --max-size 100000 \
  --count-tokens
```

## 🔤 Token Counting & LLM Context Planning

```bash
# Estimate tokens for context planning
export_project --count-tokens

# Example outputs:
# 🔤 Tokens: ~8,342 (fits in GPT-4 context)
# 🔤 Tokens: ~32,150 (fits in GPT-4-32k context)  
# 🔤 Tokens: ~95,230 (fits in GPT-4-turbo context)
# ⚠️  Tokens: ~180,500 (exceeds most model limits)
```

## 🎨 Pattern Matching

Supports powerful wildcard patterns:

```bash
# Wildcards
export_project --exclude-folders "test_*" "*_backup" "temp?"

# Multiple patterns
export_project --exclude-files "*.test.*" "*.spec.*" "draft_*" "old_*"

# Case-insensitive matching (automatic)
export_project --exclude-folders "TEST_*" "Test_*" "test_*"  # All work
```

## 📊 Presets Reference

```bash
# List all available presets
export_project --list-presets

# Available presets:
web        - React, Vue, Angular, HTML/CSS/JS projects
python     - Python packages, Django, Flask, FastAPI projects  
node       - Node.js, npm packages, backend projects
mobile     - React Native, Flutter, mobile app projects
docs       - Documentation, blog, content projects
minimal    - Only essential text files
full       - Include everything (use with caution)
```

## 🔒 Default Security Exclusions

Automatically excludes sensitive files:

- **Environment files**: `.env`, `.env.*`, `*.env`
- **Secrets**: `secrets*`, `*.key`, `*.pem`, `credentials*`
- **Lock files**: `package-lock.json`, `yarn.lock`, `Pipfile.lock`
- **Build artifacts**: `dist/`, `build/`, `__pycache__/`, `node_modules/`
- **Version control**: `.git/`, `.svn/`
- **IDE files**: `.vscode/`, `.idea/`
- **OS files**: `.DS_Store`, `Thumbs.db`
- **Logs**: `*.log`, `*.logs`

## 🚀 Installation

```bash
# Install globally
pip install llm-context-builder

# Or install with token counting support
pip install llm-context-builder[tokens]

# Development installation
git clone https://github.com/tanhanwei/llm-context-builder.git
cd llm-context-builder
pip install -e .
```

## 📁 Output Format

Creates clean, LLM-optimized files:

```
====================================================================================================
LLM CONTEXT EXPORT
====================================================================================================
Generated: 2025-06-02 14:30:52
Source: /Users/dev/my-project
Preset: Web Project
Export Tool: llm-context-builder
====================================================================================================

INSTRUCTIONS FOR LLM:
This file contains the complete source code and documentation for a project.
Each file is clearly marked with headers and footers.
Use this context to understand the project structure and help with development tasks.
====================================================================================================

================================================================================
FILE: src/App.jsx
PATH: /Users/dev/my-project/src/App.jsx
SIZE: 1,234 bytes
================================================================================
import React from 'react';
// ... file content here ...
================================================================================
END: src/App.jsx
================================================================================
```

## 🎯 Perfect For

- 📋 **Code Reviews** - Give AI complete project context
- 🐛 **Debugging** - Share entire codebase with AI assistants  
- 📚 **Documentation** - Generate comprehensive project summaries
- 🔄 **Refactoring** - AI-assisted code improvements
- 🎓 **Learning** - Understand unfamiliar codebases quickly
- 🤖 **AI Training** - Prepare datasets for model training
- 👥 **Team Onboarding** - Help new developers understand projects
- 📝 **Technical Writing** - Extract code examples and documentation

## 🛠 Troubleshooting

### Common Issues

#### Command Not Found
```bash
# If 'export_project' not found, try:
python -m llm_context_builder.main --help

# Or reinstall:
pip uninstall llm-context-builder
pip install llm-context-builder
```

#### Large Projects
```bash
# For very large projects, use size limits:
export_project --max-size 50000 --preset minimal

# Or include only essential files:
export_project --include-ext .py .md .json
```

#### Token Limits
```bash
# If output exceeds model limits, try:
export_project --preset minimal --max-size 25000
export_project --include-ext .py .js --exclude-folders tests examples
```

## 📈 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Make your changes and add tests
4. Submit a pull request

### Ideas for Contributions

- Additional project type detection (Go, Rust, Java, etc.)
- Custom preset configurations
- Integration with popular IDEs
- GitHub Action for automated exports
- Web interface for drag-and-drop exports

## 📜 License

MIT License - see [LICENSE](LICENSE) file for details.

## ⭐ Star Us!

If this tool saves you time, please give us a star! It helps others discover the project.

[![GitHub stars](https://img.shields.io/github/stars/tanhanwei/llm-context-builder?style=social)](https://github.com/tanhanwei/llm-context-builder)

## 🌟 Sponsors

Support this project:

[![Buy Me A Coffee](https://img.shields.io/badge/Buy%20Me%20A%20Coffee-ffdd00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/tanhanwei)

---

**Built with ❤️ for the AI development community**