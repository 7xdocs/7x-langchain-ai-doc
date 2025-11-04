# LangChain 文档

## 项目概述


```text
# --- docs.langchain.com ----------------------------------------------
build/                    # Built docs (do not edit)
pipeline/                 # Build pipeline source code
scripts/                  # Helper scripts
src/                      # Source documentation files (edit these)
    labs/                 # LangChain Labs docs
    langsmith/            # LangSmith docs
    oss/                  # LangChain, LangGraph, and integrations docs
    docs.json             # Mintlify site configuration
tests/                    # Test files for the pipeline
Makefile                  # Build targets
pyproject.toml            # Dependencies

# --- reference.langchain.com -----------------------------------------
reference/                # Reference docs build pipelines
    dist/                 # Build docs (do not edit)
    javascript/           # JS/TS reference build pipeline
    python/               # Python reference build pipeline and source
    package.json          # Vercel commands and dependencies
    vercel.json           # Vercel configuration/redirects
```

# 搭建本地开发环境

1. 克隆此仓库。请遵循 [IDE_SETUP.md](./IDE_SETUP.md) 中列出的步骤。
2. 从 <https://docs.astral.sh/uv/> 安装 `uv`（如果尚未安装）。
3. 从 <https://nodejs.org/en/download/> 安装 `npm`（如果尚未安装）。
4. 创建并激活虚拟环境：

   ```bash
   cd docs
   uv venv
   source .venv/bin/activate
   ```

5. 安装依赖项：

   ```bash
   uv sync --all-groups
   ```

   ```bash
   npm i -g mint
   ```

安装完成后，你将可以使用 `docs` 命令：

```bash
docs --help
```

## 常用命令
- `docs dev` - 启动开发模式，支持文件监听和热重载
- `docs build` - 构建文档
- `docs migrate <path>` - 将 MkDocs 格式的 Markdown 文件转换为 Mintlify 格式
- `docs migrate-docusaurus <path>` - 将 Docusaurus 格式的 Markdown 文件转换为 Mintlify 格式


## 重要规则
- **仅编辑 `src/` 目录下的文件** - `build/` 目录是自动生成的，无需手动修改。
- **使用 Mintlify 语法** - 有关格式规范，请参阅 [Mintlify 文档](https://mintlify.com/docs)。
- **测试你的更改** - 使用 `docs dev` 命令在本地预览更改，该模式支持热重载（文件修改后自动刷新预览）。
- **使用安全的 Mintlify 命令** - 检查最终构建的文档是否存在无效链接时，请使用 `make mint-broken-links`，而非 `mint broken-links`。


## 文档服务
文档服务主要是基于 `mint` 这个工具启动的。 https://www.npmjs.com/package/mint；


## Prompt 模板

```
你是一个 langchain的技术专家，你非常了解 python、typescript和nodejs，帮我把下面的 langchain ai 文档翻译成中文，要求
- 保持 markdown 的格式不变，
- 不用翻译代码块
- Stability: 不翻译
- 不用翻译注释内容
- 不要翻译 yaml 块内容
- 不要翻译 ```包裹的 code 块中的内容
- 不要翻译 YAML Front Matter 部分

文档如下：

```


## 部署
本质上是部署 mintlify 服务，请查看 mintlify 文档。
https://dashboard.mintlify.com/7x/7x
