# Markdown 编辑器
这里的Markdown 编辑器使用了 [simplemde-markdown-editor](https://github.com/sparksuite/simplemde-markdown-editor)

## 使用
本项目中使用模块化引入的方式，引入的代码地址在`@/components/MarkdownEditor`

```html
<template>
  <div>
    <markdown-editor id="contentEditor"
          ref="contentEditor"
          v-model="content"
          :height="300"
          :zIndex="20">
    </markdown-editor>
  </div>
  <el-button @click="markdown2Html">To HTML</el-button>
</template>

<script>
  import MarkdownEditor from '@/components/MarkdownEditor'
  export default {
    components: {
      MarkdownEditor,
      ...
    }
    ...
    methods: {
      markdown2Html() {
        import('showdown').then(showdown => {
          const converter = new showdown.Converter()
          this.html = converter.makeHtml(this.content)
        })
      }
    }
  }
</script>
```

### Demo

![](/assets/markdown.png)