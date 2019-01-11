#vue创建组件的第一种方法
创建好的组件，把组件的名称，以HTML标签的形式，引入到页面中就ok了
<div id="#app">
	<compont1></compont1>
</div>
创建vue的组件(如果是驼峰的写法那么标签要变成—小写)
Vue.component('compon1',Vue.extend({
	template: '<h3>创建vue组件的第一种方法</h3>'
}));

#创建组建的第二种方法

<div id="#app">
	<compont2></compont2>
</div>
创建组件的第二种方法 直接创建一个json对象
Vue.component('compon2',{
	template: '<div><h2>创建组件的第二种方法</h2><p>第二种</p></div>'
});

#创建组件的第三种方法

 <div id="app">
  <conpon3 id="show">
  	<div>
      <h3>创建组件的第三种方法</h3>
  	  <p>第三种方法</p>
  	</div>
  </conpon3>
 </div>
创建组件的第二种方法  
  Vue.component('conpon3',{
   	 template: '#show'
  })

------------------以上都是创建全局性的组件-----------
 #创建私有组件的方法
  <div id="app">
    <mycom3 id="temp1">
      <div>
         <p>私有组件的创建</p>
      </div>
    </mycom3>
    <login id="tmp12">
       <div>
         <p>这是私有的 login 组件</p>
       </div>
    </login>
  </div>
    Vue.component('mycom3', {
      template: '#temp1'
    })

    var vm = new Vue({
      el: '#app',
      data: {},
      components: { // 定义实例内部私有组件的
        login: {
          template: '#tmp12'
        }
      }
    });

#组件中的data的使用
  <div id="app">
    <zong id="zong1">
      <p>你----{{msg}}------你</p>
    </zong>
  </div>

  Vue.component('zong',{
     template: '#zong1',
     data: function(){
      return {
        msg: '这是组件中data的使用'
      }
     }
  });

  // 创建 Vue 实例，得到 ViewModel
  var vm = new Vue({
    el: '#app',
    data: {msg:''},
    methods: {}
  });

#组件中methods的使用

  <div id="app">
     <counter id='tmpl'>
       <div>
      <input type="button" value="点我数字加1" @click="add">
      <h3>{{count}}</h3>
    </div>
     </counter>
     <counter id='tmpl'>
       <div>
      <input type="button" value="点我数字加1" @click="add">
      <h3>{{count}}</h3>
    </div>
     </counter>
     <counter id='tmpl'>
       <div>
      <input type="button" value="点我数字加1" @click="add">
      <h3>{{count}}</h3>
    </div>
     </counter>
  </div>

  var dataObj = { count: 0}
  Vue.component('counter', {
    template: '#tmpl',
    data: function(){
      return { count: 0 }
    },
    methods:{
      add(){
        this.count++
      }
    }
  })
  // 创建 Vue 实例，得到 ViewModel
  var vm = new Vue({
    el: '#app',
    data: {},
    methods: {}
  });

#两个组件之间的切换
  <div id="app">
    <a href="" @click.prevent="flag=true">登录</a>
    <a href="" @click.prevent="flag=false">注册</a>
    
    <first v-if="flag"></first>
    <second v-else="flag"></second>
  </div>

  Vue.component('first', {
    template: '<h3>登录组件</h3>'
  }
  Vue.component('second', {
    template: '<h3>注册组件</h3>'
  }
  // 创建 Vue 实例，得到 ViewModel
  var vm = new Vue({
    el: '#app',
    data: {
      flag:true
    },
    methods: {}
  });

 #多个组件之间的切换
 <div id="app">
   <a href="" @click.prevent="comName='first'">登录</a>
   <a href="" @click.prevent="comName='second'">注册</a>
   <a href="" @click.prevent="comName='three'">退出</a>
 
   <!-- vue提供了 componnet 来展示对应的组件 -->
   <!-- component 是一个占位符，:is属性可以用来指定要展示的组建的名称 -->
   <component :is="comName"></component>
 </div>


  Vue.component('first', {
   template: '<h3>登录组件</h3>'
 });

 Vue.component('second', {
   template: '<h3>注册组件</h3>'
 });

 Vue.component('three', {
   template: '<h3>退出组件</h3>'
 });

 // 创建 Vue 实例，得到 ViewModel
 var vm = new Vue({
   el: '#app',
   data: {
     comName:'first'
   },
   methods: {}
 });