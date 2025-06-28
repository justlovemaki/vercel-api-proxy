# 🚀 vercel-api-proxy

本项目克隆自： [souying/vercel-api-proxy](https://github.com/souying/vercel-api-proxy) 

一个基于 Vercel 平台的轻量级 API 代理服务，旨在帮助开发者快速、免费地解决 API 跨域（CORS）和特定网络环境下的访问限制问题。

---

### 💡 项目价值

在日常开发和线上项目部署中，我们常常会遇到以下痛点：

*   **跨域请求限制**：浏览器出于安全策略，会阻止前端直接调用不同源的 API。
*   **API 访问性问题**：某些 API（如 OpenAI）在特定国家或地区无法直接访问。

`vercel-api-proxy` 正是为此而生，它利用 Vercel 的全球 CDN 和 Serverless 功能，为您提供一个稳定、高效的中间层，优雅地解决上述问题。

### ✨ 主要特性

*   **一键部署**：点击上方按钮即可在数秒内完成部署，无需任何复杂配置。
*   **完全免费**：充分利用 Vercel 提供的免费额度，无服务器成本，零负担运行。
*   **自定义域名**：支持绑定您自己的域名，提升专业性和访问稳定性。
*   **解决跨域**：作为服务端代理，完美绕过浏览器跨域限制。
*   **免服务器运维**：基于 Serverless 架构，您只需关注代码，Vercel 会搞定一切。

### 🚀 快速部署

部署本项目非常简单，您可以选择以下任意一种方式：

#### 方式一：一键部署 (推荐)

1.  点击 README 开头的 [![Vercel](https://vercel.com/button)](https://vercel.com/import/project?template=https://github.com/souying/vercel-api-proxy) 按钮。
2.  按照 Vercel 的引导流程，登录并完成创建即可。

#### 方式二：Fork 本项目后手动部署

1.  **Fork** 本项目到您自己的 GitHub 仓库。
2.  登录 [Vercel 官网](https://vercel.com/)，选择 "Import Project"。
3.  从您的 GitHub 仓库列表中找到并导入刚刚 Fork 的项目，然后部署。

### 📖 使用指南

部署成功后，您将获得一个 Vercel 提供的二级域名（例如 `your-project.vercel.app`）。

#### 1. 绑定自定义域名 (可选但强烈推荐)

> **重要提示**：Vercel 提供的 `*.vercel.app` 域名在中国大陆可能存在访问不稳定的问题。为了保证服务的可靠性，强烈建议您绑定自己的域名。您可以申请免费域名（如 `.tk`, `.ml` 等）或在域名注册商处购买。

在 Vercel 的项目仪表盘中，进入 "Settings" -> "Domains"，按照指引添加并配置您的域名。

![绑定域名](https://raw.githubusercontent.com/souying/vercel-api-proxy/main/img/domain.png)

#### 2. 构造代理请求

本服务的代理规则非常直观：

*   **代理 HTTP API**: `https://<你的域名>/http/<目标API地址>`
*   **代理 HTTPS API**: `https://<你的域名>/https/<目标API地址>`

只需将您要请求的 API 地址（去掉 `http://` 或 `https://` 协议头）拼接到您的代理域名之后即可。

### 📋 使用示例

假设您的服务已部署，并且绑定的域名是 `proxy.example.com`。

**场景**：您希望在前端项目中调用 OpenAI 的 API。

*   **原始请求地址**:
    ```
    https://api.openai.com/v1/chat/completions
    ```

*   **通过本服务代理后的请求地址**:
    ```
    https://proxy.example.com/https/api.openai.com/v1/chat/completions
    ```

现在，您可以在您的代码中直接使用这个新的代理地址发起请求，所有参数、请求头和请求体都会被原封不动地转发到目标 API。

