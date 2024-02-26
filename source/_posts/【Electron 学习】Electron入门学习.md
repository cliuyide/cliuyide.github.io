---
  title: 【Electron 学习】Electron入门学习
  date: 2024-02-26 
  categories: 前端 
  tags: [electron,vue,前端] 
---
### 1.使用vue-cli-plugin-electron-builder创建electron项目
#### 1.安装vue客户端
```
$ npm install -g @vue/cli
# OR
yarn global add @vue/cli
```
#### 2.创建项目
```
vue create electron-vue
```
#### 3.安装 vue-cli-plugin-electron-builder
```
# 安装并调用 vue-cli-plugin-electron-builder
vue add electron-builder
```
核心文件说明:
1.package.json：这个文件通过 main 字段定义了编译后的主入口文件路径，并且通过 script 字段定义了应用程序的启动、编译等脚本程序。
2.src/background.js：这个文件就是 Electron 的主进程的入口文件，它是应用程序的入口点，负责管理整个应用的生命周期、创建窗口、原生 API 调用等。
3.src/main.js 是渲染进程的入口文件，就是我们通常写的 Vue 前端代码的入口。
#### 4.目录结构调整
我们在src下新建了 main 和 renderer 目录，并将之前的 src/background.js 迁移到了 main 目录下，且重命名为 index.js。然后再把之前和 Vue 相关的渲染进程的文件以及文件夹全部迁移到了 renderer 目录下。

这样在开发的时候，就可以一眼看明白哪些属于渲染进程、哪些属于主进程。

因为我们做了目录的调整，所以我们需要重新修改一下 vue.config.js 的编译配置：
```
// vue.config.js
const { defineConfig } = require('@vue/cli-service')
module.exports = defineConfig({
  transpileDependencies: true,
  pages: {
    index: {
      // 修改渲染进程入口文件的位置
      entry: 'src/renderer/main.js',
    },
  },
  pluginOptions: {
    electronBuilder: {
      nodeIntegration: true,
      // 修改主进程的入口文件位置
      mainProcessFile: 'src/main/index.js',
      // 设置主进程的修改监听，当主进程发生变更时，可以及时热更
      mainProcessWatch: ['src/main'],
    },
  },
})
```
修改 package.json 里面的 main 配置：
```
{
  ...
  "main": "index.js",
  ...
}
```
### 5.升级electron
官网版本页面
https://releases.electronjs.org/
```
yarn add electron@27.1.3 -D
```
可以在.npmrc中添加electron源
```
electron_mirror=https://npmmirror.com/mirrors/electron/
```
#### 启动
```
npm run electron:serve
```









