# 可拖拽弹框
这里的可拖拽弹框基于 [el-Dialog](http://element-cn.eleme.io/#/zh-CN/component/dialog) 进行了二次开发，封装的代码在`@/directives/el-dragDialog`。

## 使用
本项目中使用模块化引入的方式

```html
<template>
  <el-dialog v-el-drag-dialog
      title="Shipping address"
      :visible.sync="dialogTableVisible">
    <!-- 自定义内容 -->
  </el-dialog>
</template>

<script>
  import elDragDialog from '@/directives/el-dragDialog';
  export default {
    components: { elDragDialog },
    data () {
      return {
        startVal: 0,
        endVal: 2017
      }
    }
  }
</script>

```

### Demo

![](/assets/drag_dialog.gif)