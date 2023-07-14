# 11
---
name: Chainlit
description: >-
  Build Python LLM apps in minutes ⚡️
  Chainlit lets you create ChatGPT-like UIs on top of any Python code in minutes! Some of the key features include intermediary steps visualisation, element management & display (images, text, carousel, etc.) as well as cloud deployment.
author:
  name: Chainlit
  avatar: https://avatars.githubusercontent.com/u/128686189?s=64&v=4
contributors: 
  - name: willydouhard
    avatar: https://avatars.githubusercontent.com/u/13104895?s=64&v=4
  - name: constantinidan  
    avatar: https://avatars.githubusercontent.com/u/16107237?s=64&v=4
language:
  - language: TypeScript
    percentage: 58.0
  - language: Python
    percentage: 41.5
star: '574'
fork: '201'
url: https://github.com/cloudstudio-platform/chainlit
banner: ./images/quick-start.png
icon: https://cs-res.codehub.cn/vscode/node.svg
video: ./images/Chainlit.mov
license: Apache-2.0
order: 18
---

# 欢迎来到 Chainlit 👋

**在几分钟内构建python LLM 应用程序 ⚡️**

Chainlit 可让您在几分钟之内就在任何Python代码上创建类似于ChatGPT的UI!一些关键功能包括中间步骤的可视化，元素的管理和现实（图像，文本，轮播等）以及云部署

[![](https://dcbadge.vercel.app/api/server/ZThrUxbAYw?style=flat)](https://discord.gg/ZThrUxbAYw)
[![Twitter](https://img.shields.io/twitter/url/https/twitter.com/chainlit_io.svg?style=social&label=Follow%20%40chainlit_io)](https://twitter.com/chainlit_io)
[![CI](https://github.com/Chainlit/chainlit/actions/workflows/ci.yaml/badge.svg)](https://github.com/Chainlit/chainlit/actions/workflows/ci.yaml)

## 安装

打开终端并运行:

```bash
$ pip install chainlit
$ chainlit hello
```

如果 `hello app`!

## 📖 Documentation

Please see [here](https://docs.chainlit.io) for full documentation on:

- Getting started (installation, simple examples)
- Examples
- Reference (full API docs)

## 🚀 Quickstart

### 🐍 Pure Python

Create a new file `demo.py` with the following code:
```python
import chainlit as cl


@cl.on_message  # this function will be called every time a user inputs a message in the UI
def main(message: str):
    # this is an intermediate step
    cl.Message(author="Tool 1", content=f"Response from tool1", indent=1).send()

    # send back the final answer
    cl.Message(content=f"This is the final answer").send()
```

Now run it!
```
$ chainlit run demo.py -w
```

<img src="./images/quick-start.png" alt="Quick Start"></img>

### 🔗 With LangChain

Checkout our plug and play [integration](https://docs.chainlit.io/langchain) with LangChain!

## 🛣 Roadmap
- [ ] New UI elements (spreadsheet, video, carousel...)
- [ ] Create your own UI elements via component framework
- [ ] DAG-based chain-of-thought interface
- [ ] Support more LLMs in the prompt playground
- [ ] App deployment

Tell us what you would like to see added in Chainlit using the Github issues or on [Discord](https://discord.gg/ZThrUxbAYw).

## 💁 Contributing

As an open-source initiative in a rapidly evolving domain, we welcome contributions, be it through the addition of new features or the improvement of documentation.

For detailed information on how to contribute, see [here](.github/CONTRIBUTING.md).

## License
Chainlit is open-source and licensed under the [Apache 2.0](LICENSE) license.
