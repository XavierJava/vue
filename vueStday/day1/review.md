# vue 第二天和第三天的复习

## vue的基本代码结构(vue2)
   <p>{{msg}}</p>

## vue的插值表达式 (vue2)
   <p v-cloak>{{msg}}</P>解决内容闪烁问题

## vue指令v-text和vue-html(vue2)
   <p v-text="msg"></p>
   <p v-html="msg"></p>
   data : {msg : "<span>ni</span>"}

## vue绑定属性指令v-bind 简写是 :(vue21)
<input type="text" :title="myTitle + 课追加内容">
  data : {myTitle : "123"}

## 函数事件指令 v-on 缩写 $ (vue22)
   <p $click="show"></p>
   methods : {show(){alert(12);}es6写法} 
   
   methods : {show : function(){alert(12);}常规写法} 

## vue的事件修饰符(vue23)

###事件修饰符   
  * .stop  阻止冒泡  一般 
  <div $click="show1">
    <p $click.stop="show2"></p>
  <div>

  * .prevent 阻止默认行为
  <a href="#" @click.prevent="show"></a>
  只是点击事件 不出现默认的跳转事件

  * .capture 捕获机制修饰符  从外往里
  <div $click.capture="show1">
    <p $click.stop="show2"></p>
  <div>
  
  * .self 只有我自身才能出触发的事件
  <div id="app" @click.self="fathershow">
  	 <input type="button" value="点击" @click="childshow">
  </div> -->

  * .once 使用.once 事件 只触发一次 <div id="app">
  <a href="www.baidu.com" @click.prevent.once="linkClick"> 阻止默认跳转行为</a>
  </div>

  ## Vue指令v-model可以实现表单的双向数据绑定(vue24)(vue25)

   <div>
      <input type="text" v-model="msg">
   </div>

   ##在vue中使用样式(vue3)(vue31)

   ### 1.数组法

   <p :class="['red',"font"]">段落</p>
   
   ### 2.使用三元表达式

   <p :class="['red','font',flag?'active':'']">段落</p>

   ### 3.对象写法代替三元表达式

   <p :class="['red','font',{'active':flag}]">段落</p>

   ### 4.直接对象写法

   <p :class="class1,class2">段落</p>
   data : {
      class1 : " red : true, font : false",
      class2 : " active : true"
   }
  ##vue指令v-for

   ### 抵袋数组(vue32)(vue33)
   <ul>
     <li v-for="(item, i) in list">i索引号 item数组里面的值 list数组名</li>
   </ul>

   ### 抵袋对象中的属性(vue34)
   key就是id name . val是 1 任伦 412 i是索引
   <div v-for="(val, key, i) in userInfo">val.id会迭代出所有Id号 i会迭代出三次所有的对象</div>
    data : {
           user : {
            id : 1,
            name : "任伦",
            grode : 412 
           }
        }

    ### 抵袋数字(vue34)
    v-for 指令就是count就是相当于i in后面我们可以放 普通数组 对象 还可以放置数字  但是数字是从1开始
    <p v-for="i in 10">这是第 {{i}} 个P标签</p>

    ### **当在组件中使用** v-for 时，key 现在是必须的。

  ## Vue指令v-if和v-show(vue36)

  <input type="button" @click="flag=!flag" value="点击">
  <h3 v-if="flag">这是v-if控制的元素</h3>
  <h4 v-show="flag">这是v-show控制的元素</h4>
  v-if 有更高的切换消耗而 v-show 有更高的初始渲染消耗。因此，如果需要频繁切换 v-show 较好，如果在运行时条件不大可能改变 v-if 较好