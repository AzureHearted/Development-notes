###### web开发个人笔记<br>~Lxs~

# electron的安装

## electron的离线安装方法(不推荐)

### 执行electron安装并中断

在项目中打开终端执行下发的代码:

``````bash
npm install electron
# 或
yarn add electron
``````

然后当看到开始安装electron时，按下<kbd>Ctrl</kbd>+<kbd>C</kbd>来中断操作。

### 修改`node_modules>electron>install.js`

找到`node_modules>electron>install.js`,并做如下修改：

```javascript
// downloads if not cached
downloadArtifact({
  version,
  artifactName: 'electron',
  force: process.env.force_no_cache === 'true',
  cacheRoot: process.env.electron_config_cache,
  checksums: process.env.electron_use_remote_checksums ?? process.env.npm_config_electron_use_remote_checksums ? undefined : require('./checksums.json'),
  platform,
  arch
}).then(extractFile).catch(err => {
  console.error(err.stack);
  process.exit(1);
});
```

改为

```javascript
downloadArtifact({
  version,
  artifactName: 'electron',
  force: process.env.force_no_cache === 'true',
  cacheRoot: process.env.electron_config_cache,
  checksums: process.env.electron_use_remote_checksums ?? process.env.npm_config_electron_use_remote_checksums ? undefined : require('./checksums.json'),
  platform,
  arch
}).then(extractFile).catch(err => {
  console.error(err.stack);
  process.exit(1);
});

extractFile('electron-v34.0.0-win32-x64.zip');
```

## 使用electron-vite

> [!note]
>
> [electron-vite | 下一代 Electron 开发构建工具](https://cn.electron-vite.org/)

在命令行中运行以下命令：

```sh
#npm
npm create @quick-start/electron@latest

#yarn (可能会出错)
yarn create @quick-start/electron

#pnpm
pnpm create @quick-start/electron
```

然后按照提示操作即可!

```
✔ Project name: … <electron-app>
✔ Select a framework: › vue
✔ Add TypeScript? … No / Yes
✔ Add Electron updater plugin? … No / Yes
✔ Enable Electron download mirror proxy? … No / Yes

Scaffolding project in ./<electron-app>...
Done.
```

还可以通过附加的命令行选项直接指定项目名称和你想要使用的模板。例如，要构建一个 Electron + Vue 项目，运行:

```sh
# npm 6.x
npm create @quick-start/electron my-app --template vue

# npm 7+, extra double-dash is needed:
npm create @quick-start/electron my-app -- --template vue

# yarn
yarn create @quick-start/electron my-app --template vue

# pnpm
pnpm create @quick-start/electron my-app --template vue
```

目前支持的模板预设如下：

| JavaScript                                                                                                 | TypeScript                                                                                                       |
| :--------------------------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------- |
| [vanilla](https://github.com/alex8088/quick-start/tree/master/packages/create-electron/playground/vanilla) | [vanilla-ts](https://github.com/alex8088/quick-start/tree/master/packages/create-electron/playground/vanilla-ts) |
| [vue](https://github.com/alex8088/quick-start/tree/master/packages/create-electron/playground/vue)         | [vue-ts](https://github.com/alex8088/quick-start/tree/master/packages/create-electron/playground/vue-ts)         |
| [react](https://github.com/alex8088/quick-start/tree/master/packages/create-electron/playground/react)     | [react-ts](https://github.com/alex8088/quick-start/tree/master/packages/create-electron/playground/react-ts)     |
| [svelte](https://github.com/alex8088/quick-start/tree/master/packages/create-electron/playground/svelte)   | [svelte-ts](https://github.com/alex8088/quick-start/tree/master/packages/create-electron/playground/svelte-ts)   |
| [solid](https://github.com/alex8088/quick-start/tree/master/packages/create-electron/playground/solid)     | [solid-ts](https://github.com/alex8088/quick-start/tree/master/packages/create-electron/playground/solid-ts)     |

# Electron项目目录说明

## **`src` 目录**

这是项目的主要源代码目录，包含了 Electron 应用的各个部分。

###  `src/main`

- **作用**：包含 Electron 主进程的代码。
- 文件描述
  - `index.ts`
    - 这是主进程的入口文件。
    - 负责创建 Electron 的主窗口、加载页面（通常通过 `loadURL` 或 `loadFile`），以及初始化主进程相关的逻辑。
    - 这里会设置应用的生命周期事件（例如 `ready`、`window-all-closed`、`activate` 等）。
  - 其他文件
    - 可能包括辅助模块或工具函数，例如菜单配置、窗口管理、IPC 通信处理等。

------

### `src/preload`

- **作用**：包含预加载脚本的代码。

- 文件描述

  - `index.ts`

    - 这是预加载脚本的入口文件。

    - 用于在主进程和渲染进程之间建立安全的桥梁。

    - 常用来定义 `contextBridge` 或暴露安全的 API，以限制渲染进程访问主进程的能力。

    - 示例代码：

      ```typescript
      import { contextBridge, ipcRenderer } from 'electron';
      
      contextBridge.exposeInMainWorld('api', {
        send: (channel: string, data: any) => ipcRenderer.send(channel, data),
        receive: (channel: string, callback: (data: any) => void) =>
          ipcRenderer.on(channel, (_, data) => callback(data)),
      });
      ```

  - 其他文件

    - 可以将不同功能的预加载脚本分开管理，例如处理文件系统操作、设置窗口行为等。

------

### `src/renderer`

- **作用**：包含渲染进程的代码（用户界面部分）。
- 目录描述
  - `src/`
    - 存放前端框架（如 Vue、React、Svelte）的核心代码。
    - 包含组件、页面路由、状态管理等内容。
  - `index.html`
    - 渲染进程的入口 HTML 文件。
    - 它会被 `main` 进程加载（通过 `loadFile` 或 `loadURL`）。
    - 在开发模式下，可能会通过开发服务器（如 Vite）运行。

------

##  `electron.vite.config.ts`

- **作用**：Electron 的 Vite 配置文件。

- 文件描述

  - 用于配置 Vite 的构建和开发行为，特别是针对 Electron 项目。

  - 通常包含以下配置：

    - 多入口配置（分别为主进程、预加载脚本、渲染进程提供支持）。

    - 输出目录、插件、环境变量等的设置。

    - 示例代码：

      ```typescript
      import { defineConfig } from 'vite';
      import { resolve } from 'path';
      
      export default defineConfig({
        build: {
          rollupOptions: {
            input: {
              main: resolve(__dirname, 'src/main/index.ts'),
              preload: resolve(__dirname, 'src/preload/index.ts'),
            },
          },
        },
      });
      ```

------

## `package.json`

- **作用**：项目的核心配置文件，管理依赖、脚本和元信息。

- 关键字段

  - `main`

    - 指定主进程的入口文件（通常指向 `dist/main/index.js` 或类似路径）。

  - `scripts`

    - 定义常用的 npm 脚本，例如启动、构建、打包等：

      ```json
      {
        "scripts": {
          "start": "vite",
          "build": "vite build",
          "dev": "electron .",
          "package": "electron-forge package"
        }
      }
      ```

  - `dependencies`

    - 项目运行时依赖的包，例如 `vue`、`react` 等。

  - `devDependencies`

    - 开发时使用的依赖，例如 `electron`、`vite`、`typescript` 等。

------

## **其他部分**

### **项目根目录**

- 用途
  - 存放配置文件和元数据。
  - 常见文件：
    - `.gitignore`：定义哪些文件/目录不应提交到版本控制。
    - `tsconfig.json`：TypeScript 配置文件，控制类型检查和编译行为。
    - `.eslintrc.js`：ESLint 配置文件，用于代码规范和静态检查。
    - `vite.config.ts`：Vite 的主配置文件（可能与 `electron.vite.config.ts` 合并）。

------

## 总结

这套结构将 **主进程**、**渲染进程** 和 **预加载脚本** 明确分离，并结合了现代前端开发工具（如 Vite 和 TypeScript），方便开发、调试和维护。每部分的功能大致如下：

| 目录                      | 作用                                                             |
| ------------------------- | ---------------------------------------------------------------- |
| `src/main`                | 主进程：负责应用的生命周期管理、窗口管理和后台逻辑。             |
| `src/preload`             | 预加载脚本：安全地在主进程和渲染进程之间通信，限制渲染进程权限。 |
| `src/renderer`            | 渲染进程：前端界面部分，使用 Vue/React 等框架实现交互。          |
| `electron.vite.config.ts` | Vite 的 Electron 配置，控制构建和开发行为。                      |
| `package.json`            | 管理项目依赖、元信息及脚本任务。                                 |

#  
