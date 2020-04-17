### AJAX（Asynchronous JavaScript and XML ）

1. #### 一般多用于异步请求数据，提升用户体验

2. #### 由于兼容性的问题，在多数浏览器中用==XMLHttpRequest==，在低版本IE中需要用==ActiveXObject==

   #### 兼容代码的写法：

   ```js
   function success(text) {
       //  ...
       //  ...
   }
   
   function fail(code) {
       //  ...
       //  ...
   }
   var request;
   if(window.XMLHttpRequest){
       request = new XMLHttpRequest();
   }else{
       request = new ActiveXObject;
   }
   request.onreadystatechange = function(){  // 状态发生变化时，函数被回调
       if(request.readyState === 4){  // 成功完成 
           // 判断响应结果:
           if(request.status == 200 || request.status == 304){
               // 成功，通过responseText拿到响应的文本:
               return success(request.responseText); //  这里的success是一个回调函数
           }else{
               // 失败，根据响应码判断失败原因:
               return fail(request.status);
           }
       }
   }
   // 发送请求:
   request.open('GET', 'dayongge.xyz');
   request.send();
   alert('请求已发送，请等待响应...');
   ```

3. #### 原生js解决跨域问题（jsonp）：只能用GET请求 ，并且要求返回JavaScript 

   1. #### 这种方式跨域实际上是利用了浏览器允许跨域引用JavaScript资源

   2. ```js
      <html>
      <head>
          <script src="http://example.com/abc.js"></script>
          ...
      </head>
      <body>
      ...
      </body>
      </html>
      ```

   3. #### ==注意==：需要在请求的最后加上回调函数（http://www.dayongga.xyz?callback=backValue）

   4. ```js
      //回调函数
      function backValue(data) {
          //请求接口，返回json数据
          console.log(data.name);
          console.log(data.age);
          console.log(data.sex);
      }
      //自定义函数并且去请求接口来完成回调函数的数据读取
      function getDate() {
          var
              js = document.createElement('script'),
              head = document.getElementsByTagName('head')[0];
          js.src = 'http://dayongge.xyz?callback=backValue';  //如果成功拿到数据，会调用backValue函数
          head.appendChild(js);
      }
      ```
      


