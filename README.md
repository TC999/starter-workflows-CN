<p align="center">
  <img src="https://avatars0.githubusercontent.com/u/44036562?s=100&v=4"/> 
</p>

## 该中文版信息（译者加）
 - 原项目地址:[starter-workflows](https://github.com/actions/starter-workflows)
 - 文档最后更新日期：2023年12月3日
 - 译者：ChatGPT3.5
 - 翻译内容：所有文档以及工作流配置文件注释
 - 如果原文档更新或翻译不准确请提议题(issue)
 - 如果您喜欢这个项目请标星(Star)

## 初始工作流程

这些是帮助人们开始使用 GitHub Actions 的工作流文件。它们在创建新的 GitHub Actions 工作流程时呈现出来。

 **如果你想开始使用 GitHub Actions，可以通过点击存储库中的 "Actions" 选项卡，在你想创建工作流程的地方使用这些初始工作流程。**

<img src="https://d3vv6lp55qjaqc.cloudfront.net/items/353A3p3Y2x3c2t2N0c01/Image%202019-08-27%20at%203.25.07%20PM.png" max-width="75%"/>

### 目录结构

 * [ci](ci): 持续集成工作流的解决方案
 * [deployments](deployments): 部署工作流的解决方案
 * [automation](automation): 工作流自动化的解决方案
 * [code-scanning](code-scanning): [代码扫描](https://github.com/features/security)的解决方案
 * [pages](pages): 页面工作流的解决方案
 * [icons](icons): 相关模板的 SVG 图标

每个工作流都必须用 YAML 编写，并具有 `.yml` 扩展名。它们还需要一个相应的 `.properties.json` 文件，其中包含有关工作流的额外元数据（这在 GitHub.com UI 中显示）。

例如：`ci/django.yml` 和 `ci/properties/django.properties.json`。

### 有效属性

 * `name`：在入门指南中显示的名称。此属性在存储库中是唯一的。
 * `description`：在入门指南中显示的描述
 * `iconName`：相关文件夹中的图标名称，例如，`django` 应该有一个图标 `icons/django.svg`。目前仅支持 SVG。另一个选择是使用 [octicon](https://primer.style/octicons/)。使用 octicon 的格式是 `octicon <<图标名称>>`。例如：`octicon person`
 * `creator`：入门指南中显示的模板的创建者。来自同一作者的所有工作流程模板将具有相同的 `creator` 字段。
 * `categories`：显示在哪些类别下的类别。至少从 [这里](#categories) 的列表中选择一个类别。此外，从 [此处](https://github.com/github/linguist/blob/master/lib/linguist/languages.yml) 提供的语言列表和 [此处](https://github.com/github-starter-workflows/repo-analysis-partner/blob/main/tech_stacks.yml) 提供的技术栈列表中选择类别。当用户查看可用模板时，与语言和技术栈匹配的模板将更为突出显示。

### 类别
 * 持续集成
 * 部署
 * 测试
 * 代码质量
 * 代码审查
 * 依赖管理
 * 监控
 * 自动化
 * 实用工具
 * 页面
 * Hugo

### 变量
这些变量可以放置在初始工作流程中，并将按照下面的详细信息进行替换：

 * `$default-branch`：将从存储库替换分支，例如 `main` 和 `master`
 * `$protected-branches`：将从存储库替换任何受保护的分支
 * `$cron-daily`：将在一天内替换为有效但随机的时间

## 如何在发布前测试模板

### 禁用公开的模板
模板作者在模板的 `properties.json` 文件中添加一个 `labels` 数组，其中包含一个 `preview` 标签。这将隐藏模板，除非用户在 URL 中使用查询参数 `preview=true`。
例如 `properties.json` 文件：
```json
{
    "name": "Node.js",
    "description": "使用 npm 构建和测试 Node.js 项目。",
    "iconName": "nodejs",
    "categories": ["持续集成", "JavaScript", "npm", "React", "Angular", "Vue"],
    "labels": ["preview"]
}
```

要查看带有 `preview` 标签的模板，请在 `new workflow` 页面 URL 中提供查询参数 `preview=true`。例如 `https://github.com/<owner>/<repo_name>/actions/new?preview=true`。

### 启用公开的模板
从 `properties.json` 文件中删除 `labels` 数组以将模板发布为公开。

## 许可证

本项目采用[MIT许可证](LICENSE)，参考中文译文如下：

MIT 许可证

版权所有（c）2020 GitHub

特此免费授予任何获得本软件及相关文档文件（以下简称“软件”）副本的人，无限制地处理本软件的权利，包括但不限于使用、复制、修改、合并、发布、分发、再许可和/或出售软件的权利，以及允许接收软件的人这样做，但须符合以下条件：

在所有的副本或实质性部分中，必须包含上述版权声明和本许可声明。

本软件按“原样”提供，不提供任何形式的明示或暗示担保，包括但不限于适销性、特定用途适用性和非侵权性的担保。在任何情况下，作者或版权持有人均不对任何索赔、损害或其他责任承担责任，无论是在合同、侵权或其他方面，由于或与软件或使用或其他交易中的软件有关，此许可证不授予您使用任何贡献者的姓名、标识或商标的权利。
