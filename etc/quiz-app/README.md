# 测验

这些测验是 [AI 初学者课程](https://aka.ms/ai-beginners) 的课前和课后测验。

## 添加翻译的测验集

通过在 `assets/translations` 文件夹中创建匹配的测验结构来添加测验翻译。规范版测验位于 `assets/translations/en`。测验按课程分成多个小组。请确保与适当的测验部分对齐编号。此课程共有 40 个测验，编号从 0 开始。

编辑翻译后，编辑翻译文件夹中的 `index.js` 文件，以按照 `en` 中的惯例导入所有文件。

编辑 `assets/translations` 中的 `index.js` 文件以导入新的翻译文件。

然后，在此应用程序中的 `App.vue` 中编辑下拉菜单以添加您的语言。将本地化的缩写与您语言的文件夹名称相匹配。

最后，编辑翻译课程中的所有测验链接（如果有），以将此本地化作为查询参数包含在内，例如 `?loc=fr`。

## 项目设置

```bash
npm install
```

### 为开发编译和热重载

```bash
npm run serve
```

### 为生产编译和压缩

```bash
npm run build
```

### 检查和修复文件

```bash
npm run lint
```

### 自定义配置

请参阅 [配置参考](https://cli.vuejs.org/config/)。

致谢：感谢原始版本的测验应用程序：[arpan45/simple-quiz-vue](https://github.com/arpan45/simple-quiz-vue)

## 部署到 Azure

以下是帮助您入门的分步指南：

1. **分叉一个 GitHub 仓库**
   确保您的静态网页应用代码在您的 GitHub 仓库中。分叉此仓库。

2. **创建 Azure 静态网页应用**
   - 创建一个 [Azure 账户](http://azure.microsoft.com)
   - 转到 [Azure 门户](https://portal.azure.com)
   - 点击“创建资源”，搜索“静态网页应用”。
   - 点击“创建”。

3. **配置静态网页应用**
   - **基础信息**:
     - 订阅：选择您的 Azure 订阅。
     - 资源组：创建一个新的资源组或使用现有的。
     - 名称：为您的静态网页应用提供一个名称。
     - 区域：选择最接近您的用户的区域。
   
   - **部署详情**:
     - 源：选择“GitHub”。
     - GitHub 账户：授权 Azure 访问您的 GitHub 账户。
     - 组织：选择您的 GitHub 组织。
     - 仓库：选择包含您的静态网页应用的仓库。
     - 分支：选择您要部署的分支。
   
   - **构建详情**:
     - 构建预设：选择您的应用所使用的框架（例如，React、Angular、Vue 等）。
     - 应用位置：指定包含您的应用代码的文件夹（例如，如果在根目录，则为 `/`）。
     - API 位置：如果您有 API，请指定其位置（可选）。
     - 输出位置：指定生成构建输出的文件夹（例如 `build` 或 `dist`）。
   
4. **审查并创建**
   审查您的设置并点击“创建”。Azure 将设置必要的资源并在您的仓库中创建一个 GitHub Actions 工作流。

5. **GitHub Actions 工作流**
   Azure 将自动在您的仓库中创建一个 GitHub Actions 工作流文件（`.github/workflows/azure-static-web-apps-<name>.yml`）。该工作流将处理构建和部署过程。

6. **监控部署**
   转到您 GitHub 仓库的“Actions”标签。您应该会看到一个正在运行的工作流。该工作流将构建并将您的静态网页应用部署到 Azure。一旦工作流完成，您的应用将在提供的 Azure URL 上运行。

### 示例工作流文件

以下是 GitHub Actions 工作流文件的示例：

```yaml
name: Azure Static Web Apps CI/CD

on:
  push:
    branches:
      - main
  pull_request:
    types: [opened, synchronize, reopened, closed]
    branches:
      - main

jobs:
  build_and_deploy_job:
    runs-on: ubuntu-latest
    name: 构建和部署任务
    steps:
      - uses: actions/checkout@v2
      - name: 构建并部署
        id: builddeploy
        uses: Azure/static-web-apps-deploy@v1
        with:
          azure_static_web_apps_api_token: ${{ secrets.AZURE_STATIC_WEB_APPS_API_TOKEN }}
          repo_token: ${{ secrets.GITHUB_TOKEN }}
          action: "upload"
          app_location: "etc/quiz-app" # 应用源代码路径
          api_location: "" # API 源代码路径（可选）
          output_location: "dist" # 构建的应用内容目录 - 可选
```

### 额外资源

- [Azure 静态网页应用文档](https://learn.microsoft.com/azure/static-web-apps/getting-started)
- [GitHub Actions 文档](https://docs.github.com/actions/use-cases-and-examples/deploying/deploying-to-azure-static-web-app)