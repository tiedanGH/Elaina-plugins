<div align="center">

# Elaina-plugins

ElainaBot 官方插件与模块市场 — 在这里发现和分享插件/模块

[![ElainaBot](https://img.shields.io/badge/框架-ElainaBot_v2-blue)](https://github.com/ElainaCore/ElainaBot_v2)
[![QQ群](https://img.shields.io/badge/QQ交流群-1085402468-blue)](https://qm.qq.com/q/5O3xGoe4so)

</div>

## 🔌 如何提交插件

### 第一步：准备你的插件仓库

你的插件是一个独立的 GitHub 仓库，结构如下：

**大型插件** (含入口文件)：
```
你的仓库/
├── main.py              # 入口文件 (必须)
├── app/                 # 子模块目录
│   ├── feature_a.py
│   └── feature_b.py
├── data/                # 数据目录 (可选)
└── requirements.txt     # 额外依赖 (可选)
```

**小型插件** (单文件)：
```
你的仓库/
└── my_plugin.py         # 插件文件
```

### 第二步：添加插件元数据

在入口文件中声明 `__plugin_meta__`：

```python
__plugin_meta__ = {
    'name': '我的插件',
    'author': '你的名字',
    'description': '插件功能描述',
    'version': '1.0.0',
    'github': 'https://github.com/你的用户名/你的仓库',
}
```

### 第三步：提交 PR

1. Fork 本仓库
2. 编辑 `plugins.json`，添加你的插件信息
3. 提交 Pull Request

### `plugins.json` 格式

```json
[
  {
    "name": "插件目录名",
    "type": "plugin",
    "author": "作者",
    "description": "插件描述",
    "version": "1.0.0",
    "category": "分类",
    "github": "https://github.com/你的用户名/你的仓库",
    "branch": "main",
    "tags": ["标签1", "标签2"]
  }
]
```

#### 字段说明

| 字段 | 必填 | 说明 |
|------|------|------|
| `name` | ✅ | 名称, 安装后的目录名 (`plugins/<name>` 或 `modules/<name>`) |
| `type` | ✅ | 类型: `plugin` 或 `module` |
| `author` | ✅ | 作者名 |
| `description` | ✅ | 描述 |
| `version` | ✅ | 版本号 |
| `category` | ✅ | 分类 |
| `github` | ✅ | GitHub 仓库地址 |
| `branch` | ❌ | 分支名，默认 `main` |
| `path` | ❌ | 仓库内文件路径 (单文件插件用) |
| `tags` | ❌ | 标签数组，用于搜索 |

#### 两种安装模式

**仓库型** — 整个仓库拉取解压到 `plugins/<name>/`：
```json
{
  "name": "my-plugin",
  "github": "https://github.com/user/my-plugin",
  "branch": "main"
}
```

**单文件型** — 一个仓库包含多个小插件，通过 `path` 指定：
```json
{
  "name": "hello",
  "github": "https://github.com/ElainaCore/Elaina-plugins",
  "path": "plugins/hello/hello.py",
  "branch": "main"
}
```

## 📦 如何提交模块

### 第一步：准备你的模块仓库

模块是一个独立的 GitHub 仓库，结构如下：

```
你的仓库/
├── main.py              # 入口文件 (必须)
├── app/                 # 子模块目录 (可选)
├── data/                # 数据目录 (可选, 更新时保留)
└── requirements.txt     # 额外依赖 (可选)
```

### 第二步：添加模块元数据

在 `main.py` 中声明 `__module_meta__`：

```python
__module_meta__ = {
    'name': '模块名',
    'description': '模块描述',
    'version': '1.0.0',
    'author': '作者',
}
```

### 第三步：提交 PR

1. Fork 本仓库
2. 编辑 `plugins.json`，添加你的模块信息
3. 提交 Pull Request

```json
{
  "name": "my_module",
  "type": "module",
  "author": "你的名字",
  "description": "模块描述",
  "version": "1.0.0",
  "category": "分类",
  "github": "https://github.com/你的用户名/你的仓库",
  "branch": "main",
  "tags": ["标签1"]
}
```

> 安装时整个仓库内容会解压到 `modules/<name>/`，`data/` 目录在更新时不会被覆盖。

## 📋 提交规范

- 额外 pip 依赖请在仓库中提供 `requirements.txt`
- 插件代码必须包含 `__plugin_meta__`，模块必须包含 `__module_meta__`
- 禁止提交恶意代码、违法内容

