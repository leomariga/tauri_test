# Tauri + Vue + Python Template

A minimal setup guide for creating desktop applications with Tauri, Vue.js, Vuetify, and Python backend using Poetry and TinyDB.

## 📋 **Prerequisites**

Install these on your system:

1. **Node.js** (v16+) - [Download](https://nodejs.org/)
2. **Rust** - [Install](https://rustup.rs/)
3. **Python** (3.8+) - [Download](https://python.org/)
4. **Poetry** - [Install](https://python-poetry.org/docs/#installation)

### Windows Requirements
```powershell
winget install Microsoft.VisualStudio.2022.BuildTools --override "--wait --quiet --add Microsoft.VisualStudio.Component.Windows11SDK.22000"
```

### Verify Installations
```bash
node --version
rustc --version
python --version
poetry --version
```

## 🚀 **Quick Setup**

### 1. Create Tauri Project
```bash
npm create tauri-app@latest my-app
cd my-app
# Choose: Vue + TypeScript/JavaScript
```

### 2. Install Frontend Dependencies
```bash
npm install
npm install vuetify@latest @mdi/font pinia
npm install @tauri-apps/plugin-dialog @tauri-apps/plugin-shell
```

### 3. Configure Vuetify
Edit `src/main.js` to add Vuetify with dark theme and Material Design icons.

### 4. Setup Python Backend
```bash
mkdir src/python_backend
cd src/python_backend
poetry init --no-interaction --name "my-app-backend" --version "0.1.0"
poetry add tinydb
poetry add --group dev pytest black flake8
touch __init__.py file_handler.py
mkdir tests && touch tests/__init__.py
```

### 5. Configure Tauri for Python
- Add required plugins to `src-tauri/Cargo.toml`
- Create Python command handler in `src-tauri/src/main.rs`
- Configure bundled resources in `src-tauri/tauri.conf.json`

### 6. Create Backend Service
Create `src/services/backendService.js` for frontend-backend communication.

### 7. Basic Python Handler
Create a minimal `file_handler.py` with JSON response handling.

### 8. Test Setup
```bash
# From project root
cd src/python_backend
poetry install
poetry run python file_handler.py test

cd ../..
npm run tauri dev
```

## 📁 **Project Structure**
```
my-app/
├── src/
│   ├── services/backendService.js
│   ├── python_backend/
│   │   ├── pyproject.toml
│   │   ├── file_handler.py
│   │   └── tests/
│   ├── App.vue
│   └── main.js
├── src-tauri/
│   ├── src/main.rs
│   ├── Cargo.toml
│   └── tauri.conf.json
└── package.json
```

## 🛠️ **Development Commands**

### Python Backend
```bash
cd src/python_backend
poetry add package-name        # Add dependency
poetry run pytest             # Run tests
poetry run python file_handler.py test
```

### Frontend
```bash
npm install package-name       # Add dependency
npm run tauri dev             # Development
npm run tauri build           # Production build
```

## 🎉 **Next Steps**

Your minimal Tauri + Vue + Python stack is ready! You can now:
- Add your business logic to `file_handler.py`
- Create Vue components with Vuetify
- Use TinyDB for local data storage
- Build cross-platform desktop apps

This template provides the foundation - expand it based on your specific needs!
