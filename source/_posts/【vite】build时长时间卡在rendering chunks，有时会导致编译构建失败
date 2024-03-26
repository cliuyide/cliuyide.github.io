---
  title: 【vite】build时长时间卡在rendering chunks，有时会导致编译构建失败
  date: 2024-03-26 
  categories: 前端 
  tags: [npm,前端,问题,vite] 
---
### 【vite】build时长时间卡在rendering chunks，有时会导致编译构建失败

#### 参考
https://github.com/vitejs/vite/issues/5597
在vite.config.js中添加下列配置
```
export default defineConfig({
  css: {
    preprocessorOptions: {
      scss: {
        charset: false
      }
    }
  },
  build: {
    minify: false
  }
})
```








