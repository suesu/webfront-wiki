# 分割面板
这里的可拖拽列表使用了 [vue-split-pane](https://github.com/PanJiaChen/vue-split-pane)

## 使用

```js
npm install vue-splitpane

// import
import splitPane from 'vue-splitpane'
...
export default {
  components: {
    splitPane,
      ...
  }
  ...

```

### 常规用法
```html
<split-pane v-on:resize="resize" :min-percent='20' :default-percent='30' split="vertical">
  <template slot="paneL">
    A
  </template>
  <template slot="paneR">
    B
  </template>
</split-pane>
```

### 嵌套使用
```html
<split-pane v-on:resize="resize" :min-percent='20' :default-percent='30' split="vertical">
  <template slot="paneL">
    A
  </template>
  <template slot="paneR">
    <split-pane split="horizontal">
      <template slot="paneL">
        B
      </template>
      <template slot="paneR">
        C
      </template>
    </split-pane>
  </template>
</split-pane>
```

#### Options 属性

| 属性         | 描述	       |类型	                          | 默认值    |
|--------------|:----------:|:------------------------------:|:--------:|
| split	       | 分割类型	   | String [horizontal,vertical]	  | 必选一种  |
| min-percent	 | 最小百分比	 | Number	                        | 10       |
| max-percent	 | 最大百分比	 | Number	                        | 10       |

### Demo

![](/assets/split_pane.png)