### 1.window.requestAnimationFrame() 方法告诉浏览器您希望执行动画并请求浏览器在下一次重绘之前调用指定的函数来更新动画。该方法使用一个回调函数作为参数，这个回调函数会在浏览器重绘之前调用。
  - 注意：若您想要在下次重绘时产生另一个动画画面，您的回调例程必须调用 requestAnimationFrame()。
  #### 语法
  > window.requestAnimationFrame(callback);

  - 参数 callback

  > 该函数在下次重新绘制动画时调用。这个回调函数只有一个传参，timeStamp，指示requestAnimationFrame()  开始触发回调函数的当前时间（performance.now() 返回的时间）。

  - 返回值

  一个 long 整数，是个非零值，没别的意义。你可以传这个值给 window.cancelAnimationFrame() 以取消回调函数。
