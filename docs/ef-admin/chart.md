# 图表

管理后台图表也是常见得需求。这里图表就只推荐ECharts，功能齐全，社区demo也丰富 [gallery](http://gallery.echartsjs.com/explore.html)。

ECharts 支持 webpack 引入，图省事可以将 ECharts 整个引入 `var echarts = require('echarts')` （这也是本项目中我们采取的方法）。不过 ECharts 还是不小的，我们大部分情况只是用到很少一部分功能，在此情况下可以按需引入。
```js
// 引入 ECharts 主模块
var echarts = require('echarts/lib/echarts');
// 引入柱状图
require('echarts/lib/chart/bar');
// 引入提示框和标题组件
require('echarts/lib/component/tooltip');
require('echarts/lib/component/title');
```
[webpack 中使用ECharts文档](http://echarts.baidu.com/tutorial.html#%E5%9C%A8%20webpack%20%E4%B8%AD%E4%BD%BF%E7%94%A8%20ECharts)

[ECharts 按需引入模块文档](https://github.com/ecomfe/echarts/blob/master/index.js)

在本项目中我们提供了三种图表示例：Keyboard Chart 、 Line Chart 、Mix Chart , 接下来我们以 Keyboard Chart 为例介绍ECharts的用法。


在绘图前我们需要为 ECharts 准备一个具备高宽的 DOM 容器。

```html
<div id="main" style="{height:600px;width:400px;}"></div>
```

接下来我们就要在 vue 中声明初始化 ECharts 了。我们可以通过 echarts.init 方法初始化一个 echarts 实例，并通过 setOption 方法生成一个简单的柱状图。因为 ECharts 初始化必须绑定 dom，所以我们只能在 vue 的 mounted 生命周期里进行初始化。

```js
mounted() {
  this.initCharts();
},
methods: {
  initCharts() {
    this.chart = echarts.init(this.getElementById('main'));
    // 使用指定的配置项和数据显示图表
    this.setOptions();
  },
  setOptions() {
    this.chart.setOption({
      // 指定图表的配置项和数据
      title: {
        text: 'ECharts 入门示例'
      },
      tooltip: {},
      xAxis: {
        data: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"]
      },
      yAxis: {},
      series: [{
        name: '销量',
        type: 'bar',
        data: [5, 20, 36, 10, 10, 20]
      }]
    })
  }
}

```

就这样简单，ECharts就配置完成了，一个简单的柱状图就诞生了。

![](/assets/echarts_bar.png)

这时候你想说我的data是远程获取的，或者说我动态改变 ECharts 的配置该怎么办呢？我们可以通过 watch 来触发 setOptions 方法

```js
//第一种 watch options变化 利用vue的深度 watcher，options一有变化就重新setOption
watch: {
  options: {
  handler(options) {
    this.chart.setOption(this.options)
  },
  deep: true
  },
}
//第二种 只watch 数据的变化 只有数据变化时触发ECharts
watch: {
  seriesData(val) {
    this.setOptions({series:val})
  }
}

```
以上两种做法原理其实都差不多，还是要结合业务来封装。后面就和平时使用 ECharts 没有什么区别了。此外 ECharts 的可配置项非常多，大家使用的时候可能要花一点时间了解它的 api 的。

## Demo:
![](/assets/charts.gif)

?> 具体实例可参照 `@/components/Charts/` 文件下几个 chart 文件

## 其它
当然社区里的其它图表如 [d3](https://github.com/d3/d3) , [Chart.js](https://github.com/chartjs/Chart.js) , [chartist-js](https://github.com/gionkunz/chartist-js) 等封装方法都是大同小异差不多的，这里就不再展开了。