### Promise（主要解决回调地狱）

1. #### 代码格式：

   1. ```js
      let p1 = new Promise(function (resolve, rehect) {});
      let p2 = new Promise(function (resolve, rehect) {});
      Promise.all([p1, p2])
          .then(function () {},function(){})
          .catch(function () {});
      ```

   2. #### 注意：jQuery中的ajax返回的值就是一个Promise对象

      1. ```js
         Promise.all([
         	$.ajax('GET','xxxxx.com',dataType:'json'),
             $.ajax('GET','xxxx2.com',dataType:'json')
         ]).then(function () {})
           .catch(function () {});
         ```


      