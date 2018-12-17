# EF-Admin

[![vue](https://img.shields.io/badge/vue-2.5.9-brightgreen.svg ':no-zoom')](https://github.com/vuejs/vue)
[![element-ui](https://img.shields.io/badge/element--ui-2.0.5-brightgreen.svg ':no-zoom')](https://github.com/ElemeFE/element)

<!-- [![license](https://img.shields.io/github/license/mashape/apistatus.svg ':no-zoom')](https://github.com/PanJiaChen/vue-element-admin/blob/master/LICENSE) -->

## 介绍

EF-Admin 是基于 Vue2.0，使用 Element UI 组件库的一个前端管理后台集成解决方案。包含管理后台应具备的用户、菜单、角色、权限等经典业务模块，提供了丰富的Vue功能组件，它可以帮助你快速搭建企业级中后台产品原型。

本项目对 [vue-element-admin](https://github.com/PanJiaChen/vue-element-admin) (github上最流行的后台管理模板) 做了修正和扩展。

**建议：** 本项目的定位是后台集成方案，不适合当基础模板来进行二次开发。你可以把 `EF-Admin`当做工具箱或者集成方案仓库，在 `vueAdmin-template` 的基础上开发，要什么就去 `EF-Admin` 那里复制过来。
> 模板工程: [vueAdmin-template](https://github.com/PanJiaChen/vueAdmin-template)。

## 功能
```
- 登录 / 注销

- 权限验证

- 管理后台业务模块（配合EF交互）
  - 菜单管理
  - 用户管理
  - 角色管理
  - 用户管理
  - 部门管理
  - 数据字典

- 多环境发布

- 全局功能
  - 国际化多语言
  - 多种动态换肤
  - 动态侧边栏（支持多级路由嵌套）
  - 动态面包屑
  - 快捷导航(标签页)
  - Svg Sprite 图标
  - 本地mock数据
  - Screenfull全屏
  - 自适应收缩侧边栏

- 编辑器
  - 富文本编辑器(Ckeditor)
  - Markdown
  - JSON 等多格式

- Excel
  - 导出excel
  - 导出zip
  - 导入excel
  - 前端可视化excel

- 表格
  - 动态表格
  - 拖拽表格
  - 树形表格
  - 内联编辑

- 错误页面
  - 401
  - 404

- 組件
  - 头像上传
  - 返回顶部
  - 拖拽Dialog
  - 拖拽看板
  - 列表拖拽
  - SplitPane
  - Dropzone
  - Sticky
  - CountTo

- ECharts 图表

- 表单综合样例

```

## 目录结构

本项目已经为你生成了一个完整的开发框架，提供了涵盖中后台开发的各类功能和坑位，下面是整个项目的目录结构。

```bash
├── build // 构建相关
├── config // 配置相关
├── mock // 项目mock 模拟数据
├── src // 源代码
│   ├── api // 所有请求
|   |   └── base-crud-api.js // CRUD 接口基类
│   ├── assets // 主题 字体等静态资源
|   │   ├── images // 图片资源
|   │   ├── styles // 全局样式
|   │   ├── locale // 国际化 language
|   │   |   ├── lang // 国际化 language
│   ├── components // 全局公用组件
│   ├── directive // 全局指令
│   ├── filters // 全局 filter
│   ├── icons // 项目所有 svg icons
|   ├── modules // 系统各功能模块
|   │   ├── common // 模块共通基类、业务组件等
|   |   |   ├── service // CRUD 服务基类
│   ├── router // 路由
│   ├── store // 全局 store管理
│   ├── utils // 全局公用方法
│   ├── vendor // 公用vendor
│   ├── views // 登录、布局、错误页面
│   ├── App.vue // 入口页面
│   ├── constants.js // 全局静态参数
│   ├── errorLog.js // 错误统一处理
│   ├── main.js // 入口js 加载组件 初始化等
├── static // 第三方不打包资源
│   └── ckeditor4.9.1 // 富文本
├── .babelrc // babel-loader 配置
├── eslintrc.js // eslint 配置项
├── .gitignore // git 忽略项
├── favicon.ico // favicon图标
├── index.html // html模板
└── package.json // package.json

```

## 安装

```bash
# 克隆项目
# 公司内网 Git
git clone http://10.21.20.76:6868/xiyt/EF-UI.git

# 安装依赖
npm install

# 本地开发 启动项目
npm run dev
```

> 强烈建议不要用直接使用 cnpm 安装有各种诡异的 bug，可以通过重新指定 registry 来解决 npm 安装速度慢的问题

```bash
npm install --registry=https://registry.npm.taobao.org
```

> Windows 用户若安装不成功，很大概率是`node-sass`安装失败，[解决方案]
下载项目的时候run install时，node-sass下载失败后来我在项目根目录下添加了一个.npmrc

```bash
sass_binary_site=https://npm.taobao.org/mirrors/node-sass/
registry=https://registry.npm.taobao.org
```
把node-sass的路径修改成淘宝的npm，就很顺利的可以在国内的网络环境下载了

> npm 5.6.0存在Bug https://github.com/npm/npm/issues/19393 故安装完nodejs之后将npm手动升级到5.8.0

```bash
npm install -g npm
```

启动完成后会自动打开浏览器访问 http://localhost:9527， 你看到下面的页面就代表成功了。

![](https://wpimg.wallstcn.com/1bc334a6-32a8-4f29-a037-ac3f5ce32588.png)

接下来你可以修改代码进行业务开发了，我们内建了典型业务模板、常用业务组件、模拟数据、HMR 实时预览、状态管理、国际化、全局路由等等各种实用的功能辅助开发，你可以继续阅读和探索左侧的其他文档。

<br/>


### 脚手架
使用Vue官方提供的 [Vue-cli脚手架](https://github.com/vuejs/vue-cli) ，包含多种打包构建模式，可自行到官网研究。

### 鸣谢
本文档参考了 [vue-element-admin-site](https://github.com/PanJiaChen/vue-element-admin-site)

文档生成通过 [docsify](https://github.com/QingWei-Li/docsify)