# 🐍 Complete Python Configuration Management Guide

> *Master Python project configuration with interactive examples and visual ASCII art*

```ascii
┌─────────────────────────────────────────────────────────────┐
│  🐍 PYTHON CONFIG MANAGEMENT MASTERY 🐍                     │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐          │
│  │ pyproject   │  │   .env      │  │   config    │          │
│  │   .toml     │  │   files     │  │   .ini      │          │
│  └─────────────┘  └─────────────┘  └─────────────┘          │
│         │                │               │                  │
│         └────────────────┼───────────────┘                  │
│                          │                                  │
│              ┌─────────────────────┐                        │
│              │  Configuration      │                        │
│              │    Ecosystem        │                        │
│              └─────────────────────┘                        │
└─────────────────────────────────────────────────────────────┘
```

---

## 📚 Table of Contents

- [🚀 Introduction to Python Configuration](#-introduction-to-python-configuration)
- [🏗️ Project Structure Visualization](#️-project-structure-visualization)
- [📋 pyproject.toml Deep Dive](#-pyprojecttoml-deep-dive)
- [🔧 Configuration File Formats Comparison](#-configuration-file-formats-comparison)
- [🌐 Environment Variables Management](#-environment-variables-management)
- [💡 Best Practices & Patterns](#-best-practices--patterns)
- [🎯 Real-World Examples](#-real-world-examples)
- [🔗 Interactive Code Snippets](#-interactive-code-snippets)

---

## 🚀 Introduction to Python Configuration

Configuration management is the backbone of robust Python applications. It enables us to separate code from settings, manage different environments, and maintain security best practices.

```ascii
Configuration Management Flow:

┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│Development  │───▶│   Config    │───▶│ Application │───▶│ Production  │
│Environment  │    │   Files     │    │    Code     │    │Environment  │
└─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘
       │                   │                   │                   │
       ▼                   ▼                   ▼                   ▼
   Local .env         pyproject.toml      os.environ         Server env
```

### 🎯 Why Configuration Matters

- **🔒 Security**: Keep sensitive data out of source code
- **🌍 Portability**: Run the same code across different environments
- **🔄 Flexibility**: Change behavior without code modifications
- **📦 Packaging**: Define project metadata and dependencies
- **🛠️ Tool Integration**: Configure linters, formatters, and build tools

---

## 🏗️ Project Structure Visualization

```ascii
Modern Python Project Structure:

my-awesome-project/
├── 📁 src/
│   └── 📁 my_awesome_project/
│       ├── 🐍 __init__.py
│       ├── 🐍 main.py
│       └── 🐍 config.py
├── 📁 tests/
│   ├── 🐍 test_main.py
│   └── 🐍 conftest.py
├── 📁 docs/
│   └── 📄 README.md
├── ⚙️  pyproject.toml      ← Main configuration
├── 🌐 .env                 ← Environment variables
├── 🔧 .env.example         ← Template for .env
├── ⚙️  .gitignore
├── 📄 LICENSE
└── 📄 README.md

Configuration Files Priority:
┌─────────────┐ 1st  ┌─────────────┐ 2nd  ┌─────────────┐ 3rd
│ Environment │ ───▶ │pyproject.toml│ ───▶│Default Values│
│ Variables   │      │   config    │     │  in Code     │
└─────────────┘      └─────────────┘     └─────────────┘
```

---

## 📋 pyproject.toml Deep Dive

The `pyproject.toml` file is the modern standard for Python project configuration, introduced by PEP 518 and enhanced by PEP 621.

### 🔧 Core Structure

```ascii
pyproject.toml Architecture:

┌─────────────────────────────────────────────────────────────┐
│                    pyproject.toml                           │
├─────────────────────────────────────────────────────────────┤
│ [build-system]          ← 🏗️  Build configuration           │
│ ├── requires = [...]    ← 📦 Build dependencies             │
│ └── build-backend       ← 🔧 Build tool specification       │
├─────────────────────────────────────────────────────────────┤
│ [project]               ← 📊 Project metadata               │
│ ├── name                ← 🏷️  Project name                  │
│ ├── version             ← 🔢 Version number                 │
│ ├── dependencies        ← 📦 Runtime dependencies           │
│ └── optional-deps       ← ⭐ Optional features              │
├─────────────────────────────────────────────────────────────┤
│ [tool.*]                ← 🛠️  Tool-specific config          │
│ ├── [tool.black]        ← ⚫ Code formatter                 │
│ ├── [tool.mypy]         ← 🔍 Type checker                   │
│ └── [tool.pytest]       ← 🧪 Test runner                    |
└─────────────────────────────────────────────────────────────┘

```

### 🏗️ Build System Configuration

```toml
[build-system]
# 🎯 Essential: Always include this section
requires = ["setuptools>=75.0.0", "wheel"]
build-backend = "setuptools.build_meta"

# Alternative build backends:
# requires = ["hatchling>=1.26"]
# build-backend = "hatchling.build"

# requires = ["flit_core>=3.12.0,<4"]
# build-backend = "flit_core.buildapi"

# requires = ["pdm-backend>=2.4.0"]
# build-backend = "pdm.backend"
```

### 📊 Project Metadata

```toml
[project]
# 🏷️ Basic Information
name = "my-awesome-project"
version = "1.0.0"
description = "A fantastic Python project with amazing features"
readme = {file = "README.md", content-type = "text/markdown"}

# 👥 Authors and Maintainers
authors = [
    {name = "Your Name", email = "your.email@example.com"},
    {name = "Co-Author", email = "coauthor@example.com"}
]
maintainers = [
    {name = "Maintainer", email = "maintainer@example.com"}
]

# 🔧 Technical Requirements
requires-python = ">=3.9"
license = {text = "MIT"}

# 🏷️ Classification
keywords = ["python", "configuration", "awesome"]
classifiers = [
    "Development Status :: 4 - Beta",
    "Intended Audience :: Developers",
    "License :: OSI Approved :: MIT License",
    "Programming Language :: Python :: 3",
    "Programming Language :: Python :: 3.9",
    "Programming Language :: Python :: 3.10",
    "Programming Language :: Python :: 3.11",
    "Programming Language :: Python :: 3.12",
]

# 📦 Dependencies
dependencies = [
    "requests>=2.28.0",
    "click>=8.0.0",
    "rich>=12.0.0"
]

# ⭐ Optional Dependencies
[project.optional-dependencies]
dev = [
    "pytest>=7.0.0",
    "black>=22.0.0",
    "mypy>=1.0.0",
    "pre-commit>=2.20.0"
]
docs = [
    "sphinx>=5.0.0",
    "sphinx-rtd-theme>=1.0.0"
]
gui = [
    "tkinter",
    "PyQt6>=6.4.0"
]

# 🔗 URLs
[project.urls]
Homepage = "https://github.com/username/my-awesome-project"
Documentation = "https://my-awesome-project.readthedocs.io"
Repository = "https://github.com/username/my-awesome-project.git"
"Bug Tracker" = "https://github.com/username/my-awesome-project/issues"
Changelog = "https://github.com/username/my-awesome-project/blob/main/CHANGELOG.md"

# 🚀 Scripts and Entry Points
[project.scripts]
my-cli = "my_awesome_project.cli:main"
awesome-tool = "my_awesome_project.tools:run"

[project.gui-scripts]
my-gui = "my_awesome_project.gui:main"
```

### 🛠️ Tool Configuration

```toml
# ⚫ Black Code Formatter
[tool.black]
line-length = 88
target-version = ['py39', 'py310', 'py311', 'py312']
include = '\.pyi?$'
extend-exclude = '''
/(
  # directories
  \.eggs
  | \.git
  | \.hg
  | \.mypy_cache
  | \.tox
  | \.venv
  | build
  | dist
)/
'''

# 🔍 MyPy Type Checker
[tool.mypy]
python_version = "3.9"
warn_return_any = true
warn_unused_configs = true
disallow_untyped_defs = true
disallow_incomplete_defs = true
check_untyped_defs = true
disallow_untyped_decorators = true
no_implicit_optional = true
warn_redundant_casts = true
warn_unused_ignores = true
warn_no_return = true
warn_unreachable = true
strict_equality = true

# 🧪 Pytest Configuration
[tool.pytest.ini_options]
minversion = "7.0"
addopts = "-ra -q --strict-markers --strict-config"
testpaths = ["tests"]
filterwarnings = [
    "error",
    "ignore::UserWarning",
    "ignore::DeprecationWarning",
]
markers = [
    "slow: marks tests as slow (deselect with '-m \"not slow\"')",
    "integration: marks tests as integration tests",
]

# 📦 Coverage
[tool.coverage.run]
source = ["src"]
omit = [
    "*/tests/*",
    "*/test_*",
    "*/__pycache__/*",
    "*/migrations/*",
]

[tool.coverage.report]
exclude_lines = [
    "pragma: no cover",
    "def __repr__",
    "if self.debug:",
    "if settings.DEBUG",
    "raise AssertionError",
    "raise NotImplementedError",
    "if 0:",
    "if __name__ == .__main__.:"
]
```

---

## 🔧 Configuration File Formats Comparison

```ascii
Configuration Formats Landscape:

┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐
│     INI     │  │    JSON     │  │    YAML     │  │    TOML     │  │    .env     │
├─────────────┤  ├─────────────┤  ├─────────────┤  ├─────────────┤  ├─────────────┤
│  Simple     │  │ Structured  │  │Humanfriendly│  │ Modern      │  │ Simple KV   │
│  Readable   │  │ Universal   │  │ Indentation │  │ Structured  │  │ Environment │
│  Limited    │  │ No comments │  │ Complex     │  │ Comments OK │  │ String only │
│  Types      │  │ Verbose     │  │ Ambiguous   │  │ Typed       │  │ Local dev   │
└─────────────┘  └─────────────┘  └─────────────┘  └─────────────┘  └─────────────┘
      ↓                ↓                ↓                ↓                ↓
  Legacy use       API configs     Docker/K8s      pyproject.toml   Environment
```

### 📝 INI Format

```ini
; config.ini - Traditional configuration format
[database]
host = localhost
port = 5432
name = myapp_db
debug = true

[api]
base_url = https://api.example.com
timeout = 30
retries = 3

[logging]
level = INFO
file = /var/log/myapp.log
```

**Python Implementation:**

```python
import configparser
from pathlib import Path

def load_ini_config(file_path: str) -> dict:
    """Load INI configuration file."""
    config = configparser.ConfigParser()
    config.read(file_path)
    
    # Convert to nested dictionary
    config_dict = {}
    for section_name in config.sections():
        config_dict[section_name] = {}
        for key, value in config.items(section_name):
            # Try to convert to appropriate type
            if value.lower() in ('true', 'false'):
                config_dict[section_name][key] = config.getboolean(section_name, key)
            elif value.isdigit():
                config_dict[section_name][key] = config.getint(section_name, key)
            else:
                config_dict[section_name][key] = value
    
    return config_dict

# Usage
config = load_ini_config('config.ini')
print(config['database']['host'])  # localhost
```

### 🔤 JSON Format

```json
{
  "database": {
    "host": "localhost",
    "port": 5432,
    "name": "myapp_db",
    "debug": true
  },
  "api": {
    "base_url": "https://api.example.com",
    "timeout": 30,
    "retries": 3,
    "headers": {
      "User-Agent": "MyApp/1.0",
      "Accept": "application/json"
    }
  },
  "logging": {
    "level": "INFO",
    "file": "/var/log/myapp.log",
    "formatters": ["timestamp", "level", "message"]
  }
}
```

**Python Implementation:**

```python
import json
from pathlib import Path
from typing import Any, Dict

class ConfigManager:
    """JSON Configuration Manager with dot notation access."""
    
    def __init__(self, config_path: str):
        self.config_path = Path(config_path)
        self._config = self._load_config()
    
    def _load_config(self) -> Dict[str, Any]:
        """Load JSON configuration."""
        try:
            with open(self.config_path, 'r', encoding='utf-8') as f:
                return json.load(f)
        except FileNotFoundError:
            print(f"Config file {self.config_path} not found!")
            return {}
        except json.JSONDecodeError as e:
            print(f"Invalid JSON in {self.config_path}: {e}")
            return {}
    
    def get(self, key: str, default: Any = None) -> Any:
        """Get configuration value using dot notation."""
        keys = key.split('.')
        value = self._config
        
        for k in keys:
            if isinstance(value, dict) and k in value:
                value = value[k]
            else:
                return default
        
        return value
    
    def save(self, config_path: str = None) -> None:
        """Save configuration to file."""
        path = config_path or self.config_path
        with open(path, 'w', encoding='utf-8') as f:
            json.dump(self._config, f, indent=2, ensure_ascii=False)

# Usage
config = ConfigManager('config.json')
print(config.get('database.host'))  # localhost
print(config.get('api.headers.User-Agent'))  # MyApp/1.0
```

### 🎯 YAML Format

```yaml
# config.yaml - Human-readable configuration
database:
  host: localhost
  port: 5432
  name: myapp_db
  debug: true
  credentials:
    username: ${DB_USER:-admin}
    password: ${DB_PASSWORD:-secret}

api:
  base_url: https://api.example.com
  timeout: 30
  retries: 3
  headers:
    User-Agent: MyApp/1.0
    Accept: application/json
  endpoints:
    - name: users
      path: /api/v1/users
      methods: [GET, POST]
    - name: posts
      path: /api/v1/posts
      methods: [GET, POST, PUT, DELETE]

logging:
  level: INFO
  file: /var/log/myapp.log
  formatters:
    - timestamp
    - level
    - message
  handlers:
    console:
      level: DEBUG
      format: "%(asctime)s - %(name)s - %(levelname)s - %(message)s"
    file:
      level: INFO
      format: "%(asctime)s [%(levelname)s] %(message)s"
```

**Python Implementation:**

```python
import yaml
import os
import re
from pathlib import Path
from typing import Any, Dict, Union

class YAMLConfig:
    """YAML Configuration Manager with environment variable substitution."""
    
    def __init__(self, config_path: str):
        self.config_path = Path(config_path)
        self._config = self._load_config()
    
    def _load_config(self) -> Dict[str, Any]:
        """Load YAML configuration with environment variable substitution."""
        try:
            with open(self.config_path, 'r', encoding='utf-8') as f:
                content = f.read()
            
            # Substitute environment variables
            content = self._substitute_env_vars(content)
            
            return yaml.safe_load(content)
        except FileNotFoundError:
            print(f"Config file {self.config_path} not found!")
            return {}
        except yaml.YAMLError as e:
            print(f"Invalid YAML in {self.config_path}: {e}")
            return {}
    
    def _substitute_env_vars(self, content: str) -> str:
        """Substitute ${VAR:-default} patterns with environment variables."""
        pattern = r'\$\{([^}^{]+)\}'
        
        def replacer(match):
            var_expr = match.group(1)
            if ':-' in var_expr:
                var_name, default = var_expr.split(':-', 1)
                return os.environ.get(var_name, default)
            else:
                return os.environ.get(var_expr, match.group(0))
        
        return re.sub(pattern, replacer, content)
    
    def get(self, key: str, default: Any = None) -> Any:
        """Get configuration value using dot notation."""
        keys = key.split('.')
        value = self._config
        
        for k in keys:
            if isinstance(value, dict) and k in value:
                value = value[k]
            else:
                return default
        
        return value

# Usage
config = YAMLConfig('config.yaml')
print(config.get('database.host'))  # localhost
print(config.get('api.endpoints.0.name'))  # users
```

### ⭐ TOML Format (Recommended)

```toml
# config.toml - Modern configuration format
title = "MyApp Configuration"

[database]
host = "localhost"
port = 5432
name = "myapp_db"
debug = true

[database.credentials]
username = "admin"
password = "secret"

[api]
base_url = "https://api.example.com"
timeout = 30
retries = 3

[api.headers]
User-Agent = "MyApp/1.0"
Accept = "application/json"

[[api.endpoints]]
name = "users"
path = "/api/v1/users"
methods = ["GET", "POST"]

[[api.endpoints]]
name = "posts"
path = "/api/v1/posts"
methods = ["GET", "POST", "PUT", "DELETE"]

[logging]
level = "INFO"
file = "/var/log/myapp.log"
formatters = ["timestamp", "level", "message"]

[logging.handlers.console]
level = "DEBUG"
format = "%(asctime)s - %(name)s - %(levelname)s - %(message)s"

[logging.handlers.file]
level = "INFO"
format = "%(asctime)s [%(levelname)s] %(message)s"

# Feature flags
[features]
enable_caching = true
max_cache_size = 1000
cache_ttl = 3600  # seconds

# Environment-specific overrides
[environments.development]
debug = true
log_level = "DEBUG"

[environments.production]
debug = false
log_level = "WARNING"
```

**Python Implementation:**

```python
try:
    import tomllib  # Python 3.11+
except ImportError:
    import tomli as tomllib  # For Python < 3.11

import os
from pathlib import Path
from typing import Any, Dict, Optional

class TOMLConfig:
    """TOML Configuration Manager with environment support."""
    
    def __init__(self, config_path: str, environment: Optional[str] = None):
        self.config_path = Path(config_path)
        self.environment = environment or os.getenv('APP_ENV', 'development')
        self._config = self._load_config()
        self._apply_environment_overrides()
    
    def _load_config(self) -> Dict[str, Any]:
        """Load TOML configuration."""
        try:
            with open(self.config_path, 'rb') as f:
                return tomllib.load(f)
        except FileNotFoundError:
            print(f"Config file {self.config_path} not found!")
            return {}
        except tomllib.TOMLDecodeError as e:
            print(f"Invalid TOML in {self.config_path}: {e}")
            return {}
    
    def _apply_environment_overrides(self) -> None:
        """Apply environment-specific configuration overrides."""
        env_config = self._config.get('environments', {}).get(self.environment, {})
        
        for key, value in env_config.items():
            if '.' in key:
                # Handle nested keys
                keys = key.split('.')
                target = self._config
                for k in keys[:-1]:
                    if k not in target:
                        target[k] = {}
                    target = target[k]
                target[keys[-1]] = value
            else:
                # Handle top-level keys - find the appropriate section
                self._merge_config_value(key, value)
    
    def _merge_config_value(self, key: str, value: Any) -> None:
        """Merge a configuration value into the main config."""
        # Try to find which section this key belongs to
        for section_name, section_config in self._config.items():
            if isinstance(section_config, dict) and key in section_config:
                section_config[key] = value
                return
        
        # If not found in any section, add to root
        self._config[key] = value
    
    def get(self, key: str, default: Any = None) -> Any:
        """Get configuration value using dot notation."""
        keys = key.split('.')
        value = self._config
        
        for k in keys:
            if isinstance(value, dict) and k in value:
                value = value[k]
            else:
                return default
        
        return value
    
    def get_section(self, section: str) -> Dict[str, Any]:
        """Get entire configuration section."""
        return self._config.get(section, {})
    
    def validate(self) -> bool:
        """Basic configuration validation."""
        required_sections = ['database', 'api', 'logging']
        
        for section in required_sections:
            if section not in self._config:
                print(f"Missing required section: {section}")
                return False
        
        # Validate database config
        db_config = self._config.get('database', {})
        required_db_keys = ['host', 'port', 'name']
        for key in required_db_keys:
            if key not in db_config:
                print(f"Missing required database key: {key}")
                return False
        
        return True

# Usage
config = TOMLConfig('config.toml', environment='production')
print(config.get('database.host'))  # localhost
print(config.get('api.endpoints.0.name'))  # users
print(config.validate())  # True
```

### 🌐 .env Format

```bash
# .env - Environment variables for local development
# Database Configuration
DB_HOST=localhost
DB_PORT=5432
DB_NAME=myapp_db
DB_USER=admin
DB_PASSWORD=secret_password_123
DB_DEBUG=true

# API Configuration
API_BASE_URL=https://api.example.com
API_TIMEOUT=30
API_RETRIES=3
API_KEY=your_api_key_here

# Application Settings
APP_ENV=development
APP_DEBUG=true
APP_SECRET_KEY=your-super-secret-key-here
APP_LOG_LEVEL=DEBUG

# External Services
REDIS_URL=redis://localhost:6379/0
ELASTICSEARCH_URL=http://localhost:9200
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your-email@gmail.com
SMTP_PASSWORD=your-app-password

# Feature Flags
FEATURE_CACHING=true
FEATURE_ANALYTICS=false
FEATURE_BETA_FEATURES=true

# Security Settings
CORS_ORIGINS=http://localhost:3000,https://yourdomain.com
JWT_SECRET_KEY=jwt-secret-key
JWT_EXPIRY_HOURS=24
```

**Python Implementation:**

```python
import os
from pathlib import Path
from typing import Any, Dict, List, Optional, Union
import re

class EnvConfig:
    """Environment Configuration Manager with type conversion."""
    
    def __init__(self, env_file: Optional[str] = None, auto_load: bool = True):
        self.env_file = Path(env_file) if env_file else Path('.env')
        if auto_load and self.env_file.exists():
            self.load_env_file()
    
    def load_env_file(self) -> None:
        """Load environment variables from .env file."""
        try:
            with open(self.env_file, 'r', encoding='utf-8') as f:
                for line_num, line in enumerate(f, 1):
                    line = line.strip()
                    
                    # Skip empty lines and comments
                    if not line or line.startswith('#'):
                        continue
                    
                    # Parse key=value pairs
                    if '=' in line:
                        key, value = line.split('=', 1)
                        key = key.strip()
                        value = value.strip()
                        
                        # Remove quotes if present
                        value = self._remove_quotes(value)
                        
                        # Set environment variable if not already set
                        if key not in os.environ:
                            os.environ[key] = value
                    else:
                        print(f"Invalid line {line_num} in {self.env_file}: {line}")
        
        except FileNotFoundError:
            print(f"Environment file {self.env_file} not found!")
        except Exception as e:
            print(f"Error loading {self.env_file}: {e}")
    
    def _remove_quotes(self, value: str) -> str:
        """Remove surrounding quotes from value."""
        if len(value) >= 2:
            if (value.startswith('"') and value.endswith('"')) or \
               (value.startswith("'") and value.endswith("'")):
                return value[1:-1]
        return value
    
    def get(self, key: str, default: Any = None, cast: type = str) -> Any:
        """Get environment variable with type casting."""
        value = os.environ.get(key, default)
        
        if value is None:
            return None
        
        # Type casting
        if cast == bool:
            return self._to_bool(value)
        elif cast == int:
            try:
                return int(value)
            except (ValueError, TypeError):
                return default
        elif cast == float:
            try:
                return float(value)
            except (ValueError, TypeError):
                return default
        elif cast == list:
            return self._to_list(value)
        else:
            return str(value)
    
    def _to_bool(self, value: Union[str, bool]) -> bool:
        """Convert string to boolean."""
        if isinstance(value, bool):
            return value
        
        return str(value).lower() in ('true', '1', 'yes', 'on', 'enabled')
    
    def _to_list(self, value: str, separator: str = ',') -> List[str]:
        """Convert string to list."""
        if not value:
            return []
        
        return [item.strip() for item in value.split(separator) if item.strip()]
    
    def get_prefix(self, prefix: str) -> Dict[str, str]:
        """Get all environment variables with a specific prefix."""
        result = {}
        prefix = prefix.upper()
        
        for key, value in os.environ.items():
            if key.startswith(prefix):
                # Remove prefix and convert to lowercase
                clean_key = key[len(prefix):].lstrip('_').lower()
                result[clean_key] = value
        
        return result
    
    def create_template(self, output_file: str = '.env.example') -> None:
        """Create a template .env file from current environment."""
        template_vars = [
            '# Database Configuration',
            'DB_HOST=localhost',
            'DB_PORT=5432',
            'DB_NAME=myapp_db',
            'DB_USER=admin',
            'DB_PASSWORD=change_me',
            '',
            '# API Configuration',
            'API_BASE_URL=https://api.example.com',
            'API_KEY=your_api_key_here',
            '',
            '# Application Settings',
            'APP_ENV=development',
            'APP_DEBUG=true',
            'APP_SECRET_KEY=generate_a_secure_key',
        ]
        
        with open(output_file, 'w', encoding='utf-8') as f:
            f.write('\n'.join(template_vars))
        
        print(f"Created template file: {output_file}")

# Usage
env = EnvConfig('.env')

# Get values with type conversion
db_host = env.get('DB_HOST', 'localhost')
db_port = env.get('DB_PORT', 5432, cast=int)
debug = env.get('APP_DEBUG', False, cast=bool)
cors_origins = env.get('CORS_ORIGINS', [], cast=list)

print(f"Database: {db_host}:{db_port}")
print(f"Debug mode: {debug}")
print(f"CORS origins: {cors_origins}")

# Get all database-related variables
db_config = env.get_prefix('DB_')
print(f"Database config: {db_config}")
```

---

## 🌐 Environment Variables Management

```ascii
Environment Variables Hierarchy:

┌─────────────────────────────────────────────────────────────┐
│                Environment Variables Flow                   │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  System Environment  ──┐                                    │
│       Variables        │                                    │
│                        │                                    │
│  .env File Variables ──┼──▶ Application ──▶ Configuration │
│                        │      Runtime           Object      │
│                        │                                    │
│  Runtime Variables   ──┘                                    │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│  Priority Order: System > Runtime > .env > Defaults         │
└─────────────────────────────────────────────────────────────┘
```

### 🔒 Security Best Practices

```python
from dataclasses import dataclass
from typing import Optional, List, Dict, Any
import os
import secrets
import hashlib

@dataclass
class AppConfig:
    """Type-safe application configuration."""
    
    # Database settings
    db_host: str = "localhost"
    db_port: int = 5432
    db_name: str = "myapp"
    db_user: str = "postgres"
    db_password: str = ""
    
    # API settings
    api_key: str = ""
    api_secret: str = ""
    api_base_url: str = "https://api.example.com"
    
    # Application settings
    debug: bool = False
    secret_key: str = ""
    allowed_hosts: List[str] = None
    
    # Security settings
    jwt_secret: str = ""
    jwt_expiry_hours: int = 24
    password_hash_rounds: int = 12
    
    def __post_init__(self):
        """Validate and process configuration after initialization."""
        self.allowed_hosts = self.allowed_hosts or []
        
        # Generate secret key if not provided
        if not self.secret_key:
            self.secret_key = secrets.token_urlsafe(32)
        
        # Generate JWT secret if not provided
        if not self.jwt_secret:
            self.jwt_secret = secrets.token_urlsafe(64)
        
        # Validate required fields
        self._validate()
    
    def _validate(self) -> None:
        """Validate configuration values."""
        errors = []
        
        if not self.db_password and not self.debug:
            errors.append("Database password is required in production")
        
        if not self.api_key and not self.debug:
            errors.append("API key is required in production")
        
        if self.jwt_expiry_hours < 1:
            errors.append("JWT expiry must be at least 1 hour")
        
        if self.password_hash_rounds < 10:
            errors.append("Password hash rounds should be at least 10")
        
        if errors:
            raise ValueError("Configuration validation failed:\n" + "\n".join(f"- {error}" for error in errors))
    
    @classmethod
    def from_env(cls, env_prefix: str = "APP_") -> "AppConfig":
        """Create configuration from environment variables."""
        def get_env_list(key: str, default: List[str] = None) -> List[str]:
            value = os.getenv(key, "")
            if not value:
                return default or []
            return [item.strip() for item in value.split(",")]
        
        def get_env_bool(key: str, default: bool = False) -> bool:
            return os.getenv(key, str(default)).lower() in ('true', '1', 'yes', 'on')
        
        def get_env_int(key: str, default: int) -> int:
            try:
                return int(os.getenv(key, str(default)))
            except ValueError:
                return default
        
        return cls(
            # Database
            db_host=os.getenv(f"{env_prefix}DB_HOST", "localhost"),
            db_port=get_env_int(f"{env_prefix}DB_PORT", 5432),
            db_name=os.getenv(f"{env_prefix}DB_NAME", "myapp"),
            db_user=os.getenv(f"{env_prefix}DB_USER", "postgres"),
            db_password=os.getenv(f"{env_prefix}DB_PASSWORD", ""),
            
            # API
            api_key=os.getenv(f"{env_prefix}API_KEY", ""),
            api_secret=os.getenv(f"{env_prefix}API_SECRET", ""),
            api_base_url=os.getenv(f"{env_prefix}API_BASE_URL", "https://api.example.com"),
            
            # Application
            debug=get_env_bool(f"{env_prefix}DEBUG", False),
            secret_key=os.getenv(f"{env_prefix}SECRET_KEY", ""),
            allowed_hosts=get_env_list(f"{env_prefix}ALLOWED_HOSTS"),
            
            # Security
            jwt_secret=os.getenv(f"{env_prefix}JWT_SECRET", ""),
            jwt_expiry_hours=get_env_int(f"{env_prefix}JWT_EXPIRY_HOURS", 24),
            password_hash_rounds=get_env_int(f"{env_prefix}PASSWORD_HASH_ROUNDS", 12),
        )
    
    def to_dict(self, hide_secrets: bool = True) -> Dict[str, Any]:
        """Convert configuration to dictionary."""
        config_dict = {}
        secret_keys = {'db_password', 'api_key', 'api_secret', 'secret_key', 'jwt_secret'}
        
        for key, value in self.__dict__.items():
            if hide_secrets and key in secret_keys:
                config_dict[key] = "***HIDDEN***" if value else ""
            else:
                config_dict[key] = value
        
        return config_dict
    
    def get_database_url(self) -> str:
        """Get database connection URL."""
        return f"postgresql://{self.db_user}:{self.db_password}@{self.db_host}:{self.db_port}/{self.db_name}"
    
    def get_redis_url(self, redis_host: str = None, redis_port: int = None) -> str:
        """Get Redis connection URL."""
        host = redis_host or os.getenv("REDIS_HOST", "localhost")
        port = redis_port or int(os.getenv("REDIS_PORT", "6379"))
        return f"redis://{host}:{port}/0"

# Usage example
if __name__ == "__main__":
    # Load configuration from environment
    config = AppConfig.from_env()
    
    print("🔧 Application Configuration:")
    print("=" * 40)
    
    # Print non-sensitive configuration
    for key, value in config.to_dict().items():
        print(f"{key}: {value}")
    
    print("\n🔗 Connection URLs:")
    print(f"Database: {config.get_database_url()}")
    print(f"Redis: {config.get_redis_url()}")
```

---

## 💡 Best Practices & Patterns

```ascii
Configuration Best Practices:

┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   🔒 Security   │    │  🏗️ Structure   │    │ 🔄 Flexibility  │
├─────────────────┤    ├─────────────────┤    ├─────────────────┤
│ No secrets in   │    │ Clear naming    │    │ Environment     │
│ version control │    │ conventions     │    │ overrides       │
├─────────────────┤    ├─────────────────┤    ├─────────────────┤
│ Environment     │    │ Logical         │    │ Feature flags   │
│ variables       │    │ grouping        │    │ support         │
├─────────────────┤    ├─────────────────┤    ├─────────────────┤
│ Encrypted       │    │ Type safety     │    │ Hot reloading   │
│ secrets         │    │ validation      │    │ for dev         │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

### 🎯 Advanced Configuration Patterns

#### 1. Configuration Factory Pattern

```python
from abc import ABC, abstractmethod
from typing import Dict, Any, Type
import os
from pathlib import Path

class ConfigurationProvider(ABC):
    """Abstract base class for configuration providers."""
    
    @abstractmethod
    def load(self) -> Dict[str, Any]:
        """Load configuration from source."""
        pass

class EnvConfigProvider(ConfigurationProvider):
    """Environment variables configuration provider."""
    
    def __init__(self, prefix: str = ""):
        self.prefix = prefix.upper()
    
    def load(self) -> Dict[str, Any]:
        config = {}
        for key, value in os.environ.items():
            if key.startswith(self.prefix):
                clean_key = key[len(self.prefix):].lower().lstrip('_')
                config[clean_key] = value
        return config

class FileConfigProvider(ConfigurationProvider):
    """File-based configuration provider."""
    
    def __init__(self, file_path: str, file_type: str = "auto"):
        self.file_path = Path(file_path)
        self.file_type = file_type
        if file_type == "auto":
            self.file_type = self.file_path.suffix.lstrip('.')
    
    def load(self) -> Dict[str, Any]:
        if not self.file_path.exists():
            return {}
        
        if self.file_type == "json":
            import json
            with open(self.file_path, 'r') as f:
                return json.load(f)
        elif self.file_type == "yaml" or self.file_type == "yml":
            import yaml
            with open(self.file_path, 'r') as f:
                return yaml.safe_load(f) or {}
        elif self.file_type == "toml":
            import tomllib
            with open(self.file_path, 'rb') as f:
                return tomllib.load(f)
        else:
            raise ValueError(f"Unsupported file type: {self.file_type}")

class ConfigurationFactory:
    """Factory for creating and managing configuration."""
    
    def __init__(self):
        self.providers: List[ConfigurationProvider] = []
        self._config: Dict[str, Any] = {}
    
    def add_provider(self, provider: ConfigurationProvider) -> 'ConfigurationFactory':
        """Add a configuration provider."""
        self.providers.append(provider)
        return self
    
    def build(self) -> Dict[str, Any]:
        """Build final configuration by merging all providers."""
        final_config = {}
        
        # Load from all providers in order
        for provider in self.providers:
            provider_config = provider.load()
            final_config = self._deep_merge(final_config, provider_config)
        
        self._config = final_config
        return final_config
    
    def _deep_merge(self, dict1: Dict, dict2: Dict) -> Dict:
        """Deep merge two dictionaries."""
        result = dict1.copy()
        
        for key, value in dict2.items():
            if key in result and isinstance(result[key], dict) and isinstance(value, dict):
                result[key] = self._deep_merge(result[key], value)
            else:
                result[key] = value
        
        return result
    
    def get(self, key: str, default: Any = None) -> Any:
        """Get configuration value using dot notation."""
        if not self._config:
            self.build()
        
        keys = key.split('.')
        value = self._config
        
        for k in keys:
            if isinstance(value, dict) and k in value:
                value = value[k]
            else:
                return default
        
        return value

# Usage
config_factory = (ConfigurationFactory()
    .add_provider(FileConfigProvider('config/default.yaml'))
    .add_provider(FileConfigProvider(f'config/{os.getenv("APP_ENV", "development")}.yaml'))
    .add_provider(EnvConfigProvider('APP_'))
)

config = config_factory.build()
database_host = config_factory.get('database.host', 'localhost')
```

#### 2. Configuration Validation Schema

```python
from typing import Any, Dict, List, Optional, Union, Callable
from dataclasses import dataclass, field
from enum import Enum
import re

class ValidationError(Exception):
    """Configuration validation error."""
    pass

@dataclass
class FieldValidator:
    """Field validation rules."""
    required: bool = False
    type_check: type = str
    min_value: Optional[Union[int, float]] = None
    max_value: Optional[Union[int, float]] = None
    min_length: Optional[int] = None
    max_length: Optional[int] = None
    pattern: Optional[str] = None
    choices: Optional[List[Any]] = None
    custom_validator: Optional[Callable[[Any], bool]] = None
    error_message: str = ""

class ConfigValidator:
    """Configuration validation system."""
    
    def __init__(self):
        self.schema: Dict[str, FieldValidator] = {}
    
    def add_field(self, field_name: str, validator: FieldValidator) -> 'ConfigValidator':
        """Add field validation rule."""
        self.schema[field_name] = validator
        return self
    
    def validate(self, config: Dict[str, Any]) -> List[str]:
        """Validate configuration and return list of errors."""
        errors = []
        
        for field_name, validator in self.schema.items():
            try:
                self._validate_field(field_name, config, validator)
            except ValidationError as e:
                errors.append(str(e))
        
        return errors
    
    def _validate_field(self, field_name: str, config: Dict[str, Any], validator: FieldValidator) -> None:
        """Validate a single field."""
        # Get field value using dot notation
        value = self._get_nested_value(config, field_name)
        
        # Check if required
        if validator.required and value is None:
            raise ValidationError(f"Field '{field_name}' is required")
        
        # Skip further validation if value is None and not required
        if value is None:
            return
        
        # Type checking
        if not isinstance(value, validator.type_check):
            raise ValidationError(f"Field '{field_name}' must be of type {validator.type_check.__name__}")
        
        # Numeric validations
        if isinstance(value, (int, float)):
            if validator.min_value is not None and value < validator.min_value:
                raise ValidationError(f"Field '{field_name}' must be >= {validator.min_value}")
            
            if validator.max_value is not None and value > validator.max_value:
                raise ValidationError(f"Field '{field_name}' must be <= {validator.max_value}")
        
        # String validations
        if isinstance(value, str):
            if validator.min_length is not None and len(value) < validator.min_length:
                raise ValidationError(f"Field '{field_name}' must be at least {validator.min_length} characters")
            
            if validator.max_length is not None and len(value) > validator.max_length:
                raise ValidationError(f"Field '{field_name}' must be at most {validator.max_length} characters")
            
            if validator.pattern and not re.match(validator.pattern, value):
                raise ValidationError(f"Field '{field_name}' does not match required pattern")
        
        # Choice validation
        if validator.choices and value not in validator.choices:
            raise ValidationError(f"Field '{field_name}' must be one of {validator.choices}")
        
        # Custom validation
        if validator.custom_validator and not validator.custom_validator(value):
            error_msg = validator.error_message or f"Field '{field_name}' failed custom validation"
            raise ValidationError(error_msg)
    
    def _get_nested_value(self, config: Dict[str, Any], key: str) -> Any:
        """Get nested value using dot notation."""
        keys = key.split('.')
        value = config
        
        for k in keys:
            if isinstance(value, dict) and k in value:
                value = value[k]
            else:
                return None
        
        return value

# Example usage
def validate_url(value: str) -> bool:
    """Custom URL validator."""
    url_pattern = re.compile(
        r'^https?://'  # http:// or https://
        r'(?:(?:[A-Z0-9](?:[A-Z0-9-]{0,61}[A-Z0-9])?\.)+[A-Z]{2,6}\.?|'  # domain...
        r'localhost|'  # localhost...
        r'\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})'  # ...or ip
        r'(?::\d+)?'  # optional port
        r'(?:/?|[/?]\S+)$', re.IGNORECASE)
    return url_pattern.match(value) is not None

# Create validator schema
validator = (ConfigValidator()
    .add_field('database.host', FieldValidator(
        required=True,
        type_check=str,
        min_length=1,
        pattern=r'^[a-zA-Z0-9.-]+$'
    ))
    .add_field('database.port', FieldValidator(
        required=True,
        type_check=int,
        min_value=1,
        max_value=65535
    ))
    .add_field('api.base_url', FieldValidator(
        required=True,
        type_check=str,
        custom_validator=validate_url,
        error_message="API base URL must be a valid HTTP/HTTPS URL"
    ))
    .add_field('logging.level', FieldValidator(
        required=False,
        type_check=str,
        choices=['DEBUG', 'INFO', 'WARNING', 'ERROR', 'CRITICAL']
    ))
)

# Validate configuration
config = {
    'database': {
        'host': 'localhost',
        'port': 5432
    },
    'api': {
        'base_url': 'https://api.example.com'
    },
    'logging': {
        'level': 'INFO'
    }
}

validation_errors = validator.validate(config)
if validation_errors:
    print("❌ Configuration validation failed:")
    for error in validation_errors:
        print(f"  - {error}")
else:
    print("✅ Configuration validation passed!")
```

---

## 🎯 Real-World Examples

### 🚀 Flask Application Configuration

```python
# app/config.py
import os
from typing import Dict, Any

class Config:
    """Base configuration class."""
    
    # Application settings
    SECRET_KEY = os.environ.get('SECRET_KEY') or 'dev-secret-key-change-in-production'
    
    # Database settings
    SQLALCHEMY_DATABASE_URI = os.environ.get('DATABASE_URL') or 'sqlite:///app.db'
    SQLALCHEMY_TRACK_MODIFICATIONS = False
    SQLALCHEMY_ENGINE_OPTIONS = {
        'pool_recycle': 300,
        'pool_pre_ping': True
    }
    
    # Mail settings
    MAIL_SERVER = os.environ.get('MAIL_SERVER') or 'smtp.gmail.com'
    MAIL_PORT = int(os.environ.get('MAIL_PORT') or 587)
    MAIL_USE_TLS = os.environ.get('MAIL_USE_TLS', 'true').lower() in ['true', 'on', '1']
    MAIL_USERNAME = os.environ.get('MAIL_USERNAME')
    MAIL_PASSWORD = os.environ.get('MAIL_PASSWORD')
    
    # Redis settings
    REDIS_URL = os.environ.get('REDIS_URL') or 'redis://localhost:6379/0'
    
    # Upload settings
    UPLOAD_FOLDER = os.environ.get('UPLOAD_FOLDER') or 'uploads'
    MAX_CONTENT_LENGTH = int(os.environ.get('MAX_CONTENT_LENGTH') or 16 * 1024 * 1024)  # 16MB
    
    # Security settings
    WTF_CSRF_TIME_LIMIT = int(os.environ.get('CSRF_TIME_LIMIT') or 3600)
    REMEMBER_COOKIE_DURATION = int(os.environ.get('REMEMBER_COOKIE_DURATION') or 86400)  # 1 day
    
    @staticmethod
    def init_app(app):
        """Initialize application with configuration."""
        pass

class DevelopmentConfig(Config):
    """Development configuration."""
    DEBUG = True
    TESTING = False
    
    # Development-specific overrides
    SQLALCHEMY_DATABASE_URI = os.environ.get('DEV_DATABASE_URL') or 'sqlite:///dev.db'
    MAIL_SUPPRESS_SEND = True
    
    @staticmethod
    def init_app(app):
        Config.init_app(app)
        
        # Development-specific initialization
        import logging
        from logging import StreamHandler
        
        handler = StreamHandler()
        handler.setLevel(logging.DEBUG)
        app.logger.addHandler(handler)

class ProductionConfig(Config):
    """Production configuration."""
    DEBUG = False
    TESTING = False
    
    # Production security settings
    SSL_REDIRECT = True
    SEND_FILE_MAX_AGE_DEFAULT = 31536000  # 1 year
    
    @staticmethod
    def init_app(app):
        Config.init_app(app)
        
        # Production-specific initialization
        import logging
        from logging.handlers import SMTPHandler, RotatingFileHandler
        import os
        
        # Email error handler
        if app.config['MAIL_USERNAME']:
            auth = (app.config['MAIL_USERNAME'], app.config['MAIL_PASSWORD'])
            mail_handler = SMTPHandler(
                mailhost=(app.config['MAIL_SERVER'], app.config['MAIL_PORT']),
                fromaddr=app.config['MAIL_USERNAME'],
                toaddrs=['admin@example.com'],
                subject='Application Error',
                credentials=auth,
                secure=() if app.config['MAIL_USE_TLS'] else None
            )
            mail_handler.setLevel(logging.ERROR)
            app.logger.addHandler(mail_handler)
        
        # File handler for logs
        if not os.path.exists('logs'):
            os.mkdir('logs')
        
        file_handler = RotatingFileHandler('logs/app.log', maxBytes=10240000, backupCount=10)
        file_handler.setFormatter(logging.Formatter(
            '%(asctime)s %(levelname)s: %(message)s [in %(pathname)s:%(lineno)d]'
        ))
        file_handler.setLevel(logging.INFO)
        app.logger.addHandler(file_handler)
        app.logger.setLevel(logging.INFO)

class TestingConfig(Config):
    """Testing configuration."""
    TESTING = True
    DEBUG = False
    
    # Testing database
    SQLALCHEMY_DATABASE_URI = os.environ.get('TEST_DATABASE_URL') or 'sqlite://'  # In-memory
    WTF_CSRF_ENABLED = False
    MAIL_SUPPRESS_SEND = True

# Configuration mapping
config = {
    'development': DevelopmentConfig,
    'production': ProductionConfig,
    'testing': TestingConfig,
    'default': DevelopmentConfig
}

# app/__init__.py
from flask import Flask
from .config import config

def create_app(config_name=None):
    """Application factory pattern."""
    if config_name is None:
        config_name = os.environ.get('FLASK_ENV', 'default')
    
    app = Flask(__name__)
    app.config.from_object(config[config_name])
    config[config_name].init_app(app)
    
    return app
```

### 🐍 Django Settings Configuration

```python
# settings/base.py
import os
from pathlib import Path

# Build paths
BASE_DIR = Path(__file__).resolve().parent.parent.parent
PROJECT_ROOT = BASE_DIR.parent

# Security
SECRET_KEY = os.environ.get('DJANGO_SECRET_KEY', 'dev-key-change-in-production')
DEBUG = False
ALLOWED_HOSTS = []

# Application definition
DJANGO_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]

THIRD_PARTY_APPS = [
    'rest_framework',
    'corsheaders',
    'django_extensions',
]

LOCAL_APPS = [
    'apps.users',
    'apps.core',
    'apps.api',
]

INSTALLED_APPS = DJANGO_APPS + THIRD_PARTY_APPS + LOCAL_APPS

MIDDLEWARE = [
    'corsheaders.middleware.CorsMiddleware',
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]

ROOT_URLCONF = 'config.urls'

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [BASE_DIR / 'templates'],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]

# Database
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': os.environ.get('DB_NAME', 'myapp'),
        'USER': os.environ.get('DB_USER', 'postgres'),
        'PASSWORD': os.environ.get('DB_PASSWORD', ''),
        'HOST': os.environ.get('DB_HOST', 'localhost'),
        'PORT': os.environ.get('DB_PORT', '5432'),
        'OPTIONS': {
            'connect_timeout': 10,
        }
    }
}

# Cache
CACHES = {
    'default': {
        'BACKEND': 'django_redis.cache.RedisCache',
        'LOCATION': os.environ.get('REDIS_URL', 'redis://localhost:6379/0'),
        'OPTIONS': {
            'CLIENT_CLASS': 'django_redis.client.DefaultClient',
        }
    }
}

# Internationalization
LANGUAGE_CODE = 'en-us'
TIME_ZONE = 'UTC'
USE_I18N = True
USE_TZ = True

# Static files
STATIC_URL = '/static/'
STATIC_ROOT = BASE_DIR / 'staticfiles'
STATICFILES_DIRS = [BASE_DIR / 'static']

# Media files
MEDIA_URL = '/media/'
MEDIA_ROOT = BASE_DIR / 'media'

# Default primary key field type
DEFAULT_AUTO_FIELD = 'django.db.models.BigAutoField'

# settings/development.py
from .base import *

DEBUG = True
ALLOWED_HOSTS = ['localhost', '127.0.0.1', '0.0.0.0']

# Database for development
DATABASES['default']['NAME'] = 'myapp_dev'

# Email backend for development
EMAIL_BACKEND = 'django.core.mail.backends.console.EmailBackend'

# Django Extensions
if 'django_extensions' in INSTALLED_APPS:
    SHELL_PLUS_PRINT_SQL = True

# Django Debug Toolbar
if DEBUG:
    INSTALLED_APPS += ['debug_toolbar']
    MIDDLEWARE = ['debug_toolbar.middleware.DebugToolbarMiddleware'] + MIDDLEWARE
    
    INTERNAL_IPS = ['127.0.0.1']
    DEBUG_TOOLBAR_CONFIG = {
        'SHOW_TEMPLATE_CONTEXT': True,
        'SHOW_TOOLBAR_CALLBACK': lambda request: DEBUG,
    }

# settings/production.py
from .base import *

DEBUG = False
ALLOWED_HOSTS = os.environ.get('ALLOWED_HOSTS', '').split(',')

# Security settings
SECURE_BROWSER_XSS_FILTER = True
SECURE_CONTENT_TYPE_NOSNIFF = True
SECURE_HSTS_INCLUDE_SUBDOMAINS = True
SECURE_HSTS_SECONDS = 31536000
SECURE_REDIRECT_EXEMPT = []
SECURE_SSL_REDIRECT = True
SESSION_COOKIE_SECURE = True
CSRF_COOKIE_SECURE = True
X_FRAME_OPTIONS = 'DENY'

# Logging
LOGGING = {
    'version': 1,
    'disable_existing_loggers': False,
    'formatters': {
        'verbose': {
            'format': '{levelname} {asctime} {module} {process:d} {thread:d} {message}',
            'style': '{',
        },
    },
    'handlers': {
        'file': {
            'level': 'INFO',
            'class': 'logging.handlers.RotatingFileHandler',
            'filename': '/var/log/myapp/django.log',
            'maxBytes': 1024*1024*15,  # 15MB
            'backupCount': 10,
            'formatter': 'verbose',
        },
        'console': {
            'level': 'INFO',
            'class': 'logging.StreamHandler',
            'formatter': 'verbose',
        },
    },
    'loggers': {
        'django': {
            'handlers': ['file', 'console'],
            'level': 'INFO',
            'propagate': True,
        },
        'myapp': {
            'handlers': ['file', 'console'],
            'level': 'INFO',
            'propagate': True,
        },
    },
}

# manage.py
import os
import sys

if __name__ == '__main__':
    os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'settings.development')
    
    try:
        from django.core.management import execute_from_command_line
    except ImportError as exc:
        raise ImportError(
            "Couldn't import Django. Are you sure it's installed and "
            "available on your PYTHONPATH environment variable? Did you "
            "forget to activate a virtual environment?"
        ) from exc
    
    execute_from_command_line(sys.argv)
```

---

## 🔗 Interactive Code Snippets

### 🎮 Configuration Manager CLI Tool

```python
#!/usr/bin/env python3
"""
Interactive Configuration Manager
A CLI tool for managing Python project configurations
"""

import click
import json
import os
import sys
from pathlib import Path
from typing import Dict, Any

@click.group()
@click.version_option(version='1.0.0')
def cli():
    """🐍 Python Configuration Manager CLI"""
    pass

@cli.command()
@click.option('--format', '-f', type=click.Choice(['toml', 'json', 'yaml', 'ini']), 
              default='toml', help='Configuration file format')
@click.option('--name', '-n', default='myproject', help='Project name')
@click.option('--author', '-a', default='Your Name', help='Author name')
@click.option('--email', '-e', default='your.email@example.com', help='Author email')
def init(format: str, name: str, author: str, email: str):
    """Initialize a new configuration file."""
    click.echo(f"🚀 Initializing {format.upper()} configuration for '{name}'")
    
    if format == 'toml':
        create_pyproject_toml(name, author, email)
    elif format == 'json':
        create_json_config(name, author, email)
    elif format == 'yaml':
        create_yaml_config(name, author, email)
    elif format == 'ini':
        create_ini_config(name, author, email)
    
    click.echo("✅ Configuration file created successfully!")

def create_pyproject_toml(name: str, author: str, email: str):
    """Create pyproject.toml file."""
    content = f'''[build-system]
requires = ["setuptools>=75.0.0", "wheel"]
build-backend = "setuptools.build_meta"

[project]
name = "{name.lower().replace(' ', '-')}"
version = "0.1.0"
description = "A fantastic Python project"
readme = "README.md"
authors = [
    {{name = "{author}", email = "{email}"}},
]
license = {{text = "MIT"}}
requires-python = ">=3.9"
keywords = ["python", "project"]
classifiers = [
    "Development Status :: 3 - Alpha",
    "Intended Audience :: Developers",
    "License :: OSI Approved :: MIT License",
    "Programming Language :: Python :: 3",
    "Programming Language :: Python :: 3.9",
    "Programming Language :: Python :: 3.10",
    "Programming Language :: Python :: 3.11",
    "Programming Language :: Python :: 3.12",
]

dependencies = [
    "click>=8.0.0",
    "rich>=12.0.0",
]

[project.optional-dependencies]
dev = [
    "pytest>=7.0.0",
    "black>=22.0.0",
    "mypy>=1.0.0",
    "pre-commit>=2.20.0",
]

[project.urls]
Homepage = "https://github.com/username/{name.lower().replace(' ', '-')}"
Repository = "https://github.com/username/{name.lower().replace(' ', '-')}.git"
Issues = "https://github.com/username/{name.lower().replace(' ', '-')}/issues"

[project.scripts]
{name.lower().replace(' ', '-')} = "{name.lower().replace(' ', '_')}.cli:main"

[tool.black]
line-length = 88
target-version = ['py39']

[tool.mypy]
python_version = "3.9"
warn_return_any = true
warn_unused_configs = true
disallow_untyped_defs = true

[tool.pytest.ini_options]
testpaths = ["tests"]
addopts = "-v --tb=short"
'''
    
    with open('pyproject.toml', 'w') as f:
        f.write(content)

@cli.command()
@click.argument('file_path', type=click.Path(exists=True))
def validate(file_path: str):
    """Validate a configuration file."""
    click.echo(f"🔍 Validating configuration file: {file_path}")
    
    path = Path(file_path)
    
    try:
        if path.suffix == '.toml':
            import tomllib
            with open(path, 'rb') as f:
                config = tomllib.load(f)
            click.echo("✅ Valid TOML syntax")
            
        elif path.suffix == '.json':
            with open(path, 'r') as f:
                config = json.load(f)
            click.echo("✅ Valid JSON syntax")
            
        elif path.suffix in ['.yaml', '.yml']:
            import yaml
            with open(path, 'r') as f:
                config = yaml.safe_load(f)
            click.echo("✅ Valid YAML syntax")
            
        # Perform semantic validation for pyproject.toml
        if path.name == 'pyproject.toml':
            validate_pyproject_toml(config)
            
    except Exception as e:
        click.echo(f"❌ Validation failed: {e}")
        sys.exit(1)

def validate_pyproject_toml(config: Dict[str, Any]):
    """Validate pyproject.toml structure."""
    errors = []
    
    # Check required sections
    if 'build-system' not in config:
        errors.append("Missing required [build-system] section")
    
    if 'project' in config:
        project = config['project']
        
        # Check required fields
        if 'name' not in project:
            errors.append("Missing required project.name field")
        
        if 'version' not in project and 'version' not in project.get('dynamic', []):
            errors.append("Missing project.version field (must be static or dynamic)")
    
    if errors:
        for error in errors:
            click.echo(f"❌ {error}")
        sys.exit(1)
    else:
        click.echo("✅ pyproject.toml structure is valid")

@cli.command()
@click.argument('key')
@click.argument('value')
@click.option('--file', '-f', default='pyproject.toml', help='Configuration file')
def set(key: str, value: str, file: str):
    """Set a configuration value."""
    click.echo(f"🔧 Setting {key} = {value} in {file}")
    
    # This would require a more sophisticated implementation
    # to modify TOML/JSON/YAML files while preserving structure
    click.echo("⚠️  This feature is not implemented yet")

@cli.command()
@click.argument('key')
@click.option('--file', '-f', default='pyproject.toml', help='Configuration file')
def get(key: str, file: str):
    """Get a configuration value."""
    click.echo(f"🔍 Getting {key} from {file}")
    
    try:
        path = Path(file)
        
        if path.suffix == '.toml':
            import tomllib
            with open(path, 'rb') as f:
                config = tomllib.load(f)
        elif path.suffix == '.json':
            with open(path, 'r') as f:
                config = json.load(f)
        
        # Navigate nested keys
        keys = key.split('.')
        value = config
        
        for k in keys:
            if isinstance(value, dict) and k in value:
                value = value[k]
            else:
                click.echo(f"❌ Key '{key}' not found")
                return
        
        click.echo(f"✅ {key} = {value}")
        
    except Exception as e:
        click.echo(f"❌ Error reading configuration: {e}")

@cli.command()
@click.option('--output', '-o', type=click.File('w'), default='-', help='Output file')
def template(output):
    """Generate configuration templates."""
    template_content = '''# Configuration Template Examples

## pyproject.toml
[build-system]
requires = ["setuptools>=75.0.0"]
build-backend = "setuptools.build_meta"

[project]
name = "my-project"
version = "0.1.0"

## .env
APP_ENV=development
DB_HOST=localhost
DB_PORT=5432
SECRET_KEY=your-secret-key

## config.yaml
database:
  host: localhost
  port: 5432
  name: myapp

api:
  base_url: https://api.example.com
  timeout: 30
'''
    
    output.write(template_content)
    click.echo("📝 Configuration templates generated")

if __name__ == '__main__':
    cli()
```

### 🎯 Usage Examples

```bash
# Initialize new project configuration
python config_manager.py init --format toml --name "MyAwesomeProject" --author "John Doe"

# Validate existing configuration
python config_manager.py validate pyproject.toml

# Get configuration value
python config_manager.py get project.name --file pyproject.toml

# Generate templates
python config_manager.py template --output config_examples.txt
```

---

## 🎉 Conclusion

```ascii
┌─────────────────────────────────────────────────────────────┐
│                    🎯 Key Takeaways                         │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ✅ Use pyproject.toml as your primary configuration file   │
│  🔒 Keep secrets in environment variables                   │
│  🏗️  Structure configuration logically                      │
│  🔍 Validate configuration early and often                  │
│  📚 Document your configuration schema                      │
│  🔄 Support multiple environments seamlessly                │
│                                                             │
└─────────────────────────────────────────────────────────────┘

Configuration Evolution Timeline:

setup.py (Legacy) ──▶ setup.cfg (Better) ──▶ pyproject.toml (Modern)
     ↓                      ↓                       ↓
  Executable           Declarative              Standardized
  Complex              Simpler                  Comprehensive
  Error-prone          Safer                    Future-proof
```

## 🔗 Additional Resources

- **📖 Official Python Packaging Guide**: https://packaging.python.org/
- **📋 PEP 518 - pyproject.toml**: https://peps.python.org/pep-0518/
- **📋 PEP 621 - Project Metadata**: https://peps.python.org/pep-0621/
- **🔧 TOML Specification**: https://toml.io/
- **🌐 python-dotenv**: https://github.com/theskumar/python-dotenv
- **⚡ Click CLI Framework**: https://click.palletsprojects.com/

---

**Happy Configuring! 🐍✨**

*Created with ❤️ for the Python community*