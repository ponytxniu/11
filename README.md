<img src="https://github.com/ricklamers/gpt-code-ui/assets/1309307/9ad4061d-2e26-4407-9431-109b650fb022" alt="GPT-Code logo" width=240 />

 OpenAI的ChatGPT[代码解释器](https://openai.com/blog/chatgpt-plugins#code-interpreter)的开源实现

只需要求 OpenAI 模型执行某些操作，它就会为您生成并执行代码

阅读[博客文章](https://ricklamers.io/posts/gpt-code)以了解更多信息
## 社区
Judah Cooper 主动提出创建并管理一个Discord社区[在这里](https://discord.gg/ZmTQwpkYu6)加入

## 安装

打开终端并运行：

```
pip install --extra-index-url https://pypi.python.org/simple gpt-code-ui
gptcode
```

为了使basic dependencies可用，建议pip在运行的shell中使用的Python环境中运行以下安装`gptcode`:

```sh
pip install "numpy>=1.24,<1.25" "dateparser>=1.1,<1.2" "pandas>=1.5,<1.6" "geopandas>=0.13,<0.14" "PyPDF2>=3.0,<3.1" "pdfminer>=20191125,<20191200" "pdfplumber>=0.9,<0.10" "matplotlib>=3.7,<3.8"
```

## 用户界面
<img src="https://github.com/ricklamers/gpt-code-ui/assets/1309307/c29c504a-a7ed-4ae0-9360-d7224bc3e3d6" alt="GPT-Code logo" width="100%" />
 
## 特征
- 上传文件
- 文件下载
- 上下文感知（可以参考您之前的消息）
- 生成代码
- 运行代码（Python内核）
- 模型切换（GPT-3.5和GPT-4）
## 杂项
### 使用 .env 作为 OpenAI key
您可以在工作目录中放置一个 .env 来加载 `OPENAI_API_KEY` 环境变量

### 可配置项
设置 `API_PORT`, `WEB_PORT`, `SNAKEMQ_PORT` 变量以覆盖默认值

设置`OPENAI_BASE_URL` 为更改正在使用的 OpenAI API 端点（请注意此环境变量包括protocol `https://...`).

您可以在存储库中使用`.env.example`(确保您`git clone`首先使用存储库来获取文件)

对于 Azure OpenAI 服务, 还有其他可配置变量,例如部署名称。请参阅 `.env.azure-example` 获取更多信息。请注意，Azure OpenAI 服务当前不支持 UI 上的模型选择。
```
cp .env.example .env
vim .env
gptcode
```

### Docker
[localagi](https://github.com/localagi) 努力将 Python 包捆绑到 Docker 容器中。在这里查看: [gpt-code-ui-docker](https://github.com/localagi/gpt-code-ui-docker).

## 贡献
请执行并查看[贡献指南](.github/CONTRIBUTING.md)!这应该是一个社区倡议。我会尽力做出回应。
