# 计数
这里的可拖拽列表使用了 [vue-countTo](https://github.com/PanJiaChen/vue-countTo)

## 使用
本项目中使用模块化引入的方式

```html
<template>
  <countTo :startVal='startVal' :endVal='endVal' :duration='3000'></countTo>
</template>

<script>
  import countTo from 'vue-count-to';
  export default {
    components: { countTo },
    data () {
      return {
        startVal: 0,
        endVal: 2017
      }
    }
  }
</script>

```
#### Options 属性

| 属性         | 描述	       |类型	    | 默认值    |
|--------------|:----------:|:------------:|:--------:|
| startVal	   | 起始值	   | Number	  | 0  |
| endVal  | 终止值	 | Number	    | 2017       |
| duration	 | 持续时间(以毫秒为单位)	 | Number	    | 3000      |
| autoplay	 | 自动开始	 | Boolean	   | true      |
| decimals	 | 小数点后几位数	 | Number	     | 0      |
| decimal	 | 十进制小数	 | String	     | .     |
| separator	 | 分隔符号	 | String	     | ,      |
| prefix	 | 前缀	 | String	      | ''      |
| suffix	 | 后缀	 | String	     | ''      |
| useEasing	 | 使用缓动功能	 | Boolean	  | true      |
| easingFn	 | 缓动功能	 | Function	  | ——      |

>注意：当 `autoplay:true` 时，它会在 startVal 或 endVal 改变时自动启动

#### Functions 函数

| 名称         | 描述	       |
|--------------|:----------:|
| mountedCallback	   | 挂载时会执行mountedCallback	   |
| start  | 开始	 |
| pause	 | 暂停	 |
| reset	 | 重置	 |

### Demo

![](/assets/countDemo.gif)