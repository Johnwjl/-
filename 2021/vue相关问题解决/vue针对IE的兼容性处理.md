### vue 针对 IE 的兼容性处理

#### 1. main.js 中 引入 ' babel-polyfill '

- ``` js
  import 'babel-polyfill'
  ```

#### 2. main.js 中 引入 ' es6-promise '

- ```js
  require('es6-promise').polyfill()
  require('es6-promise/auto')
  ```

#### 3.  .babelrc 文件中 

- ```js
  "useBuiltIns" : "entry"
  ```

#### 4. webpack.base.conf.js 文件中

- ```js
  // 在 module.exports 中
  entry : {
    	// 此处加上 babel-polyfill  
      app: ['babel-polyfill','./src/main.js']
  }
  
  ...
  
  	// 在 module -> rules -> babel-loader
  	include: [
          resolve('node_modules/element-ui/src')
          resolve('node_modules/element-ui/packages')
      ]
      // 此处写好要重新编译项目 npm run build
  ```

#### 5. 在入口 index.html

- ```html
  <!–[if lt IE 10]>
  请使用谷歌浏览器访问
  <![endif]–>
  ```

#### 6. js 判断浏览器

- ```js
  function isIE() { //ie?
   if (!!window.ActiveXObject || "ActiveXObject" in window)
    return true;
    else
    return false;
   }
  ```

- ```js
  function isIE(){
  if (window.navigator.userAgent.indexOf("MSIE")>=1) 
  return true; 
  else
  return false; 
  }
  ```

- ```js
  function IEVersion() { var userAgent = navigator.userAgent; //取得浏览器的userAgent字符串 var isIE = userAgent.indexOf("compatible") > -1 && userAgent.indexOf("MSIE") > -1; //判断是否IE<11浏览器 var isEdge = userAgent.indexOf("Edge") > -1 && !isIE; //判断是否IE的Edge浏览器 var isIE11 = userAgent.indexOf('Trident') > -1 && userAgent.indexOf("rv:11.0") > -1; if(isIE) { var reIE = new RegExp("MSIE (\\d+\\.\\d+);"); reIE.test(userAgent); var fIEVersion = parseFloat(RegExp["$1"]); if(fIEVersion == 7) { return 7; } else if(fIEVersion == 8) { return 8; } else if(fIEVersion == 9) { return 9; } else if(fIEVersion == 10) { return 10; } else { return 6;//IE版本<=7 } } else if(isEdge) { return 'edge';//edge } else if(isIE11) { return 11; //IE11 }else{ return -1;//不是ie浏览器 } }
  ```

- 

