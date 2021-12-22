- Q:在element中，遇到一种情况，当使用时间选择器，并对其赋值后，v-model双向绑定失效，无法继续选择日期
- A: 
  ```js
  // this.$set 第一个参数是要修改的对象， 第二个参数就是 这个对象里面的属性，也是本次要修改的具体值， 第三个参数是要设置的内容
  this.$set(this.mainForm, 'beginDate' , new Date())
  // 
  this.mainForm.beginDate = res.data.beginDate
  ```