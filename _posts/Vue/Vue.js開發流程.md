---
layout: post
title:  基礎vue.js 概述
category: Vue出一個電商網站
description: 介紹vue.js基本基本
---

# 基礎vue.js 概述

[課程網頁](https://www.udemy.com/vue-hexschool/)

[課程練習手冊](https://github.com/hexschool/vue-exercise/tree/gh-pages)

[vuejs簡體中文主頁](https://cn.vuejs.org/)

[Google Chrome Extension—vue-dev-tools](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)



### 建立vue的應用程式

Vue 應用程式建立起手式

```vue
<div id = app>
  {{text}}
</div>

<script>
  var app = new Vue({
  el: '#app',  // #是選取方式 in html 
     				// el是element的縮寫，Vue綁定的方法
  data: {
    text: '這是一段話'
  }
});

</script> 
```

-  App會放進一個object，內容是optional的
-  Vue的資料必須綁定再一個html 元素裡面(id,class..)
-  除了可以用id來綁定外，也可以用class來綁定
-    `{{text}}` 獲取 app內的`data`  的資料
-  一個網頁可以生成多個vue應用程式，但不可以巢狀nested





### MVVM是什麼樣的概念

![MVVMPattern.png](https://upload.wikimedia.org/wikipedia/commons/8/87/MVVMPattern.png)

-  **Model-view-viewmodel**
   -  **MODEL（模型）**
      -  資料存取層, 以資料為中心
   -  **VIEW(視圖)**
      -  用戶在螢幕上看到的結構，佈局，外觀（structure, layout, and appearance)
   -  **VIEW MODEL**
      -  (自動綁定)The view model is an abstraction of the view exposing public properties and commands. 



-  如果要串連資料
   -  可以使用雙花括號(Mustache) `{{mustache}}`
   -  可以使用`v-text` or `v-html` directive
   -  You can use the ***v*-*model*** directive to create **two-way data bindings** on form *input*, *textarea*, and *select* elements.

```js
<div id="app">
   // 串連資料from Vue Appliation
  {{message}} 
  //以文字方式輸出'message'
  <div v-text="message"></div>
//以html方式輸出'message'
  <div v-html="message"></div> 

// use v-model to do the two-way binding
  <input type="text" v-model="message"> 
</div>

<script>
var app = new Vue({
  el: '#app',
  // 在此建立資料內容

  data: {
    message: '<span>哈囉</span>'
  }
})

```

VUE JS 以**資料狀態**操作**畫面**

### v-bind 動態屬性指令

使用`v-bind`去綁定html的屬性(attribute)

```html
<div id="app">
  <img v-bind:src="imgSrc" v-bind:class="className" alt="">
</div>


<script>
var app = new Vue({
  el: '#app',
  data: {
    imgSrc: 'https://images.unsplash.com/photo-1479568933336-ea01829af8de?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=d9926ef56492b20aea8508ed32ec6030&auto=format&fit=crop&w=2250&q=80',
    className:'img-fluid'
  }
})
</script>
```

### v-for動態產生多筆資料於畫面上

使用`v-for` 和 `v-if` 去 進行去transverse array 和 進行資料篩選（filtering）

**v-if directive**

>  The directive `v-if` is used to conditionally render a block. The block will only be rendered if the directive’s expression returns a truthy value.

**v-for directive**

>  We can use the `v-for` directive to render a list of items based on an array. The `v-for`directive requires a special syntax in the form of `item in items`, where `items` is the source data array and `item` is an **alias** for the array element being iterated on:
>  
```html
<div id="app">
  <pre>{{list}}</pre>
  <ul>
    <li v-for="(item,index) in list" 
        v-if="item.age<25" >
       <!-- item 變數名稱 是自定義的，similar to for each-->
      {{index + 1}}. {{item.name}} 年齡是 {{item.age}}
    </li> 
  </ul>
</div>

<script>
var app = new Vue({
  el: '#app',
  data: {
    list: [
      {
        name: '小明',
        age: 16
      },
      {
        name: '媽媽',
        age: 38,
      },
      {
        name: '漂亮阿姨',
        age: 24
      }
    ]
  }
})
</script>
```

### 使用v-for操作頁面行為

**v-on directive**

>  We can use the `v-on` directive to listen to DOM events and run some JavaScript when they’re triggered.

```html
<div id="app">
  <input type="text" class="form-control" v-model="text">
  <button class="btn btn-primary mt-1" v-on:click="reverseText">反轉字串</button>
  <div class="mt-3">
    {{ newText }}
  </div>
</div>

<script>


var app = new Vue({
  el: '#app',
  data: {
    text: '',
    newText: ''
  },
  // 請在此撰寫 JavaScript
  methods: {
    reverseText: function(){
      console.log('點我', this.text);
      this.newText = this.text.split('').reverse().join('');
    }
  },
});
</script>
```

-  要預先定義資料狀態(newText的)



### 透過修飾符，讓v-on操作更簡單

-  如將button改為 a href="#" 時
   -    `<a href="#" class="btn btn-primary mt-1">反轉字串</a>`
   -  當按下這個hyperlink時，畫面會向最上移動
   -  可透過evt.preventDefault() 操作

```js
methods: {
     reverseText(event) {
     console.log(event);
     event.preventDefault();
     this.newText = this.text.split('').reverse().join('');
     }
  }
```

可以透過modifier `v-on:click.prevent` 代替以上代碼

```js
  <a href="#" class="btn btn-primary mt-1" v-on:click.prevent="reverseText">反轉字串</a>


  <a href="#" class="btn btn-primary mt-1" @click.prevent="reverseText">反轉字串</a>

 methods: {
    reverseText(){
    this.newText = this.text.split('').reverse().join('');
}
```

-   `@click.prevent` 可用來代替 `v-on:click.prevent`
-  `:src`可用來代替`v-bind:src`



### v-class動態切換className

```html
<div id="app">
  <div class="box" :class="{'rotate': isTransform}"></div> 
   <!-- 
		:class="{className : condiition}"
		add specfic className when paricular conditon fulfilled 
--> 
   
  <hr>
  <button class="btn btn-outline-primary" @click="isTransform = !isTransform">選轉物件</button>
    <!-- 
		click to toggle status of isTransform
--> 
</div>

<script>
var app = new Vue({
  el: '#app',
  data: {
    isTransform: false
  },
});
</script>

<style>
.box {
  transition: transform .5s;
}
.box.rotate {
  transform: rotate(45deg)
}
</style>
```

### 計算（Computed）屬性

-  容易維護
-  以系統的方式表達複雜邏輯運算

```js
<div id="app">
  <input type="text" class="form-control" v-model="text">
  <button class="btn btn-primary mt-1">反轉字串</button>
  <div class="mt-3">
    {{ text.split('').reverse().join('') }}
  </div>
  {{reverseText}}
</div>

<script>
var app = new Vue({
  el: '#app',
  data: {
    text: '',
    newText: ''
  },
  // 請在此撰寫 JavaScript
  computed: {
    reverseText: function(){
      return this.text.split('').reverse().join('');
       //this.text points to data中的text
    }
  }
});
</script>
```

### Methods 與 Computed 的使用情境

- computed 是在==監控資料更動==後，重新運算結果呈現於畫面上
一般來說**不會修改資料**，只會回傳用於**畫面呈現的資料** 

- methods 就是互動的函式，需要觸發才會運作
會用來修改資料內容

-  效能
   -  如果資料量大，computed 自然會比較慢
      -  只要資料變動就會觸發，無形之中執行次數也會增加
         因此在大量資料時，會建議透過 methods 減少不必要的運算喔



### Vue 表單與資料的綁定

-  當表單中的資料（text,raido, checkbox）有更動時，data中的也會dynamically 改變

```html
<script>
var app = new Vue({
  el: '#app',
  data: {
    text: '',
    textarea: '',
    checkbox1: false,
    checkboxArray: [],
    singleRadio: '',
    selected: '',
  },
});
</script>
```

```html
與text綁定 
<input type="text" class="form-control" v-model="text">
與textArea綁定
<textarea cols="30" rows="3" class="form-control" v-model="textarea"></textarea>

checkbox中的選取的data與checkboxArray綁定 （以array呈現）
  <div class="form-check">
    <input type="checkbox" class="form-check-input" id="check2" v-model="checkboxArray" value="雞">
    <label class="form-check-label" for="check2">雞</label>
  </div>
  <div class="form-check">
    <input type="checkbox" class="form-check-input" id="check3" v-model="checkboxArray" value="豬">
    <label class="form-check-label" for="check3">豬</label>
  </div>
  <div class="form-check">
    <input type="checkbox" class="form-check-input" id="check4" v-model="checkboxArray" value="牛">
    <label class="form-check-label" for="check4">牛</label>
  </div>
  <p>晚餐火鍋裡有 <span v-for="item in checkboxArray">{{item}}</span> 。 </p>


radio type中的data與 singleRadio 綁定
 <div class="form-check">
    <input type="radio" class="form-check-input" id="radio2" v-model="singleRadio" value="雞">
    <label class="form-check-label" for="radio2">雞</label>
  </div>
  <div class="form-check">
    <input type="radio" class="form-check-input" id="radio3" v-model="singleRadio"  value="豬">
    <label class="form-check-label" for="radio3">豬</label>
  </div>
  <div class="form-check">
    <input type="radio" class="form-check-input" id="radio4" v-model="singleRadio"  value="牛">
    <label class="form-check-label" for="radio4">牛</label>
  </div>
  <p>晚餐火鍋裡有 {{singleRadio}} </p>


select中的option data與selected綁定
  <h4>Select</h4>
  <select name="" id="" class="form-control" v-model="selected">
    <option value="" disabled> -- 請選擇-- </option>
    <option value="小明"> 小明 </option>
    <option value="小美">漂亮的小美 </option>
```



### 元件 Components

```vue
<div id="app">
  <div>
    你已經點擊 <button class="btn btn-outline-secondary btn-sm" @click="counter += 1">{{ counter }}</button> 下。
    你已經點擊 <button class="btn btn-outline-secondary btn-sm" @click="counter += 1">{{ counter }}</button> 下。
    <counter-component> </counter-component> 
    <counter-component> </counter-component>
    <counter-component> </counter-component>
  </div>
</div>

Vue.component('counter-component',{
  data: function(){
    return {
      counter: 0
    }
  },
  template:`
  <div> 
      <button class="btn btn-outline-secondary btn-sm" @click="counter += 1">{{ counter }}</button>
    </div>
  `
});

var app = new Vue({
  el: '#app',
  data: {
    counter: 0
  },
});
```

-   <counter-component> </counter-component> 用來插入Components
-  在Components裡面，data:要寫成 data:function(){return  counter:0 }
-  利用`template`和`` 編寫要插入的程式碼
-  每個Components的data是獨立的 （可參考vue的developer tools）