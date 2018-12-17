# 可拖拽列表
这里的可拖拽列表使用了 [Vue.Draggable](https://github.com/SortableJS/Vue.Draggable)

## 使用
本项目中使用模块化引入的方式

```js
import draggable from 'vuedraggable'
...
export default {
  components: {
    draggable,
      ...
    }
    ...

```

### 与Vuex结合使用，绑定数据，体现动态变化
```html
<draggable v-model='myList'>
```
```js
computed: {
  myList: {
    get() {
      return this.$store.state.myList
    },
    set(value) {
      this.$store.commit('updateList', value)
    }
  }
}
```

#### Props 属性

Vue.Draggable 有 value 、list 、options 、element 、clone 、move 等属性值/函数，在本项目中我们使用了 `value` `list` `options` , 因此介绍这三种属性，其他的皆不赘述，详情请参考 [官方文档](https://github.com/SortableJS/Vue.Draggable)。

##### 1. value

类型：Array

必需：false

默认值：null

将数组输入到可拖动组件。通常与内部元素`v-for`指令引用的数组相同。这是使用Vue.draggable的首选方式，因为它与Vuex兼容。

```html
<draggable v-model='myList'>
```

##### 2. list

类型：Array

必需：false

默认值：null

value 属性的替代属性，list 是与拖、拽动作保持同步的数组。

主要不同在于，组件利用可拼接方法更新 list ，而 value 则不可改变。

##### 3. options

类型：Object

必需：false

用于初始化可排序对象的选项。例如，可以使用 `:options="{handle:'.handle'}"` 语句将拖动手柄与列表绑定。

### 适用场景

Vue.Draggable 的典型用法是`非基于 dom `的排序，对于需要满足用户以拖拽动作达到排序目的的场景非常适合。

### Demo

![](/assets/dnd_list.gif)