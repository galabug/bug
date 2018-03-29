### 1.window.requestAnimationFrame() [请求动画帧] 告诉浏览器执行动画并请求浏览器在下一次重绘之前调用指定的函数来更新动画。该方法使用一个回调函数作为参数，这个回调函数会在浏览器重绘之前调用。
  - 注意：若您想要在下次重绘时产生另一个动画画面，您的回调例程必须调用 requestAnimationFrame()。
  #### 语法
  > window.requestAnimationFrame(callback);

  - 参数 callback

  > 该函数在下次重新绘制动画时调用。这个回调函数只有一个传参，timeStamp，指示requestAnimationFrame()  开始触发回调函数的当前时间（performance.now() 返回的时间）。

  - 返回值

  一个 long 整数，是个非零值，没别的意义。你可以传这个值给 window.cancelAnimationFrame() 以取消回调函数。


### 普及下缓动(Tween)知识吧：

    - Linear：无缓动效果
    - Quadratic：二次方的缓动（t^2）
    - Cubic：三次方的缓动（t^3）
    - Quartic：四次方的缓动（t^4）
    - Quintic：五次方的缓动（t^5）
    - Sinusoidal：正弦曲线的缓动（sin(t)）
    - Exponential：指数曲线的缓动（2^t）
    - Circular：圆形曲线的缓动（sqrt(1-t^2)）
    - Elastic：指数衰减的正弦曲线缓动
    - 超过范围的三次方缓动（(s+1)*t^3 – s*t^2）
    - 指数衰减的反弹缓动

#### 每个效果都分三个缓动方式，分别是（可采用后面的邪恶记忆法帮助记忆）：

    - easeIn：从0开始加速的缓动，先慢后快的；
    - easeOut：减速到0的缓动，先快后慢
    - easeInOut：前半段从0开始加速，后半段减速到0的缓动，先慢后快然后再慢。