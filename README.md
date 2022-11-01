## 功能

1. 侧边栏美化
2. 分版本查看
3. 内容锚点导航

## 使用步骤

1. mkdir xxx && cd xxx
2. npm init 初始化
3. 安装：npm i @zilongzhang/vuepress-theme-dragon
4. 创建如下目录
   docs
   ├── .vuepress // Vue 组件
   │ ├── public/img // 存放 logo 图片，应命名为 logo.png
   │ └── config.js // 应用主题，编写导航栏，侧边栏配置
5. config.js 添加主题
```js
module.exports = {
    theme:'@zilongzhang/vuepress-theme-dargon',
    themeConfig:{
        nav:[
            ...
        ],
        sidebar:{
            ...
        }
    }
  };
```
6. package.json添加启动命令
```js
"scripts": {
    "docs:dev": "vuepress dev docs",
    "docs:build": "vuepress build docs"
},
```

## 注意事项

1. 网站 logo 图片应放在 public/img 文件夹下，命名为 logo.png
2. 需要创建多版本方案时，应创建 versions 文件夹，在该文件夹下创建不同版本的 md 文件，同时，头部导航栏的链接应为一个具体的版本，例如：

```js
nav: [
    { text: "设计", link: "/design/versions/1.0.1/" },
    {
        text: "组件",
        items: [
        { text: "windows", link: "/components/windows/versions/1.0.0" },
        { text: "web", link: "/components/web/" },
        { text: "ios", link: "/components/ios/" },
        { text: "android", link: "/components/android/" },
        ],
    },
    { text: "资源", link: "/resource/" },
    { text: "关于", link: "/about/" },
],
```
