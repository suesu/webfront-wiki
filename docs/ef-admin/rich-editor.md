# 富文本

富文本是管理后台一个核心的功能，但同时又是一个有很多坑的地方。在选择富文本的过程中我也走了不少的弯路，市面上常见的富文本都基本用过了，最终权衡了一下选择了[Ckeditor](https://ckeditor.com/ckeditor-4/download/)。

* **[ckeditor](https://github.com/galetahub/ckeditor)** ckeditor是一家老牌做富文本的公司，今年也出了5.0版本，ui也变美观了不少。提供的编辑功能非常不错，官网给出的 [示例](https://ckeditor.com/ckeditor-4/) 有传统编辑器版本、文档编辑器版本、嵌入式编辑器版本，而且它号称是插件最丰富的富文本了，这也是本项目选用 ckeditor 的原因。

## Ckeditor

这里来简单讲一下在自己项目中使用 Ckeditor 的方法。

目前采用全局引用的方式。代码地址：`@/components/VueCKeditor`, 在 index.html 中引入。

```html
<script src=<%= htmlWebpackPlugin.options.path %>/ckeditor4.9.1/ckeditor.js></script>
```

接下来在 vue 中使用Ckeditor。

```html
<div class="vue-editor">
  <textarea :name="name"
    :id="id"
    :value="value"
    :types="types"
    :config="config">
  </textarea>
</div>
```
在 vue 中引入相关配置，配置文件为`@/components/VueCKeditor/config.js`,可在配置文件中定义 工具栏 、插件 、样式等，在此便不赘述。

```js
import default_config from './config';
const CKEDITOR = window.CKEDITOR;
```
在 vue 的 mounted 生命周期里进行初始化。

```js
mounted() {
  this.create();
},
methods: {
  create() {
    if (!CKEDITOR) {
      throw new Error(
        'CKEDITOR is missing, get it here: http://ckeditor.com/.'
      );
    } else {
      if (this.types === 'inline') {
        CKEDITOR.inline(this.id, this.config);
      } else {
        CKEDITOR.replace(this.id, this.config);
      }
      this.instance.setData(this.value);
      this.instance.on('instanceReady', () => {
        this.instance.setData(this.value);
      });
      this.instance.on('change', this.onChange);
      this.instance.on('blur', this.onBlur);
      this.instance.on('focus', this.onFocus);
    }
  },
  update(val) {
    let html = this.instance.getData();
    if (html !== val) {
      this.instance.setData(val, { internal: false });
    }
  },
  // 当编辑器内容发生变化时执行 onChange 事件
  onChange() {
    // do something
  },
  // 当编辑器失去焦点时执行 onBlur 事件
  onBlur() {
    // do something
  },
  // 当编辑器获得焦点时执行 onFocus 事件
  onFocus() {
    // do something
  }
},
```

### Demo

![](/assets/rich_editor.png)