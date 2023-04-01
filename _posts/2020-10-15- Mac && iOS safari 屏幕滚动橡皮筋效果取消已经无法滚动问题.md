---
layout: post
title: Mac && iOS safari 屏幕滚动橡皮筋效果取消已经无法滚动问题
categories: mac
description: Mac,iOS
keywords: Mac,iOS,safari,回弹效果,橡皮筋效果
---

### 1、ios的橡皮筋效果会带来一些莫名其妙的bug。如果直接对body禁止的话，那整个页面都无法滑动了。所以我今天带来一个解决方案

```js
mounted() {
    let self = this;
    let ios = navigator.userAgent.indexOf('iphone');// 判断是否为ios
    document.body.addEventListener('touchstart', self.handleStart, { passive: false });
    if (ios === -1) {
      // ios下运行
      let el = document.querySelector('#box');// 需要滑动的dom元素
      iosTrouchFn(el);
    }
    function iosTrouchFn(el) {
      // el需要滑动的元素
      el.addEventListener('touchmove', function(e) {
        e.isSCROLL = true;
      });
      document.body.addEventListener('touchmove', self.handleMove, { passive: false }); // passive防止阻止默认事件不生效
    }
  },
  ```

  ```js
  methods: {
    // 滑动开始获取初始位置坐标
    handleStart(e) {
      console.log('开始', e.touches[0].pageY);
      this.scrollDirection.startY = e.touches[0].pageY;
    },
    // 滑动距离
    handleMove(e) {
      console.log('move', e.targetTouches[0].pageY);
      let el = document.querySelector('#box');// 需要滑动的dom元素这个为包裹滑动元素的父元素
      if (!e.isSCROLL) {
        e.preventDefault(); // 阻止默认事件(上下滑动)
        console.log('阻止了');
      } else {
      // 需要滑动的区域
        let moveY = e.touches[0].pageY;
        let top = el.scrollTop;
        let ch = el.clientHeight;// 对象最顶端和窗口最顶端之间的距离
        let scrollH = el.scrollHeight; // 含滚动内容的元素大小
        if ((top === 0 && moveY > this.scrollDirection.startY) || (top + ch === scrollH && moveY < this.scrollDirection.startY)) {
          this.scrollDirection.showBtnText = true;
          e.preventDefault();
          console.log('阻止了');
        } else {
          console.log('开启了');
        }
      }
    },
    // handleEnd(e) {
    //   console.log('结束', e);
    // },
```
```js
  beforeDestroy() {
    let self = this;
    document.body.removeEventListener('touchstart', self.handleStart, { passive: false });
    document.body.removeEventListener('touchmove', self.handleMove, { passive: false });
  }
 ```