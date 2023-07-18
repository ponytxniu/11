# [twitterbio.io](https://www.twitterbio.io/)

该项目使用 AI 为您生成 Twitter 简介。

[![Twitter Bio Generator](./public/screenshot.png)](https://www.twitterbio.io)

## 如何运行

该项目使用 [ChatGPT API](https://openai.com/api/)和 [Vercel Edge 功能](https://vercel.com/features/edge-functions) 它根据表单和用户输入构建提示，通过 Vercel Edge 函数将其发送到 chatGPT API，然后将响应流式传输回应用程序。

如果您想了解我是如何构建它的，请查看 [视频](https://youtu.be/JcE-1xzQTE0) or [博客文章](https://vercel.com/blog/gpt-3-app-next-js-vercel-edge-functions).

## 本地运行

克隆存储库后，前往[OpenAI](https://beta.openai.com/account/api-keys) 创建一个帐户，并将您的 API 密钥放入名为`.env`.

然后，在命令行中运行该应用程序，它将在`http://localhost:3000`.处可用
```bash
npm i
```

```bash
npm run dev
```

## 一键部署

 [使用Vercel](https://vercel.com?utm_source=github&utm_medium=readme&utm_campaign=vercel-examples)部署示例:

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/Nutlope/twitterbio&env=OPENAI_API_KEY&project-name=twitter-bio-generator&repo-name=twitterbio)
