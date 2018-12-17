
# 开发环境
正所谓工欲善其事，必先利其器，这里推荐使用 [VSCode](https://code.visualstudio.com/)来作为前端开发的IDE工具。读者可以自行到官网下载相应的版本安装，如图：

![](/assets/vscode+eslint.png)

### 代码规范

当然，仅安装vscode还是不够的，日常团队协作开发中，我们对代码的规范有一定要求，这里我借助工具 [Eslint](https://eslint.org/)来约束代码符合质量要求。

> ESLint最初是由Nicholas C. Zakas 于2013年6月创建的开源项目。它的目标是提供一个插件化的javascript代码检测工具。

我们想要vscode能根据Eslint的脚本自动检测代码规范性，这需要安装插件: <br/>
> Integrates ESLint JavaScript into VS Code.
[ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

除此之外，为了让开发更顺畅，推荐安装如下插件：<br/>
> Vue tooling for VS Code
[Vetur](https://marketplace.visualstudio.com/items?itemName=octref.vetur)

> VS Code plugin for prettier/prettier
[Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

> Beautify css, sass and less code (extension for Visual Studio Code)
[Beautify css/sass/scss/less](https://marketplace.visualstudio.com/items?itemName=michelemelluso.code-beautifier)

> Auto complete file name
[AutoFileName](https://marketplace.visualstudio.com/items?itemName=JerryHong.autofilename)

> 一个CSS值转REM的VSCode插件
[cssrem](https://marketplace.visualstudio.com/items?itemName=cipchk.cssrem)

插件安装后，打开setting.json文件，配置个性化的vscode：

![](/../assets/vscodeSetting.gif)

下面是我本地setting配置，贴出来给大家做参考。这里有几个插件的配置，需要读者先安装插件：
```bash
{
  "editor.wordWrap": "on",
  "files.autoSave": "afterDelay",
  "editor.fontSize": 16,
  "editor.tabSize": 2,
  "workbench.colorTheme": "Visual Studio Dark",
  "editor.renderWhitespace": "boundary",
  "editor.cursorBlinking": "smooth",
  // An array of language ids which should be validated by ESLint
  "eslint.validate": [
    "javascript",
    "javascriptreact",
    {
      "language": "vue",
      "autoFix": true
    }
  ],
  // The eslint options object to provide args normally passed to eslint when executed from a command line (see http://eslint.org/docs/developer-guide/nodejs-api#cliengine).
  "eslint.options": {
    "plugins": ["html"],
    "configFile": "D:/webfront_workspace/EF-Admin/.eslintrc.js"
  },
  // Define profile for specified syntax or use your own profile with specific rules.
  "emmet.syntaxProfiles": {
    "javascript": "jsx",
    "vue-html": "html",
    "vue": "html"
  },
  "files.associations": {
    "*.vue": "vue"
  },
  "eslint.autoFixOnSave": true,
  "prettier.semi": false,
  "vetur.format.defaultFormatterOptions": {
    "js-beautify-html": {
      // force-aligned | force-expand-multiline
      "wrap_attributes": "force-aligned | force-expand-multiline"
    },
    "prettyhtml": {
      "printWidth": 100,
      "singleQuote": false,
      "wrapAttributes": false,
      "sortAttributes": true
    },
    "prettier": {
      "semi": false,
      "singleQuote": true,
      "useTabs": false,
      "tabWidth": 2,
      "eslintIntegration": true
    }
  },
  "window.zoomLevel": 0
}
```
