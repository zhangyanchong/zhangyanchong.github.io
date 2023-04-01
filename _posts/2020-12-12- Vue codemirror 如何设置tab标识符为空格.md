---
layout: post
title: Vue  如何设置tab标识符为空格
categories: js
description: js
keywords: codemirror,iOS,safari,回弹效果,橡皮筋效果
---

### 1、在使用codemirror 过程中，编辑代码时候发现按tab 键出现标识符---> 可以使用标识符替换成空字符
```js
    mounted() {
    // fix tab
    this.codemirror.options.extraKeys = {
      Tab: function(cm) {
        var spaces = Array(cm.getOption('indentUnit') + 1).join(' ');
        cm.replaceSelection(spaces);
      }
    };
  },
  ```


