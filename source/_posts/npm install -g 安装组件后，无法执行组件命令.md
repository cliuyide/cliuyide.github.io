---
  title: npm install -g 安装组件后，无法执行组件命令
  date: 2024-02-29 
  categories: 前端 
  tags: [npm,前端,问题] 
---
### npm install -g xx安装组件后，无法执行组件命令

#### 排查
1.使用下面命令查看npm配置 prefix字段
```
npm config list
```
进入prefix值的目录中
查看是否有对应的组件命令
如果没有，查看npm组件导入命令是否正确
如果有确认 prefix值的目录有没有设置到系统的环境变量中










