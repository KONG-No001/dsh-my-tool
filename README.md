# dsh-my-tool

一个最小的 DeepSeek Harness 插件：每次加载时，在运行 DSH 的终端输出 `HELLO WORLD!`。
它不注册聊天工具，也不添加页面。

## 从 GitHub 安装

先将本项目的文件提交并推送到 GitHub 仓库。仓库必须对安装者可访问。

在 DSH 的「添加插件」输入框填写：

```text
github:KONG-No001/dsh-my-tool
```

也可以从命令行安装到 Web profile：

```powershell
dsh plugin --profile web add github:KONG-No001/dsh-my-tool
dsh web
```

如果你通过 npx 使用 DSH：

```powershell
npx @deepseek-ai/dsh plugin --profile web add github:KONG-No001/dsh-my-tool
npx @deepseek-ai/dsh web
```

安装后按界面提示重启 DSH（如果需要），然后检查 DSH 运行终端中的输出。
本项目直接分发 `.mjs` 文件，没有依赖和安装构建脚本，无需安装 TypeScript 或构建源码。

## 发布前本地试装

在「添加插件」输入框填写本项目的绝对目录路径，例如：

```text
D:\Workspaces\kongyu\dsh\my-tool
```

或者执行：

```powershell
dsh plugin --profile web add "D:\Workspaces\kongyu\dsh\my-tool"
```

通过插件包安装后，不需要再传入 `--patch`。如果之前在 profile 或 home 的
`cordis.patch.yml` 中手动添加了旧插件条目，请移除那条旧配置，避免输出两次。

## 文件说明

- `my-plugin.mjs`：插件入口，导出 `name` 和 `apply()`。
- `package.json`：包入口以及 `dsh.bundle.patch` 声明。
- `cordis.patch.yml`：按包名 `dsh-my-tool` 加载插件，安装后无需硬编码文件路径。

## 卸载

```powershell
dsh plugin --profile web remove dsh-my-tool
```

## 官方参考

[打包与安装插件](https://github.com/deepseek-ai/deepseek-harness/blob/master/docs/user/develop/basic/publish.zh.md)
