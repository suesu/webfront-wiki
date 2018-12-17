# 图标

本项目集成 [font-awesome](http://fontawesome.dashgame.com/) 一套绝佳的图标字体库和CSS框架。
Font Awesome为您提供可缩放的矢量图标，您可以使用CSS所提供的所有特性对它们进行更改，包括：大小、颜色、阴影或者其它任何支持的效果。

如果你没有在 [font-awesome](http://fontawesome.dashgame.com/) 中找到需要的图标，可以到 [iconfont.cn](http://iconfont.cn/) 上选择并生成自己的业务图标库，再进行使用。


## 生成图标库代码

首先，搜索并找到你需要的图标，将它采集到你的购物车里，在购物车里，你可以将选中的图标添加到项目中（没有的话，新建一个），后续生成的资源/代码都是以项目为维度的。

> 如果你已经有了设计稿，只是需要生成相关代码，可以上传你的图标后，再进行上面的操作。

<img width="600" alt="账户相关布局" src="https://gw.alipayobjects.com/zos/rmsportal/jJQYzRyqVFBBamUOppXH.png" />

<br />

?> 现在本项目支持和推荐单独导出 svg 的引入使用方式。下载方式如下图：

<img width="600" src="https://wpimg.wallstcn.com/1f8b1e56-cfd9-4ef7-a0aa-dfb0c2883aa3.gif" />

<br />

下载完成之后将下载好的 .svg 文件放入 `@/icons/svg` 文件夹下之后就会自动导入。

**使用方式**

```js
<svg-icon icon-class="password" /> //icon-class 为 icon 的名字
```

## 改变颜色
`svg-icon` 默认会读取其父级的 color `fill: currentColor;`

你可以改变父级的`color`或者直接改变`fill`的颜色即可。


