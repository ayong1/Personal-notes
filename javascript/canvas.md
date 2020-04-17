### canvas

1. #### html5新增的标签<canvas>

2. #### 初始化可以设置一下宽高和背景色：

   1. ```html
      <canvas id="test-canvas" width="300" height="200" style="background-color:hotpink">
      	<p>您的浏览器不支持canvas</p> <!-- 由于有的浏览器不支持，所以我们给出提示，增加用户体验 -->
      </canvas>
      ```

3. #### 使用==js==代码操作canvas

   1. ```js
      var canvas = document.getElementById('test-canvas');
      var ctx = canvas.getContext('2d');
      //  var ctx = canvas.getContext("webgl");------这是绘制3D
      
      ```

   2. #### 实例

      ```js
      /** @type {HTMLCanvasElement} */
            let canvas = document.getElementById("test-canvas");
            let ctx = canvas.getContext("2d");
            var path = new Path2D();
            path.arc(75, 75, 50, 0, Math.PI * 2, true);
            path.moveTo(110, 75);
            path.arc(75, 75, 35, 0, Math.PI, false);
            path.moveTo(65, 65);
            path.arc(60, 65, 5, 0, Math.PI * 2, true);
            path.moveTo(95, 65);
            path.arc(90, 65, 5, 0, Math.PI * 2, true);
            ctx.strokeStyle = 'orange';
            ctx.stroke(path); // 运行结果为笑脸
      ```

   3. #### 
