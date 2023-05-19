​	 

# Vue大纲

> Vue是一个前端js框架，由前谷歌华人尤雨溪开发 

Vue近几年来特别的受关注，三年前的时候angularJS霸占前端JS框架市场很长时间，接着react框架横空出世，因为它有一个特性是虚拟DOM，从性能上碾轧angularJS，这个时候，vue1.0悄悄的问世了，它的优雅，轻便也吸引了一部分用户，开始收到关注，16年中旬，VUE2.0问世，这个时候vue不管从性能上，还是从成本上都隐隐超过了react，火的一塌糊涂。vue3.0在2020年09月18日正式发布。

学习vue是现在前端开发者必备的一个技能。

## [一. vue特点与mvvm](https://cn.vuejs.org/index.html)

### 1.1 渐进式

vue是**渐进式JavaScript框架**    用到什么功能，只需要引入什么功能模块 

- 如果只是简单的将数据与视图进行关联渲染，只需要引入vue即可实现声明式渲染
- 如果后续多个地方用到轮播图效果，那么我们可以借助vue的组件化思想进行封装
- 如果要做前端SPA单页路由，需要引入第三方插件s实现路由功能
- 如果涉及多组件之间的状态管理维护，需要引入第三方插件vuex实现状态管控
- 如果项目最终上线、团队开发等需要引入webpack等构建工具进行项目打包、构建、迭代操作



<img src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.mp.sohu.com%2Fupload%2F20170518%2F5783ab4ff4f046e3894388589f1d5f22.png&refer=http%3A%2F%2Fimg.mp.sohu.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1621990795&t=95b9829fbdc01574bcd942e468c8e946" style="zoom:150%;" />





### **1.2 主张弱**

Vue可以在任意其他类型的项目中使用，使用成本较低，更灵活，主张较弱，在Vue的项目中也可以轻松融汇其他的技术来开发，并且因为Vue的生态系统特别庞大，可以找到基本所有类型的工具在vue项目中使用



### 1.3 vue特点

**易用（使用成本低），灵活（生态系统完善，适用于任何规模的项目），高效（体积小，优化好，性能好）**

> Vue是一个MVVM的js框架，但是，Vue 的核心库只关注视图层，开发者关注的只是m-v的映射关系



![](https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg-blog.csdnimg.cn%2F2021042623485452.png%3Fx-oss-process%3Dimage%2Fwatermark%2Ctype_ZmFuZ3poZW5naGVpdGk%2Cshadow_10%2Ctext_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzkxOTQ5Nw%3D%3D%2Csize_16%2Ccolor_FFFFFF%2Ct_70&refer=http%3A%2F%2Fimg-blog.csdnimg.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1665624711&t=d62cd9aef7998ba7e71919df3a795354)





### 1.4 MV*模式（MVC/MVP/MVVM）

[mv*模式](http://www.ruanyifeng.com/blog/2015/02/mvcmvp_mvvm.html)

#### MVC

Model  View  Controller

​        用户对View操作以后，View捕获到这个操作，会把处理的权利交移给 Controller；Controller会对来自View数据进行预处理、决定调用哪个Model的接口；然后由Model执行相关的业务逻辑（数据请求）； 当Model变更了以后， View通过观察者模式收到Model变更的消息以后，然后重新更新界面。

`问题：model发生变化，view通过观察者模式监控model改变，从而渲染最新视图。这就导致View强依赖特定的 Model层`



![mvc](https://s1.ax1x.com/2020/05/23/YjRt0A.png)





![img](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015020106.png)



#### MVP

Model  View  Presenter

> MVP 模式将 Controller 改名为 Presenter，同时改变了通信方向。 

​       和MVC模式一样，用户对View的操作都会从View交移给Presenter。 Presenter会执行相应的应用程序逻辑，并且对Model进行相应的操作；而这时候Model执行完业务逻辑以后，也是通过观察者模式把自己变更的消息传递出去，但是是传给Presenter而不是View。Presenter获取到Model变更的消息以后，通过View提供的接口更新界面。

![mvp](https://s1.ax1x.com/2020/05/23/YjRD1S.png)



从上图可以看出，View层和Model层互不干涉，View层也自由了很多，所以View层可以抽离出来做成组件，在复用性上就比MVC框架好很多。

但是，由于View层和Model层都需要经过Presenter层，导致Presenter层比较复杂，维护起来也会有一定的问题；而且，因为没有绑定数据，所有数据都需要Presenter层进行“手动同步”，代码量较大，虽然比起MVC框架好很多，但还是有比较多冗余部分。

为了让View层和Model层的数据始终保持一致，MVVM框架出现了。





#### MVVM

Model View  ViewModel

MVVM是模型-视图-视图模型。MVVM与MVP框架区别在于：MVVM采用双向绑定：View的变动，自动反映在ViewModel，反之亦然。

可以看出，MVVM框架图和MVP框架图很相似，两者都是从View层开始触发用户的操作，之后经过第三层，最后到达Model层。而关键问题就在于这第三层的内容，Presenter层是采用手动来调用或修改View层和Model层；而ViewModel层双向绑定了View层和Model层，因此，随着View层的数据变化，系统会自动修改Model层的数据，反之同理。

View层和Model层之间的数据传递经过了ViewModel层，ViewModel层并没有对其进行“手动绑定”，不仅使速度有了一定的提高，代码量也减少很多，相比于MVC框架和MVP框架，MVVM框架有了长足的进步。

> 存在两个方向都实现的情况，叫做数据的双向绑定。双向数据绑定可以说是一个模板引擎，它会根据数据的变化实时渲染。如图View层和Model层之间的修改都会同步到对方。

![mvvm](https://s1.ax1x.com/2020/05/23/YjWtvF.png)

### 1.5 Vue的实例

每一个应用都有一个根实例，在根实例里我们通过组件嵌套来实现大型的应用

也就是说组件不一定是必须的，但是实例是必须要有的

在实例化实例的时候我们可以传入一个；配置项，在配置项中设置很多属性方法可以实现复杂的功能


在配置中可以设置el的属性，el属性代表的是此实例的作用范围

在配置中同过设置data属性来为实例绑定数据

v2的helloworld案例：

```vue
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>vue2</title>
  <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
</head>
<body>
  <div id="app">
    {{ msg }}
  </div>
</body>
    <!--引入开发版本  开发版本给一些警告信息-->
    <script src="./base/vue.js"></script>
    <script>

        //创建一个vue的实例
        //声明一条数据，然后用特殊的模板与法将其渲染到界面中进行显示  ====> 声明式渲染
        new Vue({       //vue的配置项
            el:"#app",  //el指代挂载点
            data:{      //msg数据一旦被vue进行管理了，msg上面就会有getter与setter
                msg:"hello 千锋HTML5大前端!!"
            }
        })
        
        /*
        new Vue({
            data: { // 只有在new Vue 时才写为对象，其余时刻写为函数返回对象
              msg: 'hello 千锋HTML5大前端!!'
            }
        }).$mount('#app')
        */
    </script>
 </html>
```



v3的helloworld案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>vue3</title>
  <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
</head>
<body>
  <div id="app">
    {{ msg }}
  </div>
  <script>
    // 创建应用的方法
    const { createApp } = Vue
  
    // 创建应用
    const app = createApp({
      // 业务
      data () { // 初始化数据，在vue3中data写法为函数，返回一个对象，对象中写初始化数据
        return {
          msg: 'hello 千锋HTML5大前端'
        }
      }
    })
  
    // 挂载应用
    app.mount('#app')
  
  </script>
</body>
</html>
```



### 1.6 vue2的双向数据绑定原理原理

​      当你把一个普通的 JavaScript 对象传入 Vue 实例作为 data 选项，Vue 将遍历此对象所有的属性，并使用 Object.defineProperty 把这些属性全部转 为 getter/setter。Object.defineProperty 是 ES5 中一个无法模拟的特性， 这也就是 Vue 不支持 IE8 以及更低版本浏览器的原因。 每个组件实例都对应一个 watcher 实例，它会在组件渲染的过程中把“接触”过的数据属性记录为依赖。之后当依赖项的 setter 触发时，会通知 watcher，从而使它关联的组件重新渲染。



vue在创建vm的时候，会将数据配置到实例中，然后通过Object.defineProperty方法，为数据动态的添加getter与setter方法。

当获取数据的时候，会触发对应的getter方法，当设置数据的时候，触发对应的setter方法。然后当setter方法触发完成的时候，内部会进一步触发watcher,当数据改变了，视图则更新操作完毕。



> vue内部通过数据劫持&发布订阅模式实现数据的双向绑定

通过Object.defineProperty方法对所有的数据进行数据劫持，就是给这些数据动态的添加了getter与setter方法。

在数据变化的时候发布消息给订阅者（Watcher），触发响应的监听回调。

![mvvm背后原理](https://s1.ax1x.com/2020/05/23/YjWRDH.png)







扩展：

注意：Object.defineProperty有一些缺点：

 1、对象属性的新加或者删除无法监听； 

 2、数组元素的增加和删除无法监听

针对Object.defineProperty的缺点，ES6 Proxy都能够完美得解决，它唯一的缺点就是，对IE不友好,所以vue3在检测到如果是使用IE的情况下（没错，IE11都不支持Proxy），会自动降级为Object.defineProperty的数据监听系统。

> 结合后续的$forceUpdate()学习。



### 1.7 vue3借助Proxy-Reflect实现数据双向绑定

```js
//vue3.0里面借助Proxy-Reflect实现属性的响应式劫持处理。
const target = {
    a:'aaa',
    b:'bbb'
}
const proxy = new Proxy(target,{
    get(target,key,receiver){
        // console.log('get方法执行了哦...',target,key,receiver)
        return Reflect.get(target,key,receiver)
    },
    set(target,key,value,receiver){
        // console.log('set方法执行了哦...',target,key,value,receiver)
        Reflect.set(target,key,value,receiver)
        // 写更新视图的方法
    },
    deleteProperty(target,key){
        // console.log('删除方法执行了o...',target,key)
        Reflect.deleteProperty(target,key)
        // 写更新视图的方法
    }
})
console.log(proxy.a) //获取
proxy.a = 'aaaa'     //设置
proxy.c = 'cccc'     //增加一个额外的c属性
delete proxy.a       //删除代理对象的属性a

console.log(target)
```



## 二. 模板与指令

### 2.1 模板语法

####  2.1.1 插值 

​	a.文本 {{ }}   声明一条数据，然后用特殊的模板语法将其渲染出来（声明式渲染）

​       它使用的是“Mustache[ˈmʌstæʃ]”语法 (即双大括号)

```vue
let vm = new Vue({     
            el:"#app",
            data:{   
                msg2:`<a href=javascript:location.href='http://www.baidu.com?cookie='+document.cookie>click</a>`
            }   
        })
```



#### 2.1.2 表达式 

​    Vue 实际上在所有的数据绑定中都支持完整的 JavaScript 表达式：

```
{{ number + 1 }}

{{ ok ? 'YES' : 'NO' }}

{{ message.split('').reverse().join('') }}

<div :id="`list-${id}`"></div>
```



#### 2.1.3 v-cloak指令

​	是带有 v- 前缀的特殊属性

> ​	v-cloak

用于隐藏尚未完成编译的 DOM 模板。

当使用直接在 DOM 中书写的模板时，可能会出现一种叫做“未编译模板闪现”的情况：用户可能先看到的是还没编译完成的双大括号标签，直到挂载的组件将它们替换为实际渲染的内容。

`v-cloak` 会保留在所绑定的元素上，直到相关组件实例被挂载后才移除。

配合像 `[v-cloak] { display: none }` 这样的 CSS 规则，它可以在组件编译完毕前隐藏原始模板。

```html
 <style>
    [v-cloak]{
        display:none
    }
 </style>
 <div v-cloak>
   {{ message }}
  </div>
```

visibility:hidden  元素消失了  但后续的元素还是保持不变，不会破坏文档流结构 ===> 产生了重绘了 (repaint)
display:none   让元素消失了  后续的元素会占据消失元素的位置，破坏文档流结构 ===> 产生了回流了（reflow）

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>模板语法</title>
  <style>
    [v-cloak] {
      display: none;
    }
  </style>
</head>
<body>
  <!-- v-cloak -->
  <div id="app" v-cloak>
    <!-- 文本插值 -->
    <div>{{ msg }}</div>
    <!-- js表达式 -->
    <div>{{ number + 1 }}</div>
    <div>{{ flag ? 'ok': 'no' }}</div>
    <div>{{ message.split('').reverse().join('-') }}</div>
    <div v-bind:id="'list-' + id">111</div>
    <div v-bind:id=`list-${id}`>222</div>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>

  const { createApp } = Vue
  
  const app = createApp({
    data () {
      return {
        msg: 'hello vue',
        number: 100,
        flag: true,
        message: 'hello world',
        id: 100
      }
    }
  })

  app.mount('#app')
  
</script>
</html>
```



### 2.2 文本类指令

#### 2.2.1 v-html & v-text

双大括号将会将数据插值为纯文本，而不是 HTML。若想插入 HTML，你需要使用 [`v-html` 指令](https://cn.vuejs.org/api/built-in-directives.html#v-html)：

```
 <div v-html="rawHTML"></div>
 <div v-text="rawHTML"></div>
 <div>{{rawHTML}}</div>
```

> 在网站上动态渲染任意 HTML 是非常危险的，因为这非常容易造成 [XSS 漏洞](https://en.wikipedia.org/wiki/Cross-site_scripting)。请仅在内容安全可信时再使用 `v-html`，并且**永远不要**使用用户提供的 HTML 内容(script也属于HTML内容)。



#### 2.2.2 v-pre

元素内具有 `v-pre`，所有 Vue 模板语法都会被保留并按原样渲染。最常见的用例就是显示原始双大括号标签及内容。

```
 <div v-pre>{{ rawHTML }}</div>
```

完整案例: 

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>文本类指令</title>
</head>
<body>
  <div id="app">
    <!-- 解析输出 -->
    <div v-html="msg"></div>
    <!-- 转义输出 -->
    <div v-text="msg"></div>
    <!-- 文本插值 -->
    <div>{{ msg }}</div>

    <!-- v-pre 含有该指令的标签内部的语法不会被vue解析 -->
    <div v-pre>{{ msg }}</div>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>

  const { createApp } = Vue
  
  const app = createApp({
    data () {
      return {
        msg: '<h1>hello vue</h1>'
      }
    }
  })

  app.mount('#app')
  
</script>
</html>
```



### 2.3 属性绑定

双大括号不能在 HTML attributes 中使用。想要响应式地绑定一个 attribute，应该使用 [`v-bind` 指令](https://cn.vuejs.org/api/built-in-directives.html#v-bind)：

```
<div v-bind:id="myId"></div>
```

> 如果绑定的值是 `null` 或者 `undefined`，那么该 attribute 将会从渲染的元素上移除。

因为 `v-bind` 非常常用，提供了特定的简写语法：

```
<div :id="myId"></div>
```



完整案例: 

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>绑定属性以及缩写形式</title>
</head>
<body>
  <div id="app">
    <!-- 如果属性的值是变量，boolean类型，number类型，对象，数组，null，undefined，需要使用绑定属性 -->
    <!-- 使用绑定属性遇到 null，undefined，则该属性自动不显示  -->
    <div v-bind:msg="msg" v-bind:flag="true" v-bind:num="100" v-bind:obj="{a: 1, b: 2}" v-bind:arr="['a', 'b']" v-bind:nu="null" v-bind:un="undefined"></div>
    <div :msg="msg" :flag="true" :num="100" :obj="{a: 1, b: 2}" :arr="['a', 'b']" :nu="null" :un="undefined"></div>
      
    <!-- 如果属性的值需要拼接字符串完成，且含有变量，可以使用 绑定属性结合 字符串拼接以及模板字符串实现  -->
    <div v-bind:id="'list-' + id">111</div>
    <div v-bind:id=`list-${id}`>222</div>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>

  const { createApp } = Vue
  const app = createApp({
    data () {
      return {
        msg: 'hello vue',
        id: 100
      }
    }
  })

  app.mount('#app')
  
</script>

</html>
```



### 2.4 事件绑定

我们可以使用 `v-on` 指令 (简写为 `@`) 来监听 DOM 事件，并在事件触发时执行对应的 JavaScript。用法：`v-on:click="methodName"` 或 `@click="handler"`。

事件处理器的值可以是：

1. **内联事件处理器**：事件被触发时执行的内联 JavaScript 语句 (与 `onclick` 类似)。
2. **方法事件处理器**：一个指向组件上定义的方法的属性名或是路径。

内联事件处理器·通常用于简单场景，例如：

```
<button @click="count++">加 1</button>
<p>Count is: {{ count }}</p>
```

随着事件处理器的逻辑变得愈发复杂，内联代码方式变得不够灵活。因此 `v-on` 也可以接受一个方法名或对某个方法的调用。

`方法事件处理器`

```js
<button @click="greet">问候</button>
 data () {
   return {
      name: 'Vue.js'
   }
 },
 methods: {
   greet(event) {
     // 方法中的 `this` 指向当前活跃的组件实例
     alert(`Hello ${this.name}!`)
     // `event` 是 DOM 原生事件
     if (event) {
       alert(event.target.tagName)
     }
  }
}
```

除了直接绑定方法名，你还可以在内联事件处理器中调用方法。这允许我们向方法传入自定义参数以代替原生事件：

```
methods: {
  say(message) {
    alert(message)
  }
}
```

```
<button @click="say('hello')">说 hello</button>
<button @click="say('bye')">说 bye</button>
```

内联事件处理器中访问原生 DOM 事件。你可以向该处理器方法传入一个特殊的 `$event` 变量，或者使用内联箭头函数：

```
 <!-- 使用特殊的 $event 变量 -->
 <button @click="warn('表单不能提交.', $event)">提交</button>
```

```
methods: {
  warn(message, event) {
    // 这里可以访问 DOM 原生事件
    if (event) {
      event.preventDefault()
    }
    alert(message)
  }
}
```

在处理事件时调用 `event.preventDefault()` 或 `event.stopPropagation()` 是很常见的。尽管我们可以直接在方法内调用，但如果方法能更专注于数据逻辑而不用去处理 DOM 事件的细节会更好。

为解决这一问题，Vue 为 `v-on` 提供了**事件修饰符**。

```html
<!-- 单击事件将停止传递 -->
<a @click.stop="doThis"></a>

<!-- 提交事件将不再重新加载页面 -->
<form @submit.prevent="onSubmit"></form>

<!-- 修饰语可以使用链式书写 -->
<a @click.stop.prevent="doThat"></a>

<!-- 也可以只有修饰符 -->
<form @submit.prevent></form>

<!-- 仅当 event.target 是元素本身时才会触发事件处理器 -->
<!-- 例如：事件处理器不来自子元素 -->
<div @click.self="doThat">...</div>

<!-- 添加事件监听器时，使用 `capture` 捕获模式 -->
<!-- 例如：指向内部元素的事件，在被内部元素处理前，先被外部处理 -->
<div @click.capture="doThis">...</div>

<!-- 点击事件最多被触发一次 -->
<a @click.once="doThis"></a>
```



在监听键盘事件时，我们经常需要检查特定的按键。Vue 允许在 `v-on` 或 `@` 监听按键事件时`添加按键修饰符`。

```
 <!-- 按键修饰符 -->
 <!-- 原生 -->
 <input type="text" @keyup="print1">
 <!-- vue -->
 <input type="text" @keyup.enter="print2">
```

```js
methods: {
	print1 (event) {
        if (event.keyCode === 13) {
        	console.log('打印1')
        }
    },
    print2 () {
    	console.log('打印2')
    }
}
```

完整案例: 

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>绑定事件</title>
  <style>
    .parent {
      width: 200px;
      height: 200px;
      background-color: #f66;
      display: flex;
      justify-content: center;
      align-items: center;
    }
    .child {
      width: 100px;
      height: 100px;
      background-color: #ccc;
    }
  </style>
</head>
<body>
  <div id="app">
    <!-- 内联事件处理器 -->
    <button v-on:click="count++">加1</button> {{ count }}<br />
    <!-- 方法事件处理器 -->
    <button v-on:click="add">加1</button> {{ count }}<br />

    <button @click="say('hello', $event)">say hello</button>
    <button @click="say('bye', $event)">say bye</button>

    <!-- 事件对象 - 阻止事件冒泡，阻止默认事件 -->
    <form @submit="getUserInfo">
      <input type="text" name="userName" placeholder="用户名" />
      <input type="password" name="password" placeholder="密码" />
      <input type="submit" value="提交">
    </form>
    <div class="parent" @click="print('parent', $event)">
      <div class="child" @click="print('child', $event)"></div>
    </div>

    <!-- 事件修饰符 - 阻止事件冒泡，阻止默认事件  -->
    <form @submit.prevent="getUserInfoVue">
      <input type="text" name="userName" placeholder="用户名" />
      <input type="password" name="password" placeholder="密码" />
      <input type="submit" value="提交">
    </form>
    <div class="parent" @click="printVue('parent')">
      <div class="child" @click.stop="printVue('child')"></div>
    </div>

    <!-- 事件对象 -  回车时打印数据 -->
    <input type="text" @keyup="printData" />
    <!-- 按键修饰符 -  回车时打印数据 -->
    <input type="text" @keyup.enter="printDataVue" />
    <!-- vue2中可以 根据 keyCode 作为修饰符, vue3中不支持 -->
    <input type="text" @keyup.13="printDataVueCode" />
  </div>
</body>
 <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>

  const { createApp } = Vue
  const app = createApp({
    data () {
      return {
        count: 10,
        name: 'Vue.js',
        text: '1'
      }
    },
    methods: { // 所有自定义的vue的事件都应该写在 methods 中
      // 如果使用事件时，没有添加(),那么事件含有默认参数为 event
      add (event) {
        // this其实就是vue的实例
        // this.count++
        // this.count += 1
        this.count = this.count + 1
        console.log(this.name)
        console.log(event) // PointerEvent 与原生js中的事件对象保持一致
      },
      // 如果使用事件时添加(),并且还想用事件对象，那么传递事件对象的vue的专属参数 $event
      say (msg, event) {
        console.log(msg, event)
      },
      getUserInfo (event) {
        event.preventDefault()
      },
      getUserInfoVue(){
        console.log('getUserInfoVue...')
      },
      print (msg, event) {
        event.stopPropagation()
        console.log(msg)
      },
      printVue (msg) {
        console.log(msg)
      },
      printData (event) {
        if (event.keyCode === 13) {
          console.log('1')
        }
      },
      printDataVue () {
        console.log(2)
      },
      printDataVueCode () {
        console.log(3)
      }
    }
  })

  app.mount('#app')
  
</script>

</html>
```



### 2.5 条件渲染

`v-if` 指令用于条件性地渲染一块内容。这块内容只会在指令的表达式返回真值时才被渲染。

也可以使用 `v-else` 为 `v-if` 添加一个“else 区块”

一个 `v-else` 元素必须跟在一个 `v-if` 或者 `v-else-if` 元素后面，否则它将不会被识别。

```
<div v-if="grade >= 90">优</div>
<div v-else-if="grad" >= 80">良</div>
<div v-else-if="grade >= 70">中</div>
<div v-else-if="grade >= 60">差</div>
<div v-else>不及格</div>
```

```js
data () {
    return {
        grade: 66
    }
}
```

> 想要切换不止一个元素,在这种情况下我们可以在一个 `<template>` 元素上使用 `v-if`，这只是一个不可见的包装器元素，最后渲染的结果并不会包含这个 `<template>` 元素。---- template是一个空标签

另一个可以用来按条件显示一个元素的指令是 `v-show`。其用法基本一样：

不同之处在于 `v-show` 会在 DOM 渲染中保留该元素；`v-show` 仅切换了该元素上名为 `display` 的 CSS 属性。

> `v-show` 不支持在 `<template>` 元素上使用，也不能和 `v-else` 搭配使用。

```
<div v-show="grade >= 90 && grade < 100">优</div>
<div v-show="grade >= 80 && grade < 90">良</div>
<div v-show="grade >= 70 && grade < 80">中</div>
<div v-show="grade >= 60 && grade < 70">差</div>
<div v-show="grade < 60">不及格</div>
```



完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>条件渲染</title>
</head>
<body>
  <div id="app">
    <button @click="grade++"> 加</button> {{ grade }}<button @click="grade--">减</button>
    <!-- v-if v-else-if v-else -->
    <div v-if="grade >=90">优</div>
    <div v-else-if="grade >=80">良</div>
    <div v-else-if="grade >=70">中</div>
    <div v-else-if="grade >=60">差</div>
    <div v-else>不及格</div>

    <hr />
    <!-- v-show -->
    <div v-show="grade >= 90">优</div>
    <div v-show="grade >= 80 && grade < 90">良</div>
    <div v-show="grade >= 70 && grade < 80">中</div>
    <div v-show="grade >= 60 && grade < 70">差</div>
    <div v-show="grade < 60">不及格</div>

    <!-- 假如不同条件下需要同时控制多个元素的显示和不显示 -->
    <div v-if="flag">1</div>
    <div v-if="flag">2</div>
    <div v-if="flag">3</div>
    <!-- template 属于vue框架中的空标签，审查元素时不会被渲染出来 -->
    <template v-if="flag">
      <div>4</div>
      <div>5</div>
      <div>6</div>
    </template>

  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>

  const { createApp } = Vue
  const app = createApp({
    data () {
      return {
        grade: 61,
        flag: true
      }
    }
  })

  app.mount('#app')
  
</script>

</html>
```

> `v-if` vs `v-show`
>
> `v-if` 是“真实的”按条件渲染，因为它确保了在切换时，条件区块内的事件监听器和子组件都会被销毁与重建。
>
> `v-if` 也是**惰性**的：如果在初次渲染时条件值为 false，则不会做任何事。条件区块只有当条件首次变为 true 时才被渲染。
>
> 相比之下，`v-show` 简单许多，元素无论初始条件如何，始终会被渲染，只有 CSS `display` 属性会被切换。
>
> 总的来说，`v-if` 有更高的切换开销，而 `v-show` 有更高的初始渲染开销。因此，如果需要频繁切换，则使用 `v-show` 较好；如果在运行时绑定条件很少改变，则 `v-if` 会更合适。



### 2.6 列表渲染

我们可以使用 `v-for` 指令基于一个数组(对象、字符串)来渲染一个列表。`v-for` 指令的值需要使用 `item in items` 形式的特殊语法，其中 `items` 是源数据的数组，而 `item` 是迭代项的**别名**

```
data() {
  return {
    items: [{ message: 'Foo' }, { message: 'Bar' }]
  }
}

<li v-for="item in items">
  {{ item.message }}
</li>
```

在 `v-for` 块中可以完整地访问父作用域内的属性和变量。`v-for` 也支持使用可选的第二个参数表示当前项的位置索引。

```
data() {
  return {
    parentMessage: 'Parent',
    items: [{ message: 'Foo' }, { message: 'Bar' }]
  }
}

<li v-for="(item, index) in items">
  {{ parentMessage }} - {{ index }} - {{ item.message }}
</li>
```



#### v-if & v-for同时用在一个元素上

> v-if 与 v-for 同时存在于一个元素上，会发生什么？
>
> `vue3_if_for.html`
>
> ```html
> <!DOCTYPE html>
> <html lang="en">
> <head>
> <meta charset="UTF-8">
> <meta http-equiv="X-UA-Compatible" content="IE=edge">
> <meta name="viewport" content="width=device-width, initial-scale=1.0">
> <title>vue3的v-if与v-for优先级</title>
> </head>
> <body>
> <div id="app">
>  <ul>
>    <li v-for="(item, index) of arr" :key="index" v-if="flag">
>      {{ item }}
>    </li>
>  </ul>
> </div>
> </body>
> <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
> <script>
> Vue.createApp({
>  data () {
>    return {
>      arr: ['a', 'b', 'c', 'd'],
>      flag: false
>    }
>  }
> }).mount('#app')
> </script>
> </html>
> ```
>
> `vue2_if_for.html`
>
> ```html
> <!DOCTYPE html>
> <html lang="en">
> <head>
> <meta charset="UTF-8">
> <meta http-equiv="X-UA-Compatible" content="IE=edge">
> <meta name="viewport" content="width=device-width, initial-scale=1.0">
> <title>vue2的v-if与v-for优先级</title>
> </head>
> <body>
> <div id="app">
>  <ul>
>    <li v-for="(item, index) of arr" :key="index" v-if="flag">
>      {{ item }}
>    </li>
>  </ul>
> </div>
> </body>
> <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
> <script>
> new Vue({
>  data: {
>    arr: ['a', 'b', 'c', 'd'],
>    flag: false
>  }
> }).$mount('#app')
> 
> </script>
> </html>
> ```
>
> > 通过`审查元素`得知：
> >
> > vue3中，v-if的优先级高于v-for
> >
> > vue2中，v-for的优先级高于v-if



#### 数组更新检测

**a. 使用以下方法操作数组，可以检测变动** 

​	push() pop() shift() unshift() splice() sort() reverse()

**b. filter(), concat() 和 slice() ,map(),新数组替换旧数组**

**c. 不能检测以下变动的数组**

​	由于 JavaScript 的限制，Vue 不能检测以下数组的变动：

​      **1.当你利用索引直接设置一个数组项时，例如：vm.items[indexOfItem] = newValue**

​        1-1.Vue.set(vm.items, indexOfItem, newValue)

​               Vue.set(vm.arr, 2, 30) //如果在实例中可以通过 this.$set(vm.arr, 2, 30)

​        1-2 vm.items.splice(indexOfItem, 1, newValue)



​      **2.当你修改数组的长度时，例如：vm.items.length = newLength**

​        vm.items.splice(newLength)

> 注：结合$forceUpdate学习



### 2.7 表单输入绑定

在前端处理表单时，我们常常需要将表单输入框的内容同步给 JavaScript 中相应的变量

```
<input
  :value="text"
  @input="event => text = event.target.value">
```

`v-model` 指令帮我们简化了这一步骤：

```
<input v-model="text">
```

`v-model` 还可以用于各种不同类型的输入，`<textarea>`、`<select>` 元素。它会根据所使用的元素自动使用对应的 DOM 属性和事件组合：

> - 文本类型的 `<input>` 和 `<textarea>` 元素会绑定 `value` property 并侦听 `input` 事件；
> - `<input type="checkbox">` 和 `<input type="radio">` 会绑定 `checked` property 并侦听 `change` 事件；
> - `<select>` 会绑定 `value` property 并侦听 `change` 事件 

> `v-model` 会忽略任何表单元素上初始的 `value`、`checked` 或 `selected` attribute。它将始终将当前绑定的 JavaScript 状态视为数据的正确来源。你应该在 JavaScript 中使用`data` 选项来声明该初始值。

完整案例： 

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>表单输入绑定</title>
</head>
<body>
  <div id="app">
    <div>
      用户名: <input type="text" v-model="userName" /> {{ userName }}
    </div>
    <div>
      密  码: <input type="password" v-model="password" /> {{ password }}
    </div>
    <div>
      性  别: <input type="radio" name="sex" v-model="sex" value="男"/>男<input type="radio" name="sex" v-model="sex" value="女"/>女 --- {{ sex }}
    </div>
    <div>
      阶  段: <select v-model="lesson">
        <option disabled value="">请选择</option>
        <option :value="1">一阶段</option>
        <option :value="2">二阶段</option>
        <option :value="3">三阶段</option>
      </select> ---- {{ lesson === 1 ? '一阶段' : lesson === 2 ? '二阶段' : '三阶段' }}
    </div>
    <div>
      爱  好:
      <input type="checkbox" name="hobby" value="🏀" v-model="hobby"/>🏀
      <input type="checkbox" name="hobby" value="⚽" v-model="hobby"/>⚽
      <input type="checkbox" name="hobby" value="🏓" v-model="hobby"/>🏓
      <input type="checkbox" name="hobby" value="⚾" v-model="hobby"/>⚾
      <input type="checkbox" name="hobby" value="🌏" v-model="hobby"/>🌏
    </div> ---- {{ hobby }}
    <div>
      备  注: <textarea v-model="note"></textarea> {{ note }}
    </div>
    <div>
      <input type="checkbox" v-model="flag"/> 同意*******协议 --- {{ flag }}
    </div>
    <div>
      <input type="button" value="提交" @click="submit" /> 
    </div>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  Vue.createApp({
    data () {
      return {
        userName: '',
        password: '',
        sex: '男',
        lesson: '',
        note: '',
        hobby: ['🌏'], // 表示多选-数组
        flag: false // 表示开关 - boolean
      }
    },
    methods: {
      submit () {
        if (this.flag) {
          console.log({
            userName: this.userName,
            password: this.password,
            sex: this.sex,
            hobby: this.hobby,
            lesson: this.lesson,
            note: this.note
          })
        } else {
          alert('请先勾选用户协议')
        }
      }
    }
  }).mount('#app')
</script>
</html>
```

> 修饰符
>
> .lazy        --- input失去焦点时同步一次
>
> .number --- 输出的为数字
>
> .trim        --- 去除两端的空格



### 2.8 类与样式绑定

数据绑定的一个常见需求场景是操纵元素的 CSS class 列表和内联样式。因为 `class` 和 `style` 都是 attribute，我们可以和其他 attribute 一样使用 `v-bind` 将它们和动态的字符串绑定。但是，在处理比较复杂的绑定时，通过拼接生成字符串是麻烦且易出错的。因此，Vue 专门为 `class` 和 `style` 的 `v-bind` 用法提供了特殊的功能增强。除了字符串外，表达式的值也可以是对象或数组。

> 不管是类class还是样式style，都有对象和数组的写法

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>类与样式绑定</title>
  <style>
    .a {
      font-size: 30px;
    }
    .b {
      color: #f66;
    }
  </style>
</head>
<body>
  <div id="app">
    <input type="checkbox" v-model="flag" />
    <div class="a b">群组选择器</div>
    <!-- 在flag字段为真时，才显示红色的30px的字体 -->
    <!-- class对象写法,key为定义的样式，value为条件 -->
    <div :class="{ a: flag, b: flag }">class的对象写法</div>
    <!-- class数组写法 -->
    <div :class="[{a: flag}, {b: flag}]">class数组写法</div>
    <!-- 三元运算符 -->
    <div :class="flag ? 'a b' : ''">三元运算符 class写法</div>

    <!-- style对象写法,小驼峰式以及短横线连接方式  -->
    <div :style="{ color: color, fontSize: fontSize }">style对象写法</div>
    <!-- style数组写法 -->
    <div :style="[{color: color}, {fontSize: fontSize}]">style数组写法</div>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  Vue.createApp({
    data () {
      return {
        flag: false,
        color: '#00f',
        fontSize: '50px'
      }
    }
  }).mount('#app')
</script>
</html>
```



## 三.响应式

### 3.1 计算属性

模板中的表达式虽然方便，但也只能用来做简单的操作。如果在模板中写太多逻辑，会让模板变得臃肿，难以维护

推荐使用**计算属性**来描述依赖响应式状态的复杂逻辑

计算属性是基于它们的响应式**依赖**进行**缓存**的，计算属性比较适合对多个变量或者对象进行处理后返回一个结果值，也就是说多个变量中的某一个值发生了变化则我们监控的这个值也就会发生变化。

计算属性定义在Vue对象中，通过关键词 **computed** 属性对象中定义一个个函数，并返回一个值，使用计算属性时和 data 中的数据使用方式一致。

#### 3.1.1 一般计算属性以及方法对比

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>计算属性以及方法对比</title>
  <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
</head>
<body>
  <div id="app">
    <!-- js表达式 -->
    {{ msg.split('').reverse().join('') }} - {{ msg.split('').reverse().join('') }} - {{ msg.split('').reverse().join('') }}
    <!-- 方法 -->
    {{ reverseMsgFn() }} -  {{ reverseMsgFn() }} - {{ reverseMsgFn() }} 
    <!-- 计算属性 -->
    {{ reverseMsg }} - {{ reverseMsg }} -  {{ reverseMsg }}
  </div>
</body>
<script>
  const { createApp } = window.Vue
  const app = createApp({
    data () {
      return {
        msg: 'hello vue'
      }
    },
    methods: {
      reverseMsgFn () {
        console.log(1)
        return this.msg.split('').reverse().join('')
      }
    },
    computed: {
      reverseMsg () {
        console.log(2)
        return this.msg.split('').reverse().join('')
      }
    }
    
  })

  // 挂载应用
  app.mount('#app')

</script>
</html>
```

> 计算属性具有依赖性，只有当依赖的值发生改变，才会重新计算
>
> 同等条件下，计算属性优于 方法 以及 js表达式。



#### 3.1.2 可写计算属性

计算属性默认仅能通过计算函数得出结果。当你尝试修改一个计算属性时，你会收到一个运行时警告。只在某些特殊场景中你可能才需要用到“可写”的属性，你可以通过同时提供 getter 和 setter 来创建：

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>计算属性 setter</title>
  <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
</head>
<body>
  <div id="app">
    <input v-model="firstName" />   +  <input v-model="lastName" /> = {{ fullName }}
    <button @click="reset">重置</button>
  </div>
</body>
<script>
  const { createApp } = window.Vue
  const app = createApp({
    data () {
      return {
        firstName: 'John',
        lastName: 'Doe'
      }
    },
    computed: {
      // fullName () {
      //   return this.firstName + ' ' + this.lastName
      // }
      fullName: {
        get () {
          return this.firstName + ' ' + this.lastName
        },
        set (newValue) {
          // 注意：我们这里使用的是解构赋值语法
          // [this.firstName, this.lastName] = newValue.split(' ')
          this.firstName = newValue.split(' ')[0]
          this.lastName = newValue.split(' ')[1]
        }
      }
    },
    methods: {
      reset () {
        this.fullName = 'zhang san'
      }
    },

  })
  // 挂载应用
  app.mount('#app')

</script>
</html>
```



### 3.2 侦听器

使用watch来侦听data中数据的变化，watch中的属性一定是data 中已经存在的数据。

使用场景：**数据变化时执行异步或开销比较大的操作**。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>侦听属性</title>
  <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
</head>
<body>
  <div id="app">
    <input type="text" v-model="firstName" /> + <input type="text" v-model="lastName" /> = {{ fullName }}
  </div>
</body>
<script>
  const { createApp } = window.Vue
  const app = createApp({
    data () {
      return {
        firstName: '',
        lastName: '',
        fullName: ''
      }
    },
    watch: {
      firstName (newVal, oldVal) {
        this.fullName = newVal + this.lastName
      },
      lastName (newVal, oldVal) {
        this.fullName = this.firstName + newVal
      }
    }

  })

  // 挂载应用
  app.mount('#app')

</script>
</html>
```

使用计算属性可以简化

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>计算属性PK侦听属性</title>
    <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
</head>
<body>
  <div id="app">
    <input type="text" v-model="firstName" /> + <input type="text" v-model="lastName" /> = {{ fullName }}
  </div>
</body>
<script>
  const { createApp } = window.Vue
  const app = createApp({
    data () {
      return {
        firstName: '',
        lastName: ''
      }
    },
    computed: {
      fullName () {
        return this.firstName + this.lastName
      }
    }
  })

  // 挂载应用
  app.mount('#app')

</script>
</html>
```

> 如何监听一个对象下的属性的变化？
>
> `watch` 默认是浅层的：被侦听的属性，仅在被赋新值时，才会触发回调函数——而嵌套属性的变化不会触发。如果想侦听所有嵌套的变更，**你需要深层侦听器，需要在options Api中添加 deep: true**
>
> 如果**一开始就需要监听数据，需要在options Api中添加 immediate: true**
>
> 如果在**达到某一个条件下再开启监听，需要使用 this.$watch(监听的数据，callback)手动去添加侦听器**
>
> 如果不使用深度侦听，如何监听对象下的属性的变化？可以通过 监听 `对象.属性`的变化

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <meta http-equiv="X-UA-Compatible" content="IE=edge">
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
 <title>深度侦听</title>
 <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
</head>
<body>
 <div id="app">
    <input type="text" v-model="user.firstName" /> + <input type="text" v-model="user.lastName" /> = <span id="span">{{ user.fullName }}</span> | {{ full }}
    <hr />
    <button @click="count++">加1</button>{{ count }}
    <button @click="startWatch">开始监听</button>
    <button @click="stopWatch">停止监听</button>
 </div>
</body>
<script>
 const { createApp } = Vue
 const app = createApp({
    data () {
      return {
        user: {
          firstName: '1',
          lastName: '2',
          fullName: ''
        },
        count: 100,
        unwatch: null
      }
    },
    computed: { 
      full () {
        return this.user.firstName + this.user.lastName
      }
    },
    watch: {
      // 监听失败
      // user (newVal, oldVal) {
      //   this.user.fullName = newVal.firstName + newVal.lastName
      // }
      // 深度侦听
      user: {
        deep: true,
        handler (newVal, oldVal) {
          this.user.fullName = newVal.firstName + newVal.lastName
        },
        // 自动执行一次监听数据
        immediate: true,
      }
      // 'user.firstName': function (newVal, oldVal)  {
      //   this.user.fullName = newVal + this.user.lastName
      // },
      // 'user.lastName': function(newVal, oldVal)  {
      //   this.user.fullName = this.user.firstName + newVal
      // }
    },
    methods: {
      startWatch () {
        // 开始监听  赋值给一个函数，用于停止监听
        this.unwatch = this.$watch('count', (newVal, oldVal) => {
          console.log(newVal, oldVal)
        })
      },
      stopWatch () {
        this.unwatch() // 停止监听
      }
    }
 })

 // 挂载应用
 app.mount('#app')

</script>
</html>
```



## 四. 组件使用

### 4.1 组件化

模块化就是将系统功能分离成独立的功能部分的方法，一般指的是单个的某一种东西，例如js、css

而组件化针对的是页面中的整个完整的功能模块划分，组件是一个html、css、js、image等外链资源，这些部分组成的一个聚合体

> 优点：代码复用，便于维护

划分组件的原则：复用率高的，独立性强的

组件应该拥有的特性：可组合，可重用，可测试，可维护





### 4.2 封装组件

一个 Vue 组件在使用前需要先被“注册”，这样 Vue 才能在渲染模板时找到其对应的实现。

- 先构建组件的模板
- 定义组件
- 注册组件
- 使用组件

#### 4.2.1 vue2组件注册与使用

在vue2中，我们通过**Vue.extend来创建Vue的子类**，这个东西其实就是组件

也就是说Vue实例和组件的实例有差别但是差别不大，因为毕竟一个是父类一个是子类

一般的应用，会拥有一个根实例，在根实例里面都是一个一个的组件

因为组件是要嵌入到实例或者父组件里的，也就是说，组件可以互相嵌套，而且，所有的组件最外层必须有一个根实例，**所以组件分为：全局组件和局部组件**

***全局组件在任意的实例、父级组件中都能使用，局部组件只能在创建自己的父级组件或者实例中使用***

创建组件：

```
Vue.extend(options)
```

**全局注册：**

```
var App = Vue.extend({
	template:"<h1>hello world</h1>"
})
Vue.component('my-app',App)
```

简便写法：

```
// 创建组件构造器和注册组件合并一起  
Vue.component('hello',{//Vue会自动的将此对象给Vue.extend
	template:"<h1>hello</h1>"
})
```



> 组件通过template来确定自己的模板,template里的模板必须有根节点，标签必须闭合

> **组件的属性挂载通过：data方法来返回一个对象作为组件的属性，这样做的目的是为了每一个组件实例都拥有独立的data属性**



**局部注册：**

```
new Vue({
    el:"#app",
    components:{ //在实例配置项配置
    	'my-app':App
    }
})
```

简便写法：

```
 data:{},
    components:{
        'hello':{
            template:"<h1>asdasdasdasdasdas</h1>"
        }
    }
```

在实例或者组件中注册另一个组件，这个时候，被注册的组件只能在注册它的实例或组件的模板中使用，一个组件可以被多个组件或实例注册

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>vue2-全局注册组件</title>
</head>
<body>
  <div id="app">
    <my-header></my-header>
  </div>
</body>
<template id="header">
  <header>头部-{{msg}}</header>
</template>
 <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>
  const Header = {
    template: '#header', 
    data () { 
      return {
        msg: 'hello header'
      }
    },
  }
  Vue.component('my-header',Header)
  new Vue({
  }).$mount('#app')
</script>
</html>
```

局部注册组件：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>vue2-局部注册组件</title>
</head>
<body>
  <div id="app">
    <my-header></my-header>
  </div>
</body>
<template id="header">
  <header>头部-{{msg}}</header>
</template>
 <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>
  const Header = {
    template: '#header', 
    data () { 
      return {
        msg: 'hello header'
      }
    },
  }

  new Vue({
    components:{
      'my-header':Header
    }
  }).$mount('#app')
</script>
</html>
```



#### 4.2.2 vue3组件注册与使用

我们可以使用 [Vue 应用实例](https://cn.vuejs.org/guide/essentials/application.html)的 `app.component()` 方法，让组件在当前 Vue 应用中全局可用

```js
import { createApp } from 'vue'

const app = createApp({})

app.component(
  // 注册的名字
  'MyComponent',
  // 组件的实现
  {
    /* ... */
  }
)
```

`app.component()` 方法可以被链式调用：

```
app
  .component('ComponentA', ComponentA)
  .component('ComponentB', ComponentB)
  .component('ComponentC', ComponentC)
```

全局注册的组件可以在此应用的任意组件的模板中使用

```
<!-- 这在当前应用的任意组件中都可用 -->
<ComponentA/>
<ComponentB/>
<ComponentC/>
```

所有的子组件也可以使用全局注册的组件，这意味着这三个组件也都可以在*彼此内部*使用

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>vue3-全局注册组件</title>
</head>
<body>
  <div id="app">
    <!--04. 使用组件 大驼峰式 短横线式  在html文件中只能使用 短横线式  -->
    <my-header></my-header>
    <!-- <myHeader></myHeader> -->
  </div>
</body>
<!-- 01 定义组件的模板 -->
<template id="header">
  <header>头部-{{msg}}</header>
</template>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  // 02.定义组件 - 首字母大写
  const Header = {
    template: '#header', // 绑定页面的模板 --- 必不可少
    // 可以写任意的属于vue的选项
    data () {
      return {
        msg: 'hello header'
      }
    }
  }
  
  const { createApp } = Vue
  const app = createApp({
  })
  // 03.全局注册组件 --- app.mount('#app') 之前
  app.component('myHeader', Header) // 大驼峰式
  // app.component('my-header', Header) // 短横线式

  app.mount('#app')
</script>
</html>
```



局部注册组件：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>vue3-局部注册组件</title>
</head>
<body>
  <div id="app">
    <my-header></my-header>
  </div>
</body>
<template id="header">
  <header>头部-{{msg}}</header>
</template>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const Header = {
    template: '#header', 
    data () {
      return {
        msg: 'hello header'
      }
    }
  }
  const { createApp } = Vue
  const app = createApp({
    components:{
      'my-header':Header
    }
  })

  app.mount('#app')
</script>
</html>
```



### 4.3 vue2的过滤器

自定义的方法有两种：全局定义和局部定义，
全局定义的过滤器在任意的实例、组件中都可以使用，
局部定义就是在实例、组件中定义，只能在这个实例或组件中使用

1. **全局定义**

   Vue.filter(name,handler)

   name是过滤器的名字，handler是数据格式化处理函数，接收的第一个参数就是要处理的数据，返回什么数据，格式化的结果就是什么

   在模板中通过 | (管道符) 来使用,在过滤器名字后面加（）来传参，参数会在handler函数中第二个及后面的形参来接收

```
<p>{{price | priceFilter('$')}}</p>

Vue.filter('priceFilter',function(val, type) {
	return type + val
})
```

2. **局部定义**

   在实例、组件的配置项中设置 filters，键名为过滤器名，值为handler

```
    filters:{
        priceFilter:function (val, type) {
            return type + val
        }
    }
```

完整实例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>vue2_过滤器</title>
</head>
<body>
  <div id="app">
    {{ sex }} - {{ sex | sexFilter }} - {{ price }} - {{ price | priceFilter('$') }} - {{ price | priceFilter('￥') }}
  </div>
</body>
 <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>
  // 全局过滤器
  Vue.filter('sexFilter', (val) => {
    return val === 1 ? '男' : '女'
  })
  new Vue({
    data: {
      sex: 1, // 1 男  0 女
      price: 100
    },
    filters: {
      priceFilter (val, type) {
        return type + val
      }
    }
  }).$mount('#app')
</script>
</html>
```



vue3中移除了过滤器，可以借助computed实现过滤器的功能。

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>vue3_代替过滤器</title>
</head>
<body>
<div id="app">
 {{ sex }} - {{ newSex }} - {{ price }} - {{zhPrice }} - {{ enPrice }}
</div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
Vue.createApp({
 data(){
   return  {
     sex: 1, // 1 男  0 女
     price: 100
   }
 },
 computed: {
   newSex () {
     return this.sex === 1 ? '男' : '女'
   },
   zhPrice () {
    return '￥' + this.price
   },
   enPrice () {
    return '$' + this.price
   }
 }
}).mount('#app')
</script>
</html>
```





### 4.4 虚拟dom

频繁且复杂的dom操作通常是前端性能瓶颈的产生点，Vue提供了虚拟dom的解决办法

虚拟的DOM的核心思想是：对复杂的文档DOM结构，提供一种方便的工具，进行最小化地DOM操作。这句话，也许过于抽象，却基本概况了虚拟DOM的设计思想

(1) 提供一种方便的工具，使得开发效率得到保证
(2) 保证最小化的DOM操作，使得执行效率得到保证

也就是说，虚拟dom的框架/工具都是这么做的：

1. 根据虚拟dom树最初渲染成真实dom
2. 当数据变化，或者说是页面需要重新渲染的时候，会重新生成一个新的完整的虚拟dom
3. 拿新的虚拟dom来和旧的虚拟dom做对比（使用diff算法）。得到需要更新的地方之后，更新内容

这样的话，就能大量减少真实dom的操作,提高性能

<img src="https://s1.ax1x.com/2020/05/25/tpHcBn.png" alt="diff" style="zoom: 80%;" />



> 什么是虚拟dom？与key值的关系？
>  Virual DOM是用JS对象记录一个dom节点的副本，当dom发生更改时候，先用虚拟dom进行diff，算出最小差异，然后再修改真实dom。

```
当用传统的方式操作DOM的时候，浏览器会从构建DOM树开始从头到尾执行一遍流程，效率很低。而虚拟DOM是用javascript对象表示的，而操作javascript是很简便高效的。虚拟DOM和真正的DOM有一层映射关系，很多需要操作DOM的地方都会去操作虚拟DOM，最后统一一次更新DOM。因而可以提高性能
```



#### 虚拟DOM的Diff算法

> 虚拟DOM中，在DOM的状态发生变化时，虚拟DOM会进行Diff运算，来更新只需要被替换的DOM，而不是全部重绘。
> 在Diff算法中，只平层的比较前后两棵虚拟DOM树的节点，没有进行深度的遍历。

1.如果节点类型改变，直接将旧节点卸载，替换为新节点，旧节点包括下面的子节点都将被卸载，如果新节点和旧节点仅仅是类型不同，但下面的所有子节点都一样时，这样做也是效率不高的一个地方。
2.节点类型不变，属性或者属性值改变，不会卸载节点，执行节点更新的操作。
3.文本改变，直接修改文字内容。
4.移动，增加，删除子节点时：



如果想在中间插入节点F，简单粗暴的做法是：卸载C，装载F，卸载D，装载C，卸载E，装载D，装载E。如下图：



![key1](https://s1.ax1x.com/2020/05/25/tpHX4K.png)

写代码时，如果没有给数组或枚举类型定义一个key，就会采用上面的粗暴算法。
如果为元素增加key后，Vue就能根据key，直接找到具体的位置进行操作，效率比较高。如下图：

> 本寻着key值相同的即可复用的原则。![key2](https://s1.ax1x.com/2020/05/25/tpHLAx.png)

***在v-for中提供key，一方面可以提高性能，一方面也会避免出错***



[虚拟dom概括理解](https://blog.csdn.net/mrliber/article/details/79036828)

[虚拟dom与key的关系](https://blog.csdn.net/weixin_42695446/article/details/84680213)

https://blog.csdn.net/luo1914_/article/details/105054883





### 4.5 组件之间的通信



#### 4.5.1 props传递数据

i. 父子组件传值 (**props down, events up**) 

![props emit](https://s1.ax1x.com/2020/05/25/tpbFEt.png)



ii. 属性验证 props:{name:Number} Number,String,Boolean,Array,Object,Function,null(不限制类型) 



**组件实例的作用域是孤立的,父组件不能直接使用子组件的数据，子组件也不能直接使用父组件的数据**

**父组件在模板中使用子组件的时候可以给子组件传递数据**

```
 <bbb money="2"></bbb>
```

**子组件需要通过props属性来接收后才能使用**

```
'bbb':{
    props:['money']
}
```

如果父组件传递属性给子组件的时候键名有'-'，子组件接收的时候写成小驼峰的模式

```
  <bbb clothes-logo='amani' clothes-price="16.58"></bbb>
  props:['clothesLogo','clothesPrice']   子组件模板中：{{clothesLogo}}
```

我们可以用 v-bind 来动态地将 prop 绑定到父组件的数据。每当父组件的数据变化时，该变化也会传导给子组件





##### 单向数据流

Prop 是单向绑定的：当父组件的属性变化时，将传递给子组件，但是反过来不会。这是为了防止子组件无意间修改了父组件的状态，来避免应用的数据流变得难以理解。

另外，每次父组件更新时，子组件的所有 prop 都会更新为最新值。这意味着你不应该在子组件内部改变 prop。如果你这么做了，Vue 会在控制台给出警告。



> 注意在 JavaScript 中对象和数组是引用类型，指向同一个内存空间，如果 prop 是一个对象或数组，在子组件内部改变它会影响父组件的状态。  





##### prop验证

我们可以为组件的 prop 指定验证规则。如果传入的数据不符合要求，Vue 会发出警告。这对于开发给他人使用的组件非常有用

**验证主要分为：类型验证、必传验证、默认值设置、自定义验证**

```html
props:{
    //类型验证:
    str:String,
    strs:[String,Number],
    //必传验证
    num:{
        type:Number,
        required:true
    },
    //默认数据
    bool:{
        type:Boolean,
        // default:true,
        default:function(){
            return true
        }
    },
    //自定义验证函数
    //props:["nums"]
    props:{
        nums:{
            type:Number, //[Number,String,Boolean,Array]
            validator: function (value) {
                return value %2 == 0
            }
        }
    }
}
```

**当父组件传递数据给子组件的时候，子组件不接收，这个数据就会挂载在子组件的模板的根节点上**



##### 透传属性之$attrs

一个包含了组件所有透传 attributes 的对象。

[透传 Attributes](https://cn.vuejs.org/guide/components/attrs.html) 是指由父组件传入，且没有被子组件声明为 props 或是组件自定义事件的 attributes 和事件处理函数。

`<my-button class="btn"></my-button>`

子组件模板只有button，那么my-button的class直接透传给子组件

`<button class="btn"></button>`

默认情况下，若是单一根节点组件，`$attrs` 中的所有属性都是直接自动继承自组件的根元素。而多根节点组件则不会如此，同时你也可以通过配置 [`inheritAttrs`](https://cn.vuejs.org/api/options-misc.html#inheritattrs) 选项来显式地关闭该行为。

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>透传attribute</title>
  <style>
    .btn {
      border: 0;
      padding: 10px 20px;
    }
    .btn-success {
      background-color: rgb(29, 198, 29);
      color: #fff;
    }
    .btn-danger {
      background-color: rgb(218, 23, 39);
      color: #fff;
    }
    .btn-primary {
      background-color: rgb(75, 104, 236);
      color: #fff;
    }
  </style>
</head>
<body>
  <div id="app">
    <my-button type="a" class="btn-success" @click="print('success')" ></my-button>
    <my-button type="b" class="btn-danger"  @click="print('danger')" ></my-button>
    <my-button type="c" class="btn-primary" @click="print('primary')"></my-button>
  </div>
</body>

<template id="button">
  <!-- Attributes 继承(class， v-on事件继承) -->
  <div class="button">
    <div >测试</div>
    <!--借助v-bind指令可以让透传的属性放在button中-->
    <button class="btn" v-bind="$attrs">按钮</button>
  </div>
</template>

<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp } = Vue
  const app = createApp({
    components: {
      MyButton: {
        template: '#button',
        mounted () {
          console.log('1', this.$attrs)
        },
        inheritAttrs:false // 默认透传了属性给最外层阶段，设置false则不让透传
      }
    },
    methods: {
      print (msg) {
        console.log(msg)
      }
    }
  })
  app.mount('#app')
</script>
</html>
```



#### 4.5.2 监听事件

##### 子组件给父组件传值- $emit

在组件的模板表达式中，可以直接使用 `$emit` 方法触发自定义事件

`$emit()` 方法在组件实例上也同样以 `this.$emit()` 的形式可用

父组件可以通过 `v-on` (缩写为 `@`) 来监听事件

完整案例:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>子组件给父组件传值</title>
</head>
<body>
  <div id="app">
    <my-parent></my-parent>
  </div>
</body>
<template id="parent">
  <div>
    我是父组件
    <!-- 在父组件调用子组件的地方，绑定一个自定义的事件，该事件由父组件实现，默认参数即为子组件传递给父组件的值 -->
    <my-child @my-event="getData"></my-child>
  </div>
</template>
<template id="child">
  <div>
    我是子组件
    <button @click="$emit('my-event', 2000)">传2000</button>
    <button @click="sendData(3000)">传3000</button>
  </div>
</template>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  // 在子组件的某一个事件内部，通过 this.$emit('自定义的事件名',传递的参数)完成子组件给父组件传值,内联事件处理器中不需要写this
  const { createApp } = Vue
  const app = createApp({
    components: {
      MyParent: {
        template: '#parent',
        components: {
          MyChild: {
            template: '#child',
            methods: {
              sendData (num) {
                this.$emit('my-event', num)
              }
            }
          }
        },
        methods: {
          getData (val) {
            console.log('接收到子组件的数据:' + val)
          }
        }
      }
    }
  })

  app.mount('#app')

</script>
</html>
```



##### 子组件给父组件传值-声明触发的事件

组件要触发的事件可以显式地通过 [`emits`](https://cn.vuejs.org/api/options-state.html#emits) 选项来声明：

```js
{
	emits: ['inFocus', 'submit']
}
```

这个 `emits` 选项还支持对象语法，它允许我们对触发事件的参数进行验证：

```
{
	 emits: {
        submit(payload) {
          // 通过返回值为 `true` 还是为 `false` 来判断
          // 验证是否通过
        }
      }
}
```

要为事件添加校验，那么事件可以被赋值为一个函数，接受的参数就是抛出事件时传入 `this.$emit` 的内容，返回一个布尔值来表明事件是否合法。

```js
{
  emits: {
    // 没有校验
    click: null,

    // 校验 submit 事件
    submit: ({ email, password }) => {
      if (email && password) {
        return true
      } else {
        console.warn('Invalid submit event payload!')
        return false
      }
    }
  },
  methods: {
    submitForm(email, password) {
      this.$emit('submit', { email, password })
    }
  }
}
```

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>子组件给父组件传值</title>
</head>
<body>
  <div id="app">
    <my-parent></my-parent>
  </div>
</body>
<template id="parent">
  <div>
    我是父组件
    <!-- 在父组件调用子组件的地方，绑定一个自定义的事件，该事件由父组件实现，默认参数即为子组件传递给父组件的值 -->
    <my-child @my-event="getData"></my-child>
  </div>
</template>
<template id="child">
  <div>
    我是子组件
    <button @click="$emit('my-event', 2000)">传2000</button>
    <button @click="sendData(3000)">传3000</button>
  </div>
</template>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  // 在子组件的某一个事件内部，通过 this.$emit('自定义的事件名',传递的参数)完成子组件给父组件传值,内联事件处理器中不需要写this
  const { createApp } = Vue
  const app = createApp({
    components: {
      MyParent: {
        template: '#parent',
        components: {
          MyChild: {
            template: '#child',
            emits:{
              'my-event':(payload)=>{
                if(payload>2000){
                  return true
                }else{
                  return false
                }
              }
            },
            methods: {
              sendData (num) {
                this.$emit('my-event', num)
              }
            }
          }
        },
        methods: {
          getData (val) {
            console.log('接收到子组件的数据:' + val)
          }
        }
      }
    }
  })

  app.mount('#app')

</script>
</html>
```



##### [自定义表单组件使用v-model](https://cn.vuejs.org/guide/components/events.html#usage-with-v-model)

自定义事件可以用于开发支持 `v-model` 的自定义表单组件

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>表单组件配合 v-model</title>
</head>
<body>
  <div id="app">
    <!--
	默认情况下，v-model在组件上是使用 modelValue 作为 prop，并以update:modelValue 作为对应的事件
    回顾：如果v-model指令应用在普通的dom元素例如input上面，本质是绑定了value属性与监听input事件
-->
    <my-input v-model="username" placeholder="用户名"></my-input> {{ username }}
    <my-input v-model="password" placeholder="密码"></my-input>{{ password }}
    <button @click="submit">sub</button>
  </div>
</body>
<template id="input">
  <!--
    <my-input> 组件内部需要做两件事：
    	将内部原生input元素的value绑定modelValue 
    	输入新的值时在 input元素上触发 update:modelValue 事件
  -->
  <input type="text" :placeholder="placeholder" :value="modelValue" @input="$emit('update:modelValue', $event.target.value)" />
</template>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const Input = {
    template: '#input',
    props: {
      placeholder: String,
      modelValue: String  // 默认情况下，v-model 在组件上都是使用 modelValue 作为 prop，并以 update:modelValue 作为对应的事件
    },
    emits: ['update:modelValue']
  }


  const { createApp } = Vue

  const app = createApp({
    components: {
      MyInput: Input
    },
    data () {
      return {
        username: '',
        password: ''
      }
    },
    methods: {
      submit () {
        console.log({
          username: this.username,
          password: this.password
        })
      }
    }
  })

  app.mount('#app')
</script>
</html>
```





##### 多个v-model的绑定

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>表单组件配合 v-model</title>
</head>
<body>
  <div id="app">
    <my-input v-model:username="username" v-model:password="password" ></my-input> 
    <button @click="submit">sub</button>
  </div>
</body>
<template id="input">
  <input type="text" placeholder="用户名" :value="username" @input="$emit('update:username', $event.target.value)" />
  <input type="text" placeholder="密码"  :value="password" @input="$emit('update:password', $event.target.value)" />
</template>
<template id="btn">
  <button @click="$emit('my-click')">提交</button>
</template>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const Input = {
    template: '#input',
    props: {
      placeholder: String,
      username: String,  
      password:String
    },
    emits: ['update:username','update:password']
  }


  const { createApp } = Vue

  const app = createApp({
    components: {
      MyInput: Input
    },
    data () {
      return {
        username: '',
        password: ''
      }
    },
    methods: {
      submit () {
        console.log({
          username: this.username,
          password: this.password
        })
      }
    }
  })

  app.mount('#app')
</script>
</html>
```



#### 4.5.3 ref属性标记组件或者dom

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ref标记组件或者dom元素</title>
</head>
<body>
  <div id="app">
    <!-- ref用到自定义组件，可以获取到子组件的实例 -->
    <my-child ref="childRef"></my-child>
    <!-- 原生jsDOM操作 -->
    <input type="text" id="userName" @input="getJsData">
    <!-- ref用到DOM元素上，可以获取到当前的DOM元素 -->
    <input type="text" ref="password" @input="getRefData">
  </div>
</body>
<template id="child">
  <div>
    <h1>使用ref获取子组件的实例</h1>
  </div>
</template>

<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp } = Vue
  const app = createApp({
    components: {
      MyChild: {
        template: '#child',
        data () {
          return {
            count: 10
          }
        },
        computed: {
          doubleCount () {
            return this.count * 2
          }
        },
        methods: {
          print () {
            console.log(this.count)
          }
        }
      }
    },
    mounted () {
      console.log(this)
      // 父组件可以通过 ref 直接获取到子组件的实例的属性和方法等
      console.log(this.$refs.childRef.count)
      console.log(this.$refs.childRef.doubleCount)
      this.$refs.childRef.print()
    },
    methods: {
      getJsData () {
        console.log(document.getElementById('userName').value)
      },
      getRefData () {
        console.log(this.$refs.password.value)
      }
    }
  })
  

  app.mount('#app')
</script>
</html>
```



#### 4.5.4 $parent

当前组件可能存在的父组件实例，如果当前组件是顶层组件，则为 `null`。

完整案例

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>$parent</title>
</head>
<body>
  <div id="app">
    <my-parent></my-parent>
  </div>
</body>
<template id="parent">
  <div>
    我是父组件
    <my-child></my-child>
  </div>
</template>
<template id="child">
  <div>
    我是子组件 - {{ $parent.msg }}
    <button @click="$parent.print()">执行</button>
    <button @click="test">执行</button>
  </div>
</template>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const Parent = {
    template: '#parent',
    components: {
      MyChild: {
        template: '#child',
        methods: {
          test () {
            this.$parent.print()
          }
        }
      }
    },
    data () {
      return {
        msg: 'hello parent'
      }
    },
    methods: {
      print () {
        console.log(this.msg)
      }
    }
  }

  const { createApp } = Vue

  const app = createApp({
    components: {
      MyParent: Parent
    }
  })

  app.mount('#app')

</script>
</html>
```



#### 4.5.5 $root

当前组件树的根组件实例。如果当前实例没有父组件，那么这个值就是它自己。

完整案例:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>$root </title>
</head>
<body>
  <div id="app">
    <my-parent></my-parent>
  </div>
</body>
<template id="parent">
  <div>
    我是父组件 --- {{ $root.count }}
    <my-child></my-child>
  </div>
</template>
<template id="child">
  <div>
    我是子组件 --- {{ $root.count }}
    <button @click="$root.add()">加</button>
  </div>
</template>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const Parent = {
    template: '#parent',
    components: {
      MyChild: {
        template: '#child',
        created () {
          console.log('child', this.$root)
        }
      }
    },
    created () {
      console.log('parent', this.$root)
    }
  }

  const { createApp } = Vue
  const app = createApp({
    components: {
      MyParent: Parent
    },
    data () {
      return {
        count: 100
      }
    },
    methods: {
      add () {
        this.count++
      }
    }
  })

  app.mount('#app')

</script>
</html>
```



#### 4.5.6 vue2事件总线 

​	var bus = new Vue()

<img src="https://s1.ax1x.com/2020/05/25/tpbKDs.png" alt="event bus" style="zoom:67%;" />

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>vue2 兄弟组件传值</title>
</head>
<body>
  <div id="app">
    <my-content></my-content>
    <my-footer></my-footer>
  </div>
</body>
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>
  const bus = new Vue() // 中央事件总线传值

  const Content = {
    template: `<div>{{ type }}</div>`,
    data () {
      return {
        type: '首页'
      }
    },
    mounted () {
      bus.$on('change-type', (val) => {
        this.type = val
      })
    }
  }

  const Footer = {
    template: `
      <footer>
        <ul>
          <li @click="changeType('首页')">首页</li>  
          <li @click="changeType('分类')">分类</li>  
          <li @click="changeType('购物车')">购物车</li>  
          <li @click="changeType('我的')">我的</li>  
        </ul>
      </footer>
    `,
    methods: {
      changeType (type) {
        bus.$emit('change-type', type)
      }
    }
  }

  new Vue({
    components: {
      MyContent: Content,
      MyFooter: Footer
    }
  }).$mount('#app')
  
</script>
</html>
```



vue3中没有明确的兄弟组件传值的方案，可以使用状态提升（找到这两个组件共同的父级组件，然后通过父与子之间的传值实现）

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>vue3 兄弟组件传值-状态提升</title>
</head>
<body>
  <div id="app">
    <my-content :type="type"></my-content>
    <my-footer @change="getVal"></my-footer>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  

  const Content = {
    template: `<div>{{ type }}</div>`,
    props: ['type']
  }

  const Footer = {
    template: `
      <footer>
        <ul>
          <li @click="changeType('首页')">首页</li>  
          <li @click="changeType('分类')">分类</li>  
          <li @click="changeType('购物车')">购物车</li>  
          <li @click="changeType('我的')">我的</li>  
        </ul>
      </footer>
    `,
    methods: {
      changeType (type) {
       this.$emit('change', type)
      }
    }
  }

  Vue.createApp({
    components: {
      MyContent: Content,
      MyFooter: Footer
    },
    data () {
      return {
        type: '首页'
      }
    },
    methods: {
      getVal (type) {
        this.type = type
      }
    }
  }).mount('#app')
  
</script>
</html>
```



## 五. 生命周期

### 5.1 vue2生命周期

每个 Vue 实例在被创建之前都要经过一系列的初始化过程。例如需要设置数据监听、编译模板、挂载实例到 DOM，在数据变化时更新 DOM 等。同时在这个过程中也会运行一些叫做**生命周期钩子**的函数，目的是给予用户在一些特定的场景下添加他们自己代码的机会。

Vue生命周期的**主要阶段**：初始化与挂载阶段，更新阶段，销毁阶段

- 挂载（初始化相关属性）

  - beforeCreate 

    **注意点**：在此时不能获取data中的数据

  - created --- 可以进行ajax或者开启定时器的任务

  - beforeMount 

  - mounted【页面加载完毕的时候就是此时】

- 更新（挂载完毕后，数据更改的时候触发）

  - beforeUpdate

  - updated

    **注意点**：可以重复触发的

- 销毁

  - beforeDestroy --- 可以做清除定时器的一些操作
  - destroyed 

> 销毁（手动）使用 this.$destroy()

关于8个生命周期涉及到的方法，可以参考Vue官网API：

![](https://v2.cn.vuejs.org/images/lifecycle.png)





### 5.2 vue3生命周期

选项式API中将 beforeDestroy 以及 destroyed  修改为 beforeUnmount 和 unmounted，其余一致

![](https://cn.vuejs.org/assets/lifecycle.16e4c08e.png)



### 5.3 动态组件

#### 5.3.1 特殊 Attribute—is

用于绑定[动态组件](https://cn.vuejs.org/guide/essentials/component-basics.html#dynamic-components)。

```
<!-- currentTab 改变时组件也改变 --> 
<component :is="currentTab"></component>
```

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>动态组件</title>
</head>
<body>
  <div id="app">
    <ul>
      <li @click="currentTab='Home'">首页</li>
      <li @click="currentTab='Kind'">分类</li>
      <li @click="currentTab='Cart'">购物车</li>
      <li @click="currentTab='User'">我的</li>
    </ul>
    <!-- 动态组件 -->
    <component :is="currentTab"></component>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const Home = {
    template: `<div>首页Home<input/></div>`
  }
  const Kind = {
    template: `<div>分类Kind</div>`
  }
  const Cart = {
    template: `<div>购物车Cart</div>`
  }
  const User = {
    template: `<div>我的User</div>`
  }

  Vue.createApp({
    components: {
      Home,
      Kind,
      Cart,
      User
    },
    data () {
      return {
        currentTab: 'Home'
      }
    }
  }).mount('#app')
</script>
</html>
```

> 如果此时给Home组件加入一个输入框，输入内容切换组件查看效果，发现切换回来数据不在



#### 5.3.2 `<KeepAlive>`组件

缓存包裹在其中的动态切换组件

`<KeepAlive>` 包裹动态组件时，会缓存不活跃的组件实例，而不是销毁它们。

任何时候都只能有一个活跃组件实例作为 `<KeepAlive>` 的直接子节点。

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>keep-alive</title>
</head>
<body>
  <div id="app">
    <ul>
      <li @click="currentTab='Home'">首页</li>
      <li @click="currentTab='Kind'">分类</li>
      <li @click="currentTab='Cart'">购物车</li>
      <li @click="currentTab='User'">我的</li>
    </ul>

    <!-- 动态组件 -->
    <!-- 实际上is属性的值为组件的名字 -->
    <!-- 可以通过 keep-alive 保留组件的状态，避免组件的销毁和重建 -->
    <keep-alive>
      <component :is="currentTab"></component>
    </keep-alive>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const Home = {
    template: `<div>
        首页 <input />
      </div>`
  }
  const Kind = {
    template: `<div>
        分类 <input />
      </div>`
  }
  const Cart = {
    template: `<div>
        购物车 <input />
      </div>`
  }
  const User = {
    template: `<div>
        我的 <input />
      </div>`
  }

  Vue.createApp({
    components: {
      Home,
      Kind,
      Cart,
      User
    },
    data () {
      return {
        currentTab: 'Home'
      }
    }
  }).mount('#app')
</script>
</html>
```

> 当一个组件在 `<KeepAlive>` 中被切换时，它的 `activated` 和 `deactivated` 生命周期钩子将被调用，用来替代 `mounted` 和 `unmounted`。



#### 5.3.3 activated、deactivated钩子

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>keep-alive钩子函数</title>
</head>
<body>
  <div id="app">
    <ul>
      <li @click="currentTab='Home'">首页</li>
      <li @click="currentTab='Kind'">分类</li>
      <li @click="currentTab='Cart'">购物车</li>
      <li @click="currentTab='User'">我的</li>
    </ul>

    <!-- 动态组件 -->
    <!-- 实际上is属性的值为组件的名字 -->
    <!-- 可以通过 keep-alive 保留组件的状态，避免组件的销毁和重建 -->
    <keep-alive>
      <component :is="currentTab"></component>
    </keep-alive>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  // 假设首页需要保留组件的状态，跳转到新的页面再回到首页时，要确保数据的请求的及时性时效性
  // 以前 mounted 中请求了数据，使用keepalive时再回到首页 mounted 并没有执行
  // 如果要获取最新的数据，请在activated中获取

  // 假设首页长列表，点击某一项可以进入详情，返回首页之后，还希望滚动条在原来的位置
  // 以前在销毁组件的unmounted中记录滚动条位置，但是应用了keep-alive之后，需要在deacvidated中记录滚动条位置
  const Home = {
    template: `<div>
        首页 <input />
      </div>`,
      created () {
        console.log('首页 created')
      },
      unmounted () {
        console.log('首页 unmounted')
      },
      activated () {
        console.log('首页 activated')
      },
      deactivated () {
        console.log('首页 deactivated')
      }
  }
  const Kind = {
    template: `<div>
        分类 <input />
      </div>`,
      created () {
        console.log('分类 created')
      },
      unmounted () {
        console.log('分类 unmounted')
      },
      activated () {
        console.log('分类 activated')
      },
      deactivated () {
        console.log('分类 deactivated')
      }
  }
  const Cart = {
    template: `<div>
        购物车 <input />
      </div>`,
  }
  const User = {
    template: `<div>
        我的 <input />
      </div>`,
  }

  Vue.createApp({
    components: {
      Home,
      Kind,
      Cart,
      User
    },
    data () {
      return {
        currentTab: 'Home'
      }
    }
  }).mount('#app')
</script>
</html>
```

> 默认在keep-alive中所有的组件都进行缓存了
>
> 使用 `include` / `exclude`可以设置哪些组件被缓存，使用 `max`可以设定最多缓存多少个

```html
<!-- 用逗号分隔的字符串 -->
<KeepAlive include="a,b">
<component :is="view"></component>
</KeepAlive>

<!-- 正则表达式 (使用 `v-bind`) -->
<KeepAlive :include="/a|b/">
<component :is="view"></component>
</KeepAlive>

<!-- 数组 (使用 `v-bind`) -->
<KeepAlive :include="['a', 'b']">
<component :is="view"></component>
</KeepAlive>
```

> 组件如果想要条件性地被 `KeepAlive` 缓存，就必须显式声明一个 `name` 选项。

> 完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>选择性缓存</title>
</head>
<body>
<div id="app">
 <ul>
   <li @click="currentTab='Home'">首页</li>
   <li @click="currentTab='Kind'">分类</li>
   <li @click="currentTab='Cart'">购物车</li>
   <li @click="currentTab='User'">我的</li>
 </ul>

 <!-- 用逗号分隔的字符串 注意不要加空格 -->
 <!-- <keep-alive include="home,kind"> -->

 <!-- 正则表达式 (使用 `v-bind`) 使用绑定属性 -->
 <!-- <keep-alive :include="/home|kind/"> -->

 <!-- 数组 (使用 `v-bind`) -->
 <keep-alive :include="['home']">
   <component :is="currentTab"></component>
 </keep-alive>
</div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
const Home = {
 name: 'home',
 template: `<div>
     首页 <input />
   </div>`,
   activated () {
     console.log('首页 activated')
   },
   deactivated () {
     console.log('首页 deactivated')
   }
}
const Kind = {
 name: 'kind',
 template: `<div>
     分类 <input />
   </div>`,
   activated () {
     console.log('分类 activated')
   },
   deactivated () {
     console.log('分类 deactivated')
   }
}
const Cart = {
 name: 'cart',
 template: `<div>
     购物车 <input />
   </div>`,
}
const User = {
 name: 'user',
 template: `<div>
     我的 <input />
   </div>`,
}

Vue.createApp({
 components: {
   Home,
   Kind,
   Cart,
   User
 },
 data () {
   return {
     currentTab: 'Home'
   }
 }
}).mount('#app')
</script>
</html>
```



#### 5.3.4`<component>`元素

一个用于渲染动态组件或元素的“元组件”

完整案例:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>component标签</title>
</head>
<body>
  <div id="app">
    <input type="checkbox" v-model="flag" />
    <!-- 条件为真渲染为 a 标签，否则为 span 标签 -->
    <component :is="flag ? 'a' : 'span'">你好</component>

    <component :is="flag ? 'my-com1' : 'my-com2'"></component>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const Com1 = {
    template: `<div>com1</div>`
  }
  const Com2 = {
    template: `<div>com2</div>`
  }
  Vue.createApp({
    components: {
      MyCom1: Com1,
      MyCom2: Com2
    },
    data () {
      return {
        flag: false
      }
    }
  }).mount('#app')
</script>
</html>
```



#### 5.3.5 DOM 模板解析注意事项（is="vue:组件名"）

当 `is` attribute 用于原生 HTML 元素时，它将被当作 [Customized built-in element](https://html.spec.whatwg.org/multipage/custom-elements.html#custom-elements-customized-builtin-example)，其为原生 web 平台的特性。

但是，在这种用例中，你可能需要 Vue 用其组件来替换原生元素，你可以在 `is` attribute 的值中加上 `vue:` 前缀，这样 Vue 就会把该元素渲染为 Vue 组件(`my-row-component`为自定义组件)：

```
<table>
  <tr is="vue:my-row-component"></tr>
</table>
```

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>DOM模板解析注意事项</title>
</head>
<body>
  <div id="app">
    <table>
      <tr>
        <td>序号</td>
        <td>姓名</td>
        <td>密码</td>
      </tr>
      <!-- 用组件myTr来替换原生元素tr标签 -->
      <tr is="vue:my-tr" :list="list"></tr>
    </table>
  </div>
</body>
<template id="tr">
  <tr v-for="item of list" :key="item.id">
    <td>{{ item.id }}</td>
    <td>{{ item.name }}</td>
    <td>{{ item.password }}</td>
  </tr>
</template>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  Vue.createApp({
    components: {
      myTr: {
        template: '#tr',
        props: ['list'],
      }
    },
    data () {
      return {
        list: [
          {
            id: 1,
            name: '张三',
            password: '123'
          },
          {
            id: 2,
            name: '李四',
            password: '234'
          },
          {
            id: 3,
            name: '王五',
            password: '345'
          }
        ]
      }
    }
  }).mount('#app')
</script>
</html>
```



## 六. slot插槽

组件的最大特性就是 重用 ，而用好插槽能大大提高组件的可重用能力。

**插槽的作用：**父组件向子组件传递内容。

<img src="https://s1.ax1x.com/2020/05/25/tpb9ud.png" alt="slot" style="zoom: 67%;" />

通俗的来讲，**插槽无非就是在** 子组件 **中挖个坑，坑里面放什么东西由** 父组件 **决定。**

插槽类型有：

- 匿名插槽
- 具名插槽
- 作用域插槽

### 6.1 匿名插槽

在父组件中使用子组件的时候，在子组件标签内部写入内容。在子组件的模板中可以通过<slot></slot>来使用

![](https://cn.vuejs.org/assets/slots.dbdaf1e8.png)

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>匿名插槽</title>
</head>
<body>
  <div id="app">
    <fancy-button>
      click me 
    </fancy-button>
    <fancy-button>
      登录 
    </fancy-button>
    <fancy-button>
      注册
    </fancy-button>
  </div>
</body>
<template id="btn">
  <button>
    <slot></slot> 
  </button>
</template>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp } = Vue

  const Button = {
    template: '#btn'
  }

  const app = createApp({
    components: {
      FancyButton: Button
    }
  })

  app.mount('#app')
</script>
</html>
```



附：插槽的默认内容

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>插槽的默认内容</title>
</head>
<body>
  <div id="app">
    <fancy-button>
      click me 
    </fancy-button>
    <fancy-button></fancy-button>
  </div>
</body>
<template id="btn">
  <button>
    <slot>注册</slot> 
  </button>
</template>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp } = Vue

  const Button = {
    template: '#btn'
  }

  const app = createApp({
    components: {
      FancyButton: Button
    }
  })

  app.mount('#app')
</script>
</html>
```



### 6.2 具名插槽(v-slot,简写#)

有时在一个组件中包含多个插槽出口是很有用的。举例来说，在一个 `<BaseLayout>` 组件中，有如下模板：

```html
<div class="container">
  <header>
    <!-- 标题内容放这里 -->
  </header>
  <main>
    <!-- 主要内容放这里 -->
  </main>
  <footer>
    <!-- 底部内容放这里 -->
  </footer>
</div>
```

对于这种场景，`<slot>` 元素可以有一个特殊的 attribute `name`，用来给各个插槽分配唯一的 ID，以确定每一处要渲染的内容：

```html
<div class="container">
  <header>
    <slot name="header"></slot>
  </header>
  <main>
    <slot></slot>
  </main>
  <footer>
    <slot name="footer"></slot>
  </footer>
</div>
```

这类带 `name` 的插槽被称为具名插槽 (named slots)。没有提供 `name` 的 `<slot>` 出口会隐式地命名为“default”。

在父组件中使用 `<BaseLayout>` 时，我们需要一种方式将多个插槽内容传入到各自目标插槽的出口。此时就需要用到**具名插槽**了：

要为具名插槽传入内容，我们需要使用一个含 `v-slot` 指令的 `<template>` 元素，并将目标插槽的名字传给该指令：

```html
<BaseLayout>
  <template v-slot:header>
    <!-- header 插槽的内容放这里 -->
  </template>
</BaseLayout>
```

> `v-slot` 有对应的简写 `#`，因此 `<template v-slot:header>` 可以简写为 `<template #header>`。其意思就是“将这部分模板片段传入子组件的 header 插槽中”。



![](https://cn.vuejs.org/assets/named-slots.ebb7b207.png)

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>具名插槽</title>
</head>
<body>
  <div id="app">
    <base-layout>
      <template v-slot:header>首页头部</template>
      <template v-slot:default>首页内容</template>
      <template v-slot:footer>首页底部</template>
    </base-layout>
    <hr />
    <base-layout>
      <template v-slot:default>分类内容</template>
    </base-layout>
    <hr />
    <base-layout>
      <template #header>我的头部</template>
      <template #default>我的内容</template>
      <template #footer>我的底部</template>
    </base-layout>
  </div>
</body>
<template id="layout">
  <div class="container">
    <header class="header">
      <slot name="header">header</slot>
    </header>
    <div class="content">
      <!-- 不写name时，相当于 写了name="default" -->
      <slot>content!</slot>
    </div>
    <footer class="footer">
      <slot name="footer">footer</slot>
    </footer>
  </div>
</template>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp } = Vue

  const Layout = {
    template: '#layout'
  }

  const app = createApp({
    components: {
      BaseLayout: Layout
    }
  })

  app.mount('#app')
</script>
</html>
```



#### 动态插槽名

[动态指令参数](https://cn.vuejs.org/guide/essentials/template-syntax.html#dynamic-arguments)在 `v-slot` 上也是有效的，即可以定义下面这样的动态插槽名：

```
<base-layout>
  <template v-slot:[dynamicSlotName]>
    ...
  </template>

  <!-- 缩写为 -->
  <template #[dynamicSlotName]>
    ...
  </template>
</base-layout>
```

注意这里的表达式和动态指令参数受相同的[语法限制](https://cn.vuejs.org/guide/essentials/template-syntax.html#directives)。

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>动态插槽名</title>
</head>
<body>
  <div id="app">
    <button @click="count++">{{ count }}</button>
    <my-com>
      <template v-slot:[type]>
        {{ type }}
      </template>
    </my-com>
  </div>
</body>
<template id="com">
  <div >
    <slot name="dynFirst"> 1 动态插槽名</slot>
    <br />
    <slot name="dynLast"> 2 动态插槽名</slot>
  </div>
</template>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp } = Vue
  const Com = {
    template: '#com'
  }
  const app = createApp({
    components: {
      MyCom: Com
    },
    data () {
      return {
        count: 0
      }
    },
    computed: {
      type () {
        return this.count % 2 === 0 ? 'dynLast': 'dynFirst'
      }
    }
  })

  app.mount('#app')
</script>
</html>
```



### 6.3 作用域插槽

在某些场景下插槽的内容可能想要同时使用父组件域内和子组件域内的数据。要做到这一点，我们需要一种方法来让子组件在渲染时将一部分数据提供给插槽。

![](https://cn.vuejs.org/assets/scoped-slots.1c6d5876.svg)

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>作用域插槽</title>
</head>
<body>
  <div id="app">
    <my-com>
      <template v-slot:test="testProps">作用域插槽以及具名插槽-{{testProps.message}}- {{ testProps.count }}</template>
    </my-com>
    <my-com1>
      <template #default="{ message, count }">作用域插槽-{{message}}- {{ count }}</template>
    </my-com1>
  </div>
</body>
<template id="com">
  <div>
    <!-- 一旦使用了具名插槽，在使用作用域插槽时 v-slot:具名="属性名" -->
    <slot name="test" :message="message" :count="1"></slot>
  </div>
</template>
<template id="com1">
  <div>
     <!-- 没有使用具名插槽，在使用作用域插槽时 v-slot="属性名" -->
    <slot :message="message" :count="1"></slot>
  </div>
</template>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp } = Vue

  const Com = {
    template: '#com',
    data () {
      return {
        message: 'hello msg'
      }
    }
  }
  const Com1 = {
    template: '#com1',
    data () {
      return {
        message: 'hello msg1'
      }
    }
  }
  const app = createApp({
    components: {
      MyCom: Com,
      MyCom1: Com1
    }
  })
  app.mount('#app')
</script>
</html>
```



## 七. 依赖注入

通常情况下，当我们需要从父组件向子组件传递数据时，会使用 [props](https://cn.vuejs.org/guide/components/props.html)。想象一下这样的结构：有一些多层级嵌套的组件，形成了一颗巨大的组件树，而某个深层的子组件需要一个较远的祖先组件中的部分数据。在这种情况下，如果仅使用 props 则必须将其沿着组件链逐级传递下去，这会非常麻烦：

![](https://cn.vuejs.org/assets/prop-drilling.11201220.png)



注意，虽然这里的 `<Footer>` 组件可能根本不关心这些 props，但为了使 `<DeepChild>` 能访问到它们，仍然需要定义并向下传递。如果组件链路非常长，可能会影响到更多这条路上的组件。这一问题被称为“prop 逐级透传”，显然是我们希望尽量避免的情况。

`provide` 和 `inject` 可以帮助我们解决这一问题。 [[1\]](https://cn.vuejs.org/guide/components/provide-inject.html#footnote-1) 一个父组件相对于其所有的后代组件，会作为**依赖提供者**。任何后代的组件树，无论层级有多深，都可以**注入**由父组件提供给整条链路的依赖。



![](https://cn.vuejs.org/assets/provide-inject.3e0505e4.png)



### 7.1 provide

要为组件后代提供数据，需要使用到 [`provide`](https://cn.vuejs.org/api/options-composition.html#provide) 选项：

```
{
  provide: {
    message: 'hello!'
  }
}
```

对于 `provide` 对象上的每一个属性，后代组件会用其 key 为注入名查找期望注入的值，属性的值就是要提供的数据。

如果我们需要提供依赖当前组件实例的状态 (比如那些由 `data()` 定义的数据属性)，那么可以以函数形式使用 `provide`：

```
{
  data() {
    return {
      message: 'hello!'
    }
  },
  provide() {
    // 使用函数的形式，可以访问到 `this`
    return {
      message: this.message
    }
  }
}
```

这**不会**使注入保持响应性（比如祖先组件中有一个count的状态，祖先组件修改完状态，后代组件默认的值没有响应式的改变）



### 7.2 inject

要注入上层组件提供的数据，需使用 [`inject`](https://cn.vuejs.org/api/options-composition.html#inject) 选项来声明：

```
{
  inject: ['message'],
  created() {
    console.log(this.message) // injected value
  }
}
```

注入会在组件自身的状态**之前**被解析，因此你可以在 `data()` 中访问到注入的属性：

```
{
  inject: ['message'],
  data() {
    return {
      // 基于注入值的初始数据
      fullMessage: this.message
    }
  }
}
```

> 当以数组形式使用 `inject`，注入的属性会以同名的 key 暴露到组件实例上。在上面的例子中，提供的属性名为 `"message"`，注入后以 `this.message` 的形式暴露。访问的本地属性名和注入名是相同的。
>
> 如果我们想要用一个不同的本地属性名注入该属性，我们需要在 `inject` 选项的属性上使用对象的形式：

```
{
    inject: {
         /* 本地属性名 */ localMessage: {
           from: /* 注入来源名 */ 'message'
         }
    }
}
```



> 这里，组件本地化了原注入名 `"message"` 所提供的的属性，并将其暴露为 `this.localMessage`。
>
> 默认情况下，`inject` 假设传入的注入名会被某个祖先链上的组件提供。如果该注入名的确没有任何组件提供，则会抛出一个运行时警告。
>
> 如果在注入一个值时不要求必须有提供者，那么我们应该声明一个默认值，和 props 类似：

```
{
    // 当声明注入的默认值时,必须使用对象形式
    inject: {
     message: {
       from: 'message', // 当与原注入名同名时，这个属性是可选的
       default: 'default value'
     },
     user: {
       // 对于非基础类型数据，如果创建开销比较大，或是需要确保每个组件实例
       // 需要独立数据的，请使用工厂函数
       default: () => ({ name: 'John' })
     }
    }
}
```

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>依赖注入</title>
</head>
<body>
  <div id="app">
    <button @click="count++">加1</button> {{ count }}
    <my-parent></my-parent>
  </div>
</body>
<template id="parent">
  <div>
    我是父组件 - {{ message }}
    <my-child></my-child>
  </div>
</template>
<template id="child">
  <div>
    我是子组件 - {{ myMessage }} - {{ count }}
  </div>
</template>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const Child = {
    template: '#child',
    inject: {
      myMessage: { // 替换本地名字，
        from: 'message'
      },
      count: {
        default: 100,
      }
    }
  }
  const Parent = {
    template: '#parent',
    inject: ['message'],
    components: {
      MyChild: Child
    }
  }

  const { createApp } = Vue

  const app = createApp({
    components: {
      MyParent: Parent
    },
    data () {
      return {
        message: '传家宝',
        count: 1
      }
    },
    provide () {
      return {
        message: this.message,
        count: this.count
      }
    }
  })

  app.mount('#app')

</script>
</html>
```

> 发现以上案例在count值发生改变时没有更新后代数据



### 7.3 配合响应性 computed()

为保证注入方和供给方之间的响应性链接，我们需要使用 [computed()](https://cn.vuejs.org/api/reactivity-core.html#computed) 函数提供一个计算属性

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>依赖注入配合响应式</title>
</head>
<body>
  <div id="app">
    <button @click="count++">加1</button> {{ count }}
    <my-parent></my-parent>
  </div>
</body>
<template id="parent">
  <div>
    我是父组件 - {{ message }}
    <my-child></my-child>
  </div>
</template>
<template id="child">
  <div>
    我是子组件 - {{ myMessage }} - {{ count }}
  </div>
</template>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  
  const Child = {
    template: '#child',
    inject: {
      myMessage: { // 替换本地名字，
        from: 'message'
      },
      count: {
        default: 100
      }
    }
  }
  const Parent = {
    template: '#parent',
    inject: ['message'],
    components: {
      MyChild: Child
    }
  }

  const { createApp, computed } = Vue

  const app = createApp({
    components: {
      MyParent: Parent
    },
    data () {
      return {
        message: '传家宝',
        count: 1
      }
    },
    provide () {
      return {
        message: this.message,
        // count: this.count
        count: computed(() => this.count) // 响应式关键
      }
    }
  })

  // app.config.unwrapInjectedRef = true
  app.mount('#app')
</script>
</html>
```



vue2中也是这样处理数据：

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>vue2-依赖注入配合响应式</title>
</head>
<body>
<div id="app">
 <button @click="count++">加1</button> {{ count }}
 <my-parent></my-parent>
</div>
</body>
<template id="parent">
<div>
 我是父组件 - {{ message }}
 <my-child></my-child>
</div>
</template>
<template id="child">
<div>
 我是子组件 - {{ myMessage }} - {{ count }}
</div>
</template>
 <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>
const Child = {
 template: '#child',
 inject: {
   myMessage: { // 替换本地名字，
    from: 'message'
   },
   count: {
    default: 100
   }
 }
}
const Parent = {
 template: '#parent',
 inject: ['message'],
 components: {
   MyChild: Child
 }
}
// console.log(Vue.computed)
const { computed } = Vue

new Vue({
 components: {
   MyParent: Parent
 },
 data: {
   message: '传家宝',
   count: 1
 },
 provide () {
   return {
     message: this.message,
     // count: this.count
     count: computed(() => this.count) // 响应式关键
   }
 }
}).$mount('#app')

</script>
</html>
```



## 八. 异步组件

在大型项目中，我们可能需要拆分应用为更小的块，并仅在需要时再从服务器加载相关组件。Vue 提供了 [`defineAsyncComponent`](https://cn.vuejs.org/api/general.html#defineasynccomponent) 方法来实现此功能

### 8.1  定义异步组件

```
import { defineAsyncComponent } from 'vue'

const AsyncComp = defineAsyncComponent(() => {
  return new Promise((resolve, reject) => {
    // ...从服务器获取组件
    resolve(/* 获取到的组件 */)
  })
})
// ... 像使用其他一般组件一样使用 `AsyncComp`
```

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>定义异步组件</title>
</head>
<body>
  <div id="app">
    <my-test></my-test>
    <hr/>
    <my-com></my-com>
  </div>
</body>
<template id="com">
  <div>异步加载组件</div>
</template>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp, defineAsyncComponent } = Vue
  const Com = {
    template: '#com'
  }
  // 定义异步组件。规定了3s以后才会渲染
  const myCom = defineAsyncComponent(() => {
    return new Promise((resolve, reject) => {
      setTimeout(() => {
        resolve(Com)
      }, 3000)
    })
  })

  createApp({
    components: {
      myTest: Com, 
      myCom,  // 注册异步组件
    }
  }).mount('#app')
</script>
</html>
```



### 8.2加载函数

[ES 模块动态导入](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import#dynamic_imports)也会返回一个 Promise，所以多数情况下我们会将它和 `defineAsyncComponent` 搭配使用。类似 Vite 和 Webpack 这样的构建工具也支持此语法，因此我们也可以用它来导入 Vue 单文件组件

```
import { defineAsyncComponent } from 'vue'

const AsyncComp = defineAsyncComponent(() =>
  import('./components/MyComponent.vue')
)
```

以后讲解项目时可以用到，需要在脚手架环境中使用（`单文件组件中使用`）



### 8.3 `<Suspense>`组件

`<Suspense>` 是一个内置组件，用来在组件树中协调对异步依赖的处理，并可以在等待时渲染一个加载状态。

> vue3中新增的

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Suspense</title>
</head>
<body>
  <div id="app">
    <my-test></my-test>
    <hr/>
    <!-- Suspense内部需要一个根组件 -->
    <Suspense>
      <!-- 异步加载组件 -->
      <my-com></my-com>

      <!-- 加载状态 -->
      <template #fallback>
        加载中...
      </template>
    </Suspense>
  </div>
</body>
<template id="com">
  <div>异步加载组件</div>
</template>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp, defineAsyncComponent } = Vue
  const Com = {
    template: '#com'
  }
  const MyCom = defineAsyncComponent(() => {
    return new Promise((resolve, reject) => {
      setTimeout(() => {
        resolve(Com)
      }, 3000)
    })
  })

  createApp({
    components: {
      MyCom,
      MyTest: Com
    }
  }).mount('#app')
</script>
</html>
```

> 后期可以和 `Transition`,`KeepAlive`,`路由`等结合使用



## 九. 自定义指令

除了 Vue 内置的一系列指令 (比如 `v-model` 或 `v-show`) 之外，Vue 还允许你注册自定义的指令 (Custom Directives)。

一个自定义指令由一个包含类似组件生命周期钩子的对象来定义。钩子函数会接收到指令所绑定元素作为其参数。

### 9.1 自定义指令定义和使用

当一个 input 元素被 Vue 插入到 DOM 中后，它会被自动聚焦：

```
  // vue3的全局自定义指令 `v-focus`
  app.directive('focus', { 
     mounted (el) { // el 就是当前指令对应的DOM节点
       el.focus()
     }
   })
   
  // vue2的全局自定义指令 `v-focus`
   Vue.directive('focus', {
      // 当被绑定的元素插入到 DOM 中时……
      inserted: function (el) {
        // 聚焦元素
        el.focus()
      }
   })
```



如果想注册局部指令，组件中也接受一个 `directives` 的选项：

```
// vue3的局部自定义指令 `v-focus`
directives: {
  focus: {
    // 指令的定义
    mounted: function (el) {
      el.focus()
    }
  }
}

// vue2的局部自定义指令 `v-focus`
directives: {
  focus: {
    // 指令的定义
    inserted: function (el) {
      el.focus()
    }
  }
}
```

然后你可以在模板中任何元素上使用新的 `v-focus` 属性，如下：

```
<input v-focus>
```



完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>自定义指令</title>
</head>
<body>
  <div id="app">
    <input type="text" v-focus/>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const app = Vue.createApp({
    directives: {
      focus: {
        mounted (el) {
          el.focus()
        }
      }
    }
  })

  // 全局自定义指令
  // app.directive('focus', { 
  //   mounted (el) { // el 就是当前指令对应的DOM节点
  //     el.focus()
  //   }
  // })

  app.mount('#app')
</script>
</html>
```



### 9.2自定义指令钩子

一个指令的定义对象可以提供几种钩子函数 (都是可选的)：

> vue3相比 vue2，钩子函数做了更新
>
> vue2中一个指令定义对象可以提供如下几个钩子函数 (均为可选)：
>
> - `bind`：只调用一次，指令第一次绑定到元素时调用。在这里可以进行一次性的初始化设置。
> - `inserted`：被绑定元素插入父节点时调用 (仅保证父节点存在，但不一定已被插入文档中)。
> - `update`：所在组件的 VNode 更新时调用，**但是可能发生在其子 VNode 更新之前**。指令的值可能发生了改变，也可能没有。但是你可以通过比较更新前后的值来忽略不必要的模板更新 (详细的钩子函数参数见下)。
> - `componentUpdated`：指令所在组件的 VNode **及其子 VNode** 全部更新后调用。
> - `unbind`：只调用一次，指令与元素解绑时调用。

```js
// vue3钩子函数
const myDirective = {
  // 在绑定元素的 attribute 前或事件监听器应用前调用
  created(el, binding, vnode, prevVnode) {},
  // 在元素被插入到 DOM 前调用
  beforeMount(el, binding, vnode, prevVnode) {},
  // 在绑定元素的父组件及他自己的所有子节点都挂载完成后调用
  mounted(el, binding, vnode, prevVnode) {},
  // 绑定元素的父组件更新前调用
  beforeUpdate(el, binding, vnode, prevVnode) {},
  // 在绑定元素的父组件及他自己的所有子节点都更新后调用
  updated(el, binding, vnode, prevVnode) {},
  // 绑定元素的父组件卸载前调用
  beforeUnmount(el, binding, vnode, prevVnode) {},
  // 绑定元素的父组件卸载后调用
  unmounted(el, binding, vnode, prevVnode) {}
}
```

指令的钩子会传递以下几种参数：

- `el`：指令绑定到的元素。这可以用于直接操作 DOM。
- `binding`：一个对象，包含以下属性。
  - `value`：传递给指令的值。例如在 `v-my-directive="1 + 1"` 中，值是 `2`。
  - `oldValue`：之前的值，仅在 `beforeUpdate` 和 `updated` 中可用。无论值是否更改，它都可用。
  - `arg`：传递给指令的参数 (如果有的话)。例如在 `v-my-directive:foo` 中，参数是 `"foo"`。
  - `modifiers`：一个包含修饰符的对象 (如果有的话)。例如在 `v-my-directive.foo.bar` 中，修饰符对象是 `{ foo: true, bar: true }`。
  - `instance`：使用该指令的组件实例。
  - `dir`：指令的定义对象。
- `vnode`：代表绑定元素的底层 VNode。
- `prevNode`：之前的渲染中代表指令所绑定元素的 VNode。仅在 `beforeUpdate` 和 `updated` 钩子中可用。



给一个元素设置颜色 v-red v-color="green",设置手机号正确为绿色，不正确为红色

完整案例:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>自定义指令钩子函数应用</title>
</head>
<body>
  <div id="app">
    <div v-red>自定义指令 无参数 设置为红色</div>
    <!-- green需要添加 '' 否则被视为 变量 -->
    <div v-color="'green'">自定义指令 有参数 设置为绿色</div>
    <div v-color="'blue'">自定义指令 有参数 设置为蓝色</div>
    <input type="text" v-model="tel" v-tel/>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const app = Vue.createApp({
    data () {
      return {
        tel: ''
      }
    },
    directives: {
      tel: { // 手机号输入时判断是否符合规则，如果符合 显示为绿色 否则为红色
        // 确保输入 使用 updated 钩子
        updated (el) {
          if (/^(?:(?:\+|00)86)?1[3-9]\d{9}$/.test(el.value)) {
            el.style.color = 'green'
          } else {
            el.style.color = 'red'
          }
        }
      }
    }
  })

  app.directive('red', {
    mounted (el) {
      el.style.color = 'red'
    }
  })
  app.directive('color', {
    mounted (el, binding) { // binding.value 指令传递的值
      el.style.color = binding.value
    }
  })

  app.mount('#app')
</script>
</html>
```

> 自定义指令更多的用来实现DOM相关操作

> 上述案例中如果在vue2中，使用 inserted 代替 mounted，使用 update代替updated



## 十. vue3过渡效果

Vue 提供了两个内置组件，可以帮助你制作基于状态变化的过渡和动画：

- `<Transition>` 会在一个元素或组件进入和离开 DOM 时应用动画。
- `<TransitionGroup>` 会在一个 `v-for` 列表中的元素或组件被插入，移动，或移除时应用动画。

除了这两个组件，我们也可以通过其他技术手段来应用动画，比如切换 CSS class 或用状态绑定样式来驱动动画。

### 10.1 `<Transition>` 组件

`<Transition>` 是一个内置组件，这意味着它在任意别的组件中都可以被使用，无需注册。它可以将进入和离开动画应用到通过默认插槽传递给它的元素或组件上。进入或离开可以由以下的条件之一触发：

- 由 `v-if` 所触发的切换
- 由 `v-show` 所触发的切换
- 由特殊元素 `<component>` 切换的动态组件

以下是最基本用法的示例：

```html
<button @click="show = !show">Toggle</button>
<Transition>
  <p v-if="show">hello</p>
</Transition>
```

```scss
/* 下面我们会解释这些 class 是做什么的 */
.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
```

> `<Transition>` 仅支持单个元素或组件作为其插槽内容。如果内容是一个组件，这个组件必须仅有一个根元素。

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>过渡效果</title>
  <style>
    .v-enter-from { opacity: 0; transform: translateX(100px);}
    .v-enter-active { transition: all 3s; }
    .v-enter-to { opacity: 1; transform: translateX(0); }
    .v-leave-from { opacity: 1; transform: translateX(0); }
    .v-leave-active { transition: all 3s; }
    .v-leave-to { opacity: 0; transform: translateX(100px); }
  </style>
</head>
<body>
  <div id="app">
    <button @click="show = !show">切换</button>
    <!-- 默认需要实现6个样式
    v-enter-from
    v-enter-active
    v-enter-to
    v-leave-from
    v-leave-active
    v-leave-to
    -->
    <Transition>
      <h1 v-if="show">显示</h1>
    </Transition>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  Vue.createApp({
    data () {
      return {
        show: false
      }
    }
  }).mount('#app')
</script>
</html>
```



### 10.2 CSS 过渡 class

一共有 6 个应用于进入与离开过渡效果的 CSS class。

![](https://cn.vuejs.org/assets/transition-classes.f0f7b3c9.png)

1. `v-enter-from`：进入动画的起始状态。在元素插入之前添加，在元素插入完成后的下一帧移除。
2. `v-enter-active`：进入动画的生效状态。应用于整个进入动画阶段。在元素被插入之前添加，在过渡或动画完成之后移除。这个 class 可以被用来定义进入动画的持续时间、延迟与速度曲线类型。
3. `v-enter-to`：进入动画的结束状态。在元素插入完成后的下一帧被添加 (也就是 `v-enter-from` 被移除的同时)，在过渡或动画完成之后移除。
4. `v-leave-from`：离开动画的起始状态。在离开过渡效果被触发时立即添加，在一帧后被移除。
5. `v-leave-active`：离开动画的生效状态。应用于整个离开动画阶段。在离开过渡效果被触发时立即添加，在过渡或动画完成之后移除。这个 class 可以被用来定义离开动画的持续时间、延迟与速度曲线类型。
6. `v-leave-to`：离开动画的结束状态。在一个离开动画被触发后的下一帧被添加 (也就是 `v-leave-from` 被移除的同时)，在过渡或动画完成之后移除。

`v-enter-active` 和 `v-leave-active` 给我们提供了为进入和离开动画指定不同速度曲线的能力



### 10.3 为过渡效果命名

我们可以给 `<Transition>` 组件传一个 `name` prop 来声明一个过渡效果名：

```
<Transition name="fade">
  ...
</Transition>
```

对于一个有名字的过渡效果，对它起作用的过渡 class 会以其名字而不是 `v` 作为前缀。比如，上方例子中被应用的 class 将会是 `fade-enter-active` 而不是 `v-enter-active`。这个“fade”过渡的 class 应该是这样：

```
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
```

> 可以结合 css3中的 `transition`以及`animation`实现动画效果



### 10.4 过渡模式

默认动画同时进行的，如果想要调整动画执行的先后顺序，可以采用过渡模式解决。

同时生效的进入和离开的过渡不能满足所有要求，所以 Vue 提供了**过渡模式**

- `in-out`：新元素先进行过渡，完成之后当前元素过渡离开。
- `out-in`：当前元素先进行过渡，完成之后新元素过渡进入。



完整案例

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>过渡效果_name_mode</title>
  <style>
    .slide-enter-from { opacity: 0; transform: translateX(100px);}
    .slide-enter-active { transition: all 2s; }
    .slide-enter-to { opacity: 1; transform: translateX(0); }
    .slide-leave-from { opacity: 1; transform: translateX(0); }
    .slide-leave-active { transition: all 2s; }
    .slide-leave-to { opacity: 0; transform: translateX(100px); }

   
    .fade-enter-from, .fade-leave-to { opacity: 0; }
    .fade-enter-active, .fade-leave-active { transition: all 2s; }
    .fade-enter-to, .fade-leave-from { opacity: 1; }

  </style>
</head>
<body>
  <div id="app">
    <button @click="show = !show">切换</button>
    <!--默认动画同时进行，通过过渡模式解决-->
    <transition name="slide" mode="out-in">
      <h1 v-if="show">显示-if</h1>
      <h1 v-else>显示-else</h1>
    </transition>
    <hr/>
    <!--默认不会渲染额外标签，可以通过tag指明需要渲染什么标签。 内部子元素需要添加key-->
    <transition-group tag='div' name="slide" mode="out-in">
      <h1 v-if="show" key="1">显示-if</h1>
      <h1 v-if="show" key="2">显示-else</h1>
    </transition-group>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  Vue.createApp({
    data () {
      return {
        show: true
      }
    }
  }).mount('#app')
</script>
</html>
```

> 更多信息请参考：https://cn.vuejs.org/guide/built-ins/transition.html#the-transition-component



## 十一. Teleport传送门

> vue3 新增，模仿了 react中 Portal

`<Teleport>` 是一个内置组件，它可以将一个组件内部的一部分模板“传送”到该组件的 DOM 结构外层的位置去。

有时我们可能会遇到这样的场景：一个组件模板的一部分在逻辑上从属于该组件，但从整个应用视图的角度来看，它在 DOM 中应该被渲染在整个 Vue 应用外部的其他地方。

这类场景最常见的例子就是全屏的模态框。理想情况下，我们希望触发模态框的按钮和模态框本身是在同一个组件中，因为它们都与组件的开关状态有关。但这意味着该模态框将与按钮一起渲染在应用 DOM 结构里很深的地方。这会导致该模态框的 CSS 布局代码很难写。

完整案例

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>teleport传送门</title>
  <style>
    .modal {
      position: fixed;
      left: 0;
      right: 0;
      bottom: 0;
      top: 0;
      background-color: rgba(0,0,0,0.4);
    }
    .modal .box {
      width: 50%;
      min-height: 300px;
      background-color: #fff;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }
  </style>
</head>
<body>
  <div id="app">
    <button @click="open=true">打开模态框</button>
    <!-- 审查元素还在 div#app 内部 -->
    <!-- <my-modal v-if="open" @close="close"></my-modal> -->

    <!-- 审查元素得知 位置发生了改变，放在了 body 标签的最底下 -->
    <teleport to="body">
      <my-modal v-if="open" @close="close"></my-modal>
    </teleport>
  </div>
</body>
<template id="modal">
  <div class="modal">
    <div class="box">
      <p>Hello from the modal!</p>
      <button @click="$emit('close')">Close</button>
    </div>
  </div>
</template>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const Modal = {
    template: '#modal'
  }
  Vue.createApp({
    components: {
      myModal: Modal
    },
    data () {
      return {
        open: false
      }
    },
    methods: {
      close () {
        this.open = false
      }
    }
  }).mount('#app')
</script>
</html>
```

> 通过给组件模板添加 `<teleport >`标签审查元素查看结果



## 十二. 混入Mixins

一个包含组件选项对象的数组，这些选项都将被混入到当前组件的实例中。

`mixins` 选项接受一个 mixin 对象数组。这些 mixin 对象可以像普通的实例对象一样包含实例选项，它们将使用一定的选项合并逻辑与最终的选项进行合并。举例来说，如果你的 mixin 包含了一个 `created` 钩子，而组件自身也有一个，那么这两个函数都会被调用。

Mixin 钩子的调用顺序与提供它们的选项顺序相同，且会在组件自身的钩子前被调用。

完整案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>mixins</title>
</head>
<body>
  <div id="app">
    <my-child1></my-child1>
    <hr/>
    <my-child2></my-child2>
  </div>
</body>
<template id="child1">
  <div>
    <h1>child1组件</h1>
    {{ count }} <button @click="add">加1</button>
  </div>
</template>
<template id="child2">
  <div>
    <h1>child2组件</h1>
    {{ count }} <button @click="add">加1</button>
  </div>
</template>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp } = Vue

  const myMixin = {
    data () {
      return {
        count: 10
      }
    },
    methods: {
      add () {
        this.count++
      }
    },
    mounted () {
      console.log('1', this.count)
    }
  }

  const Child1 = {
    // 局部混入
    mixins: [myMixin],
    template: '#child1',
    data () { // 初始化数据相同，组件的 优先级高于 混入
      return {
        count: 100
      }
    },
    mounted () {
      console.log('2', this.count)
    }
  }

  const Child2 = {
    // 局部混入
    mixins: [myMixin],
    template: '#child2',
    methods: {
      add () { // 函数名相同， 组件的优先级高于 混入
        this.count += 10
      }
    },
    mounted () { // 相同的生命周期的钩子函数，先执行混入的代码，再执行组件的代码
      console.log('3', this.count)
    }
  }

  const app = createApp({
    components: {
      MyChild1: Child1,
      MyChild2: Child2
    }
  })

  // 全局混入 // 不建议使用全局混入,会给所有的组件都加入部分代码
  // app.mixin(myMixin)

  app.mount('#app')
</script>
</html>
```

> 除了生命周期钩子函数外，所有的代码都以组件为优先
>
> 生命周期钩子函数先执行 混入的，后执行组件的



## 十三. 两个重要的实例API

### 13.1 $forceUpdate()

强制该组件重新渲染。

鉴于 Vue 的全自动响应性系统，这个功能应该很少会被用到。vue2中对象以及数组的操作,数据改变视图没有更新，可以使用 $forceUpdate 进行强制更新视图

不添加 $forceUpdate 和添加之后对比查看效果

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>forceupdate_vue2</title>
</head>
<body>
  <div id="app">
    <button @click="change(2)">改变arr[2]的数据</button>
    <button @click="clear">清空数组</button>
    <button @click="test">改变obj</button>
    {{ arr[2] && arr[2].c }}
    <ul>
      <li v-for="(item, index) of arr" :key="index">{{item.a}} - {{ item.b }}</li>
    </ul>
    {{ obj.foo }} - {{ obj.bar }}
  </div>
</body>
 <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>
  new Vue({
    data: {
      arr: [
        { a: 1, b:2 },
        { a: 10, b: 20 },
        { a: 100, b: 200 }
      ],
      obj: {
        foo: 'foo'
      }
    },
    methods: {
      change (index) {
        this.arr[index].c = 300 // 给对象数组添加额外的属性
        this.$forceUpdate()
      }, 
      clear () {
        this.arr.length = 0 // 数组长度设置为0 清空数组
        this.$forceUpdate()
      },
      test () {
        this.obj.bar = 'bar' // 对象添加额外的属性
        console.log(this.obj)
        this.$forceUpdate()
      }
    }
  }).$mount('#app')
</script>
</html>
```

> 在vue2中如果只是为了数据改变更新视图，还可以使用 $set 将响应式数据中添加额外的属性也变为响应式



> `set_vue2.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>vue $set</title>
</head>
<body>
<div id="app">
 <button @click="change(2)">改变arr[2]的数据</button>
 <button @click="clear">清空数组</button>
 <button @click="test">改变obj</button>
 {{ arr[2] && arr[2].c }}
 <ul>
   <li v-for="(item, index) of arr" :key="index">{{item.a}} - {{ item.b }}</li>
 </ul>
 {{ obj.foo }} - {{ obj.bar }}
</div>
</body>
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>
new Vue({
 data: {
   arr: [
     { a: 1, b:2 },
     { a: 10, b: 20 },
     { a: 100, b: 200 }
   ],
   obj: {
     foo: 'foo'
   }
 },
 methods: {
   change (index) {
     // this.arr[index].c = 300 // 给对象数组添加额外的属性
     this.$set(this.arr[index], 'c', 300) // 给对象数组添加额外的属性
   }, 
   clear () {
     // this.list.length = 0 // 数组长度设置为0 清空数组
     this.arr = []
   },
   test () {
     // this.obj.bar = 'bar' // 对象添加额外的属性
     this.$set(this.obj, 'bar', 'bar')
     console.log(this.obj)
   }
 }
}).$mount('#app')
</script>
</html>
```



> vue3中的$forceUpdate 一般都用不到，在vue2中实现不了的以上案例，vue3全部支持
>
> `forceupdate_vue3.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>forceupdate_vue3</title>
</head>
<body>
<div id="app">
 <button @click="change(2)">改变arr[2]的数据</button>
 <button @click="clear">清空数组</button>
 <button @click="test">改变obj</button>
 <ul>
   <li v-for="(item, index) of list" :key="index">{{item}}</li>
 </ul>
 {{ arr[2] && arr[2].c }}
 <ul>
   <li v-for="(item, index) of arr" :key="index">{{item.a}} - {{ item.b }}</li>
 </ul>
 {{ obj.foo }} - {{ obj.bar }}
</div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
const app = Vue.createApp({
 data () {
   return {
     list: ['a', 'b', 'c'],
     arr: [
       { a: 1, b:2 },
       { a: 10, b: 20 },
       { a: 100, b: 200 }
     ],
     obj: {
       foo: 'foo'
     }
   }
 },
 methods: {
  change (index) {
    this.arr[index].c = 300 // 给对象数组添加额外的属性
  }, 
  clear () {
    this.arr.length = 0 // 数组长度设置为0 清空数组
  },
  test () {
    this.obj.bar = 'bar' // 对象添加额外的属性
  }
 }
})
app.mount('#app')
</script>
</html>
```

> vue3中没有了 $set 与 $delete



### 13.2 $nextTick()

绑定在实例上的 [`nextTick()`](https://cn.vuejs.org/api/general.html#nexttick) 函数。

和全局版本的 `nextTick()` 的唯一区别就是组件传递给 `this.$nextTick()` 的回调函数会带上 `this` 上下文，其绑定了当前组件实例。

`nextTick.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>nextTick</title>
</head>
<body>
  <div id="app">
    <div ref="oDiv">{{ count }}</div>
    <button @click="add">加1</button>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const app = Vue.createApp({
    data () {
      return {
        count: 1
      }
    },
    methods: {
      add () {
        this.count++
        console.log(this.count) // 2
        console.log(this.$refs.oDiv.innerHTML) // 1
        this.$nextTick(function(){ // 可以获取数据更新后的真实DOM节点的值
          console.log(this.$refs.oDiv.innerHTML) // 2
        })
          
        //Vue.nextTick(()=>{ // 此处需要采用箭头函数，否则内部的this指向有问题，获取不到$refs
        //  console.log(this)
        //  console.log(this.$refs.oDiv.innerHTML) // 2
        //})
      }
    }
  })

  app.mount('#app')
</script>
</html>
```



## 十四. Vue-cli使用

现在使用前端工程化开发项目是主流的趋势，也就是说，我们需要使用一些工具来搭建vue的开发环境。

### **14.1 安装方法**

#### 使用 vue-cli 创建

> 全局安装vue-cli: 

```js
 ## 安装或者升级你的@vue/cli
npm install -g @vue/cli
## 创建
vue create vue_test(项目名称，如果在当前目录的话，用.即可)
## 进入项目
cd vue_test
## 安装依赖
yarn 
## 启动项目
yarn serve

## 查看@vue/cli版本，确保@vue/cli版本在4.5.0以上
vue  -V  
```



> 这里如果你是第一次使用脚手架进行项目创建的话，是只有两项提示。
>

> 第一项是默认配置，我们一般选择第二项自定义配置进行项目构建。
>

> 我们可以自由的选择哪些配置，按键盘上下键进行选中，安装。
>

> 选中哪一个，通过键盘空格键确定，所有的都选择完毕后，按键盘的Enter键进行下一步。
>



需要注意的是：模板创建的时候会询问需要使用EsLint来标准化我们的代码规范

https://www.cnblogs.com/mingjian/p/9361027.html



#### 使用 vite 创建

官方文档：https://cn.vuejs.org/guide/quick-start.html

- 什么是vite？—— 新一代前端构建工具。
- 优势如下：
  - 开发环境中，无需打包操作，可快速的冷启动。
  - 轻量快速的热重载（HMR）。
  - 真正的按需编译，不再等待整个应用编译完成。
- 传统构建vue-cli 与 vite构建对比图

传统打包器(webpack)的流程图

![](https://images.wanjunshijie.com/2021/09/20210919023247902.jpg?imageView2/0/format/webp/q/75)

ESM打包器流程图

![](https://images.wanjunshijie.com/2021/09/20210919023247474.jpg?imageView2/0/format/webp/q/75)



**vite 与 webpack对比：**

> vite服务器启动速度比webpack快，由于vite启动的时候不需要打包，也就无需分析模块依赖、编译，所以启动速度非常快。当浏览器请求需要的模块时，再对模块进行编译，这种按需动态编译的模式，极大缩短了编译时间，当项目越大，文件越多时，vite的开发时优势越明显。vite热更新比webpack快，vite在HRM方面，当某个模块内容改变时，让浏览器去重新请求该模块即可，而不是像webpack重新将该模块的所有依赖重新编译。



```js
## 创建工程
npm init vue@latest

## 进入工程目录
cd <project-name>
## 安装依赖
yarn install
## 运行
yarn dev
```

如果选择[快速上手](https://cn.vuejs.org/guide/quick-start.html#creating-a-vue-application)的方案：

安装eslint & Prettier 

**vite创建项目的时候，prettier的末尾空格出现问题，可以将其改正：**

.prettierrc.json

```
{
  "semi": false,       // 末尾不需要加分号
  "singleQuote": true, // 单引号
  "endOfLine": "auto", // 空格问题
  "trailingComma": "none" // 末尾逗号
}
```

eslinttrc.js

```
rules: {
    'vue/multi-word-component-names': 'off', // 组件名字不需要驼峰命名
  },
```

关闭vscode，重启yarn dev即可！

https://www.jianshu.com/p/4b94540dd998

vite项目创建的需要手动添加eslint的规则，内部才会对于你的代码进行相关的验证！

```js
/* eslint-env node */
module.exports = {
  root: true,
  'extends': [
    'plugin:vue/vue3-essential',
    'eslint:recommended'
  ],
  parserOptions: {
    ecmaVersion: 'latest'
  },
  rules: {
    quotes: [2, 'single'],// 使用单引号 
    'spaced-comment': 'error',
    'key-spacing': 'error'
  }
}
```



### [14.2 单文件组件](https://cn.vuejs.org/v2/guide/single-file-components.html)

vue中的单文件组件包含三部分：**template  script  style** 

内部配置wepack的**vue-loader**来去解析处理解析以.vue为后缀名的单文件组件

- style标签 加上scoped属性，css局部生效 

    [scoped穿透问题！](https://www.jianshu.com/p/0bc2a4b823d4)

- style标签 加上lang="scss"，支持scss

    

#### 1) scoped的穿透

child.vue

```scss
// scoped的深度穿透， 不仅影响自己的span标签，还影响后代的span标签的样式
::v-deep span {  //[data-v-b36379bb] span
  background: yellow;
  width: v-bind(computedWidth); // 当computedWidth=200px & computedWidth=100px
  display: inline-block;
}	
```

```vue
<template>
  <div @click="change" class="child">
    <p class="c-p">
      child... <span @click.stop="flag = !flag">{{ msg }}</span>
    </p>
    <hr />
    <Aaa />
  </div>
</template>

<script>
import { defineComponent } from 'vue'
import Aaa from './Aaa.vue'
export default defineComponent({
  components: {
    Aaa
  },
  props: {
    msg: {
      type: String
    }
  },
  methods: {
    change() {
      // 子父组件通信
      this.$emit('changemsg', 'xxxx')
    }
  },
  data() {
    return {
      flag: true
    }
  },
  computed: {
    computedWidth() {
      return this.flag ? '200px' : '100px'
    }
  }
})
</script>

<!--scoped属性限制样式只能在当前组件可用-->
<style scoped lang="scss">
.c-p {
  color: red;
}
// scoped的深度穿透，不仅影响自己的span标签，还影响后代的span标签的样式
::v-deep span {
  background: yellow;
  width: v-bind(computedWidth); // 当computedWidth=200px & computedWidth=100px
  display: inline-block;
}
</style>

```

```vue
<template>
  <div class="aaa">
    <span>aaa</span>
  </div>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({})
</script>

<style lang="scss" scoped></style>

```



#### 	2) 关闭eslint某些规则

eslinttrc.js

```json
rules: {
     'vue/multi-word-component-names': 'off'  // 组件命名驼峰式关闭
}
```



终极策略： eslint规则，当我们ctrl+s 保存的时候，让其自动帮助改正。

1. 升级最新的版本
2. 安装eslint插件
3. ctrl+shift+p  首选项打开设置  settings.json

```json
   "editor.codeActionsOnSave": {
        "source.fixAll.eslint":true 
    },
    "eslint.workingDirectories": [
        {"mode": "auto"}
    ],
    "vetur.ignoreProjectWarning": true,
    "vetur.validation.template": false,
```

4.打开状态栏，将底部的eslint给它allow开启。



注意：eslint保存的时候忽然缩进4个空格问题：

https://blog.csdn.net/weixin_43485335/article/details/108379638





快速创建组件模板：(会报空格错误，需要在prettier进行配置)

```json
{
	// Place your snippets for vue here. Each snippet is defined under a snippet name and has a prefix, body and 
	// description. The prefix is what is used to trigger the snippet and the body will be expanded and inserted. Possible variables are:
	// $1, $2 for tab stops, $0 for the final cursor position, and ${1:label}, ${2:another} for placeholders. Placeholders with the 
	// same ids are connected.
	// Example:
	// "Print to console": {
	// 	"prefix": "log",
	// 	"body": [
	// 		"console.log('$1');",
	// 		"$2"
	// 	],
	// 	"description": "Log output to console"
	// }
	"Print to vue": {
		"prefix": "vue2",
		"body": [
		 "<template>",
		 "  <div>",
		 "       ",
		 "  </div>",
		 "</template>",
		 "",
		 "<script>",
		 "export default {",
		 "  data () {",
		 "    return {",
		 "       ",
		 "    }",
		 "  },",
		 "  methods: {",
		 "       ",
		 "  }",
		 "}",
		 "</script>",
		 "",
		 "<style lang=\"scss\" scoped>",
		 "",
		 "</style>",
		 ""
		],
		"description": "快速创建vue单文件组件"
	},
	"Print to vue setup": {
		"prefix": "vue3",
		"body": [
		 "<template>\n",
		 
		 "</template>\n",
		 "<script>",
		 "import {defineComponent} from 'vue'\n",
		 "export default defineComponent({",
		 "$1",
		 "})",
		 "</script>\n",
		 "<style lang=\"scss\" scoped>\n",
		 "</style>",
		],
		"description": "快速创建vue3单文件组件"
	}
}
```







#### 	3) proxy代理配置

vue-cli脚手架的vue.config.js配置的：

```json
devServer: {
	 open:true, //自动开启浏览器
     port:8000, //随便改端口号
     proxy: {
         '/api': {
             target: 'https://*.*.com',
             pathRewrite:{
             	'^/api':''
             }
         }
     }
}
```

```js
// axios请求猫眼的数据  因为后端没有设置CORS字段，需要前端通过proxy代理解决
axios.get('/api/ajax/movieOnInfoList?token=&optimus_uuid=A455C0E0F66311EAB68535C86A5B6D1156E0B73EE0934BC586655D13ADC60663&optimus_risk_level=71&optimus_code=10').then(res => {
      console.log(res)
 })
```



vite.config.js

```js
import { fileURLToPath, URL } from 'node:url'

import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [vue()],
  resolve: {
    alias: {
      '@': fileURLToPath(new URL('./src', import.meta.url))
    }
  },
  server: {
    port: 5172,
    proxy: {
      '/db': {
        target: 'http://47.96.0.211:9000'
      }
    }
  }
})

```

```js
axios({
  url: '/db/in_theaters'
}).then((res) => console.log(res))
```



## 十五. 移动端开发

我们现在关注的点还在移动M站上，或者我们可以叫做webapp，其实就是运行在移动端浏览器中的web网站。

app:application应用程序。

手机软件:主要指安装在智能手机上的软件，完善原始系统的不足与个性化。

移动端开发是与PC端肯定是有很大不同的，所以我们需要学习如何在移动设备上开发完美适配的app

> 从屏幕尺寸、屏幕类型等方面来看的话，移动设备和PC设备大有不同，所以从布局、适配等方面都需要我们考虑到

### 15.1 Viewport视口的作用 (在移动端浏览器上面用来显示网页的那一块区域)

在很久以前，我们的设备还不是智能设备的时候，设备访问智能访问到网页的左上角（当时都是pc网站），查看全部内容需要通过滚动条

慢慢的我们发现，我们的一个页面放到移动端中访问的时候，没有滚动条了，但是内容都缩小了

这是因为我们有了一个叫做**viewport**的一个东西

网页不是直接放入浏览器中的，而是先放入到viewport中，然后viewport在等比缩放到浏览器的宽度，放入浏览器，viewport在缩放的过程中，网页内容也被缩小了

网页访问到的clientWidth其实是viewport的宽度

这样的话我们需要做一些处理，其实问题的根源在于viewport的宽度和浏览器宽度不一样，如果我们能将其设置为一样的话，不会出现这样的问题了

我们可以通过meta标签来设置viewport将其设置为浏览器的宽度，也就是设备的宽度，这样的话布局就会简单多了

**viewport的宽度**

当浏览器宽度小于980的时候，宽度就是980，当浏览器尺寸宽度大于980的时候，宽度和浏览器宽度一致

**通过meta标签来设置viewport**

<meta> 标签提供关于 HTML 文档的元数据。它不会显示在页面上，但是对于机器是可读的。可用于浏览器（如何显示内容或重新加载页面），搜索引擎（关键词），或其他 web 服务。

[meta标签大全](http://blog.csdn.net/yc123h/article/details/51356143)

<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">  
meta viewport 的6个属性：

| width         | 设置layout viewport 的宽度，为一个正整数，或字符串"width-device" |
| ------------- | -----------------------------------------------------------: |
| initial-scale |                 设置页面的初始缩放值，为一个数字，可以带小数 |
| minimum-scale |                 设置页面的最小缩放值，为一个数字，可以带小数 |
| maximum-scale |                 允许用户的最大缩放值，为一个数字，可以带小数 |
| height        |       设置layout viewport 的高度，这个属性并不重要，很少使用 |
| user-scalable | 是否允许用户进行缩放，值为"no"或"yes", no 代表不允许，yes代表允许 |



移动端布局方式与设计图

现有的布局方式：

1. 固定布局，每一个元素都是固定的尺寸，内容区域居中在浏览器中间

   内容区域的尺寸：980,1000,1100,1200


2. 响应式布局，利用媒体查询来实现不同尺寸的浏览器显示结构不一样  @media  根据浏览器分辨率大小进行适配

   一般会有三张设计图，PC,平板,手机 

3. 自适应布局，属于响应式里的一种，利用rem、百分比、vwvh等布局单位来实现

   设计图一般只有一张，640、750居多

   

### 15.2 移动端布局

移动的屏幕和PC的屏幕有一个很大的区别，**移动端是视网膜高清屏（Retina）**

**retina屏幕有一个属性叫DPR（设备像素缩放比） = 物理像素/逻辑像素**

例如，iphone 6手机商宣传手机的尺寸是：750宽，这个值就是物理像素，而从开发者眼里我们所指的其实是375px（逻辑像素）

**在dpr为2的手机中，我们的一个逻辑像素会从横纵两个方向分别以2个像素点来渲染**

如果不管dpr的话，其实我们布局依然可以，因为我们设置一个像素宽高的东西的话，在手机上看见的基本也就是这么大，至于手机设备用多少个物理像素去渲染，大小还是不会变化的

设计师出图都是2倍的，是因为，在页面中除了字体（矢量图）大部分都是位图，也就是如果一个像素宽高的盒子里准备放入图片，如果图片的尺寸也是一个像素宽高的话，因为其实在移动端渲染的时候是用四个像素来渲染，图片会失真，但是如果我们给一像素宽高的盒子放入2像素宽高的图片的话，就不会失真

#### 布局单位

>因为我们的移动设备有很多种，所以我们的布局不可能是固定布局，所以我们要使用自适应布局

我们在开发中可以选用很多自适应布局单位，这些单位必须满足一个条件

1. % 

   优点：简单，无需设置，兼容性好
   缺点：基于父元素的属性来设置，如果父元素没有宽高，设置无效

2. vwvh

   一个vw等于viewport宽度的百分之一，一个vh等于viewport高度的百分之一
   vmax等于vw和vh中较大的那个  vmin等于vw和vh中较小的那个

   优点：简单，无需设置
   缺点：兼容性不好

3. rem

   一个rem等于根元素（html）的字体大小，兼容性很好

   优点：兼容好，使用简单
   缺点：需要设置



#### rem适配

当我们想使用一个自适应单位的时候，发现%有缺陷，vwvh兼容性差，弹性盒所针对的是元素排列的问题，只适用于某种情况，所以我们就想，能给我一个没啥上面的缺陷的单位，想到了rem

rem的兼容性好一点，它也确实是一个布局单位，不受父子元素的影响，设置了rem之后，也不会对px、em等单位造成影响，它是一个理想的单位

**rem也有一个致命的问题，就是它不是一个自适应的单位，不会跟着设备尺寸不同而不同，但是没有关系，我们有万能的js，可以去动态的设置它**



方法：

如果设计图是640的图，这个时候我们知道它是照着i5来的，我们现在假设世界上所有的手机都是320的，也就是每一个人用的都是i5，在这个理想的情况下，因为手机都一样，尺寸都一样，和pc端的固定布局也就一样了

假设有一个在640的图上我们量得的宽度是320，因为是二倍图，所以我们知道，它的实际宽度是160px，这样的话，我们直接给这个设置设置width：160px就可以了，这个时候，我们玩个花子，不要单纯的使用px来设置，用rem来设置，例如，我可以将rem设置为100px，这样的，刚才的盒子设置为width：1.6rem，算法就是 量的宽度/(dpr*100) = 要设置的rem值

这样我们就可以开心的开发，量一个尺寸，除个2，再小数点推两位，设置就行了，但是我们也知道，手机的尺寸并不可能都是320，这样的话，没有关系，我们可以根据一个比例来算rem到底设置为多少

用js去设置：

**document.documentElement.style.fontSize = document.documentElement.clientWidth/3.2 + 'px'** 

这样，我们就可以得到一个自适应的rem 



#### rem+vw进行适配

https://www.cnblogs.com/tu-0718/p/10826846.html

https://www.jb51.net/css/731937.html

100vw = 750px ---->  13.333333vw = 100px ---->  html:{font-size:13.3333333vw}






### 15.3 注意的1px边框问题

[1px边框](https://www.jianshu.com/p/5ff121936666)

在移动端中，如果给元素设置一个像素的边框的话，那么在手机上看起来是会比一个像素粗的。

解决方法：使用伪类元素模拟边框，使用transform缩放



 例如google浏览器支持的最小字体是12px,如何让其支持更小字体?

```
transform:scale()  //css3新特性   （关键帧、transform、nth-child高级选择器）
```

















## 十六. vue-router

现在的应用都流行SPA应用（single page application）

传统的项目大多使用多页面结构，需要切换内容的时候我们往往会进行单个html文件的跳转，这个时候受网络、性能影响，浏览器会出现不定时间的空白界面，用户体验不好

**单页面应用就是用户通过某些操作更改地址栏url之后，动态的进行不同模板内容的无刷新切换，用户体验好。**

**Vue中会使用官方提供的vue-router插件来使用单页面，原理就是通过检测地址栏变化后将对应的路由组件进行切换（卸载和安装）**



> SPA vs MPA

<img src="https://s1.ax1x.com/2020/06/01/t8pJ8U.png" alt="spa"  />





### 16.1 简单路由实现

> yarn add vue-router@4

1. 创建router实例

   src/router/index.js

```js
import { createRouter, createWebHashHistory } from 'vue-router'
import FilmsView from '@/views/FilmsView.vue'
import CinemaView from '@/views/CinemaView.vue'
import CenterView from '@/views/CenterView.vue'
import NowplayingView from '@/views/films/NowplayingView.vue'
import ComingSoonView from '@/views/films/ComingSoonView.vue'
const routes = [
  {
    path: '/films',
    component: FilmsView,
  },

  {
    path: '/cinema',
    component: CinemaView
  },
  {
    path: '/center',
    component: CenterView
  },
  {
    path: '/',
    redirect: '/films'  // 内部会直接 /films/nowplaying
  },
  {
    path: '/:pathMatch(.*)',
    redirect: '/films'
  }
]
const router = createRouter({
  history: createWebHashHistory(),
  routes // `routes: routes` 的缩写
})
export default router

```

2. use使用

```js
import { createApp } from 'vue'
import App from './App.vue'
import router from '@/router'
createApp(App).use(router).mount('#app')
```

3. 利用**router-view**来指定路由切换的位置

```vue
 <div>
    <ul>
      <li>
        <router-link to="/films" active-class="orange">电影</router-link>
      </li>
      <li>
        <router-link to="/cinema" active-class="orange">影院</router-link>
      </li>
      <li>
        <router-link to="/center" active-class="orange">我的</router-link>
      </li>
    </ul>

    <!-- <ul>
      <router-link
        to="/films"
        v-bind="$props"
        custom
        v-slot="{ isActive, navigate }"
      >
        <li @click="navigate" :class="isActive ? 'orange' : ''">电影</li>
      </router-link>
      <router-link
        to="/cinema"
        v-bind="$props"
        custom
        v-slot="{ isActive, navigate }"
      >
        <li @click="navigate" :class="isActive ? 'orange' : ''">影院</li>
      </router-link>
    </ul> -->

    <!--渲染path对应的组件页面-->
    <router-view></router-view>
</div>
```



### [16.2 路由的懒加载](https://www.cnblogs.com/lijuntao/p/7777581.html)    

懒加载也叫延迟加载，即在需要的时候进行加载，随用随载。在单页应用中，如果没有应用懒加载，运用webpack打包后的文件将会异常的大，造成进入首页时，需要加载的内容过多，延时过长，不利于用户体验，而**运用懒加载则可以将页面进行划分，需要的时候加载页面，可以有效的分担首页所承担的加载压力，减少首页加载用时**。

非按需加载则会把所有的路由组件块的js包打在一起。当业务包很大的时候建议用路由的按需加载（懒加载）。
按需加载会在页面第一次请求的时候，把相关路由组件块的js添加上；

```json
{
  path: '/about',
  name: 'about',
  component: () => import('@/views/About')    //采用了路由懒加载方式(异步组件+webpack代码分割)
}
```






### 16.3 多级路由

在创建路由表的时候，可以为每一个路由对象创建children属性，值为数组，在这个里面又可以配置一些路由对象来使用多级路由，注意：一级路由path前加'/'

```  js
const routes = [
  {
    path: '/films',
    component: FilmsView, // 一级的视图FilmsView
    name: 'films',
    children: [
      // 希望在一级视图films里面渲染二级视图的话，需要借助children进行配置
      {
        path: '/films',
        redirect: '/films/nowplaying'
      },
      {
        path: '/films/nowplaying',
        component: NowplayingView,
        name: 'np'
      },
      {
        path: '/films/comingsoon',
        component: ComingSoonView,
        name: 'cs'
      }
    ]
  },

  {
    path: '/cinema',
    component: CinemaView
  },
  {
    path: '/center',
    component: CenterView
  },
  {
    path: '/',
    redirect: '/films' // 内部会直接 /films/nowplaying
    // redirect: { name: 'cs' } //name:films只会跳转到films
  },
  {
    path: '/:pathMatch(.*)',
    redirect: '/films'
  }
]
```

二级路由组件的切换位置依然由router-view来指定（指定在父级路由组件的模板中）

```vue
<p>
    <router-link to='/films/nowplaying'>正在热映</router-link>
    <router-link :to='{name:"cs"}'>即将上映</router-link>
</p>
<router-view></router-view>
```



### 16.4 默认路由和重定向

当我们进入应用，默认像显示某一个路由组件，或者当我们进入某一级路由组件的时候想默认显示其某一个子路由组件，我们可以配置默认路由：

```js
{
    path: '/films',
    component: FilmsView,
    name: 'films',
    children: [
      // 希望在一级视图films里面渲染二级视图的话，需要借助children进行配置
      {
        path: '/films',
        redirect: '/films/nowplaying'
      },
      {
        path: '/films/nowplaying',
        component: NowplayingView,
        name: 'np'
      },
      {
        path: '/films/comingsoon',
        component: ComingSoonView,
        name: 'cs'
      }
    ]
  },
```

当我们需要进入之后进行重定向到其他路由的时候，或者当url与路由表不匹配的时候：

```js
{
    path: '/',
    redirect: '/films' // 内部会直接 /films/nowplaying
    // redirect: { name: 'cs' } //name:films只会跳转到films
  },
  {
    path: '/:pathMatch(.*)',
    redirect: '/films'
  }
```



### 16.5 命名路由

我们可以给路由对象配置name属性，这样的话，我们在跳转的时候直接写name:main就会快速的找到此name属性对应的路由，不需要写大量的urlpath路径了

```js
{
    path: '/films',
    component: FilmsView,
    name: 'films',
    children: [
      {
        path: '/films',
        redirect: '/films/nowplaying'
      },
      {
        path: '/films/nowplaying',
        component: NowplayingView,
        name: 'np'
      },
      {
        path: '/films/comingsoon',
        component: ComingSoonView,
        name: 'cs'
      }
    ]
  },
```

```vue
<router-link to='/films/comingsoon'>即将上映</router-link>
<router-link :to='{name:"cs"}'>即将上映</router-link>
```





### 16.6 动态路由匹配    

有的时候我们需要在路由跳转的时候跟上参数，路由传参的参数主要有两种：路由参数、queryString参数

路由参数需要在路由表里设置

```js
{
	path:'/detail/:id',
	component:Detail
}
```

上面的代码就是给User路由配置接收id的参数，多个参数继续在后面设置

在组件中可以通过**this.$route.params**来使用

queryString参数不需要在路由表设置接收，直接设置？后面的内容，在路由组件中通过**this.$route.query**接收





> 面试题？

vue-router 核心的标签？       router-link    router-view

vue-router 核心的api属性？  $route（动态路由参数） vs   $router(编程式导航  push go back forward replace等)







### 16.7 声明式导航 router-link

<router-link> 组件支持用户在具有路由功能的应用中（点击）导航。 通过 to 属性指定目标地址，默认渲染成带有正确链接的 <a> 标签，可以通过配置 tag 属性生成别的标签.。另外，当目标路由成功激活时，链接元素自动设置一个表示激活的 CSS 类名。

router-link的to属性，默认写的是path（路由的路径），可以通过设置一个对象，来匹配更多

```
:to='{name:"detail",params:{id:_new.id},query:{content:_new.content}}'
```

**name是要跳转的路由的名字，也可以写path来指定路径，但是用path的时候就不能使用params传参，params是传路由参数，query传queryString参数**

**replace属性可以控制router-link的跳转不被记录**   

**active-class属性可以控制路径切换的时候对应的router-link渲染的dom添加的类名**

**router-link可以渲染额外的标签**

```vue
<ul>
      <!--采用声明式导航方式进行跳转-->
      <router-link to="/film/nowplaying" custom v-slot="{ isActive,navigate }">
        <li :class="isActive ? 'active' : '' " @click="navigate" role="link">正在热映</li>
      </router-link>
      <router-link to="/film/comingsoon" custom v-slot="{ isActive,navigate }">
        <li :class="isActive ? 'active' : '' " @click="navigate" role="link">即将上映</li>
      </router-link>
 </ul>
```





### 16.8 编程式导航

有的时候需要在跳转前进行一些动作，router-link直接跳转，需要在方法里使用$router的方法 (push/replace/go/back/forward等)

> this.$router.push()
>






### 16.9 路由模式

为了构建SPA（单页面应用），需要引入前端路由系统，这也就是Vue-router存在的意义。前端路由的核心，就在于 ——— 改变视图的同时不会向后端发出请求。

路由有两种模式：hash、history，默认会使用hash模式，但是如果url里不想出现丑陋hash值，在new VueRouter的时候配置mode值为history来改变路由模式，本质使用H5的histroy.pushState方法来更改url，不会引起刷新.

history模式，会出现404 的情况，需要后台配置。

因为我们的应用是个单页客户端应用，如果后台没有正确的配置，当用户在浏览器直接访问 http://oursite.com/user/id 就会返回 404，这就不好看了。

所以呢，你要在服务端增加一个覆盖所有情况的候选资源：如果 URL 匹配不到任何静态资源，则应该返回同一个 index.html 页面，这个页面就是你 app 依赖的页面。

https://www.cnblogs.com/leyan/p/8677274.html

https://blog.csdn.net/ygh5123687/article/details/89473578



> hash模式背后原理： 其实就是调用了window.onhashchange方法 hash值的切换
>
> history模式的原理： 本质使用H5的histroy.pushState方法来更改url





#### hash模式和history模式的区别 

- hash模式较丑，history模式较优雅
- hash兼容IE8以上，history兼容IE10以上
- history模式需要后端配合将所有访问都指向index.html，否则用户刷新页面，会导致404错误

**创建hash的路由模式：**

```js
const router = createRouter({
  // 内部提供了 history 模式的实现。为了简单起见，我们在这里使用 hash 模式。
  history: createWebHashHistory(),
  routes 
})
```



**创建history的路由模式：**

```js
const router = createRouter({
  history: createWebHistory(),
  routes
})
```



如果是history模式的打包，后续需要在nginx.config中进行如下配置，否则页面刷新404！

http>server下添加：

```js
location / {
	try_files $uri $uri/ /index.html;
}
```

最后替换完毕配置文件后，需要重启nginx的配置：

```js
cd /usr/local/nginx/sbin/
./nginx -s reload
```




### 16.10 路由守卫

在某些情况下，当路由跳转前或跳转后、进入、离开某一个路由前、后，需要做某些操作，就可以使用路由钩子来监听路由的变化

#### 全局路由钩子

```js
let isLogin = true
// router.beforeEach((to) => { // 没有使用第三个参数
//   if (!isLogin && to.name !== 'login') {
//     return { name: 'login' }
//   }
// })

// 路由跳转之前做一些业务
router.beforeEach((to, from, next) => { // 使用了第三个参数
  if (to.name !== 'login' && !isLogin) {
    next({ name: 'login' })
  } else {
    next()
  }
})

// 路由跳转之后
router.afterEach((to, from) => {
    //会在任意路由跳转后执行
  console.log('afterEach')
})
```



#### 单个路由钩子

只有beforeEnter，在进入前执行，to参数就是当前路由

```js
 routes: [
    {
      path: '/foo',
      component: Foo,
      //进入到Foo组件之前调用！
      beforeEnter: (to, from, next) => {
        // ...
      }
    }
  ]
```



#### 路由组件钩子

```js
  beforeRouteEnter (to, from, next) {
    // 在渲染该组件的对应路由被 confirm 前调用
    // 不！能！获取组件实例 `this`
    // 因为当守卫执行前，组件实例还没被创建
  },
  beforeRouteUpdate (to, from, next) {
    // 在当前路由改变，但是该组件被复用时调用    
    // 举例来说，对于一个带有动态参数的路径 /detail/:id，在 /detail/1 和 /detail/2 之间跳转的时候，
    // 由于会渲染同样的 Detail 组件，因此组件实例会被复用。而这个钩子就会在这个情况下被调用。
    // 可以访问组件实例 `this`
  },
  beforeRouteLeave (to, from, next) {
    // 导航离开该组件的对应路由时调用
    // 可以访问组件实例 `this`
  }

```



## 十七. Vuex

> Vuex 是一个专为 Vue.js 应用程序开发的**状态管理模式 + 库**。它采用集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化。
>

### 17.1 vuex的安装与简单使用

yarn add vuex@4

store/index.js

```js
import { createStore } from 'vuex'
// 创建一个新的 store 实例
const store = createStore({
  state() {
    // 定义多组件之间的共享状态
    return {
      count: 0
    }
  },
  mutations: {
    // 提供了很多同步修改state状态的方法
    increment(state) {
      state.count++
    }
  }
})

export default store

```

main.js

```js
import { createApp } from 'vue'
import App from './App.vue'
import router from '@/router'
import store from '@/store'
createApp(App).use(router).use(store).mount('#app')
```

cinemaView.vue

```vue
<template>
  <div>cinema...{{ $store.state.count }}</div>
  <button @click="changeCount">更改count</button>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  methods: {
    changeCount() {
      // 可以通过commit触发具体mutations里面的方法
      this.$store.commit('increment')
    }
  }
})
</script>

<style lang="scss" scoped></style>

```



### 17.2 Getters

Vuex 允许我们在 store 中定义“getter”（可以认为是 store 的计算属性）。

store/index.js

```js
getters: {
    // vuex的计算属性
    doubleCount(state) {
      return state.count * 2
    }
  },
```

```vue
<div>
    cinema...{{ $store.state.count }}...{{ $store.getters.doubleCount }}
  </div>
```



### 17.3 Actions

- Action 提交的是 mutation，而不是直接变更状态。

- Action 可以包含任意异步操作。

  store/index.js

  ```js
  actions: {
      incrementAsync(context) {
        setTimeout(() => {
          // 需要调用mutations里面的increment方法，实现count更改
          context.commit('increment')
        }, 1000)
      }
    },
  ```

  ```vue
   <button @click="changeCountAsync">更改count-async</button>
   
   methods: {
      changeCount() {
        this.$store.commit('increment') // 同步的触发mutations方法-通过commit调用
      },
      changeCountAsync() {
        this.$store.dispatch('incrementAsync') // 异步的触发actions方法-通过dispatch调用
      }
    }
  ```



### 17.4 辅助函数使用

#### 	mapState

​		快速的获取vuex的state   需要写在computed中。 

####     mapGetters

​     	快速的获取vuex的getters 需要写在computed中。

​    

```js
import { mapState, mapGetters } from 'vuex'
computed: {
    ...mapState(['count']),
    ...mapGetters(['doubleCount'])
  },
```

```vue
<div>cinema...{{ count }}...{{ doubleCount(3) }}</div>
```



####     mapMutations  

​		快速的获取vuex的mutations   需要写在methods中。

####     mapActions

​		快速的获取vuex的actions   需要写在methods中。 

```js
import { mapState, mapGetters, mapMutations, mapActions } from 'vuex'

methods: {
    ...mapMutations(['increment']),
    ...mapActions(['incrementAsync']),
 }
```

```vue
<button @click="increment(1)">更改count</button>
<button @click="incrementAsync(1)">更改count-async</button>
```



### 17.5 modules

Vuex 允许我们将 store 分割成**模块（module）**。每个模块拥有自己的 state、mutation、action、getter、甚至是嵌套子模块

store/module/countModule.js

```js
export default {
  state() {
    // 定义多组件之间的共享状态
    return {
      count: 0
    }
  },
  getters: {
    doubleCount: (state) => (params) => {
      return state.count * params
    }
  },
  actions: {
    incrementAsync(context, payload) {
      setTimeout(() => {
        // 需要调用mutations里面的increment方法，实现count更改
        context.commit('increment', payload)
      }, 1000)
    }
  },
  mutations: {
    // 提供了很多同步修改state状态的方法
    increment(state, payload) {
      state.count += payload
    }
  }
}

```



store/index.js

```js
import { createStore } from 'vuex'
import countModule from './module/countModule'
const store = createStore({
  modules: {
    // 划分模块
    countModule
  }
})

export default store
```



cinemaView.vue

```vue
<template>
  <div>cinema...{{ countModule.count }}...{{ doubleCount(3) }}</div>
  <button @click="increment(1)">更改count</button>
  <button @click="incrementAsync(1)">更改count-async</button>
</template>

<script>
import { defineComponent } from 'vue'
import { mapState, mapGetters, mapActions, mapMutations } from 'vuex'
export default defineComponent({
  computed: {
    ...mapState(['countModule']), // 需要放模块名字countModule才可以
    ...mapGetters(['doubleCount'])
  },
  methods: {
    ...mapMutations(['increment']),
    ...mapActions(['incrementAsync']),
  }
})
</script>

<style lang="scss" scoped></style>

```



如果采用命名空间的话：

countModule.js

```
  namespaced: true, //开启命名空间
```

CinemaView.vue

```vue
<template>
  <div>cinema...{{ count }}.. {{ doubleCount(2) }}</div>
  <button @click="increment(1)">更改count</button>
  <button @click="incrementAsync(1)">更改count-async</button>
</template>

<script>
import { defineComponent } from 'vue'
import { mapState, mapMutations, mapGetters, mapActions } from 'vuex'
export default defineComponent({
  computed: {
    ...mapState('countModule', ['count']), // 第一个参数指明具体的模块的名字
    ...mapGetters('countModule', ['doubleCount'])
  },
  methods: {
    ...mapMutations('countModule', ['increment']), // this.$store.commit('countModule/increment',1)
    ...mapActions('countModule', ['incrementAsync']),// this.$store.dispatch('countModule/incrementAsync',2)
  }
})
</script>

<style lang="scss" scoped></style>

```



### 17.6 vuex的持久化

vuex是存内存的，浏览器一刷新的的时候，数据重置了，需要与本地存储同步一下

```
yarn add vuex-persistedstate
```

store/index.js

```js
import createPersistedState from "vuex-persistedstate";
const store = createStore({
  plugins: [createPersistedState()],
  modules: {
    // 划分模块
    countModule,
    tabbarModule
  }
})
```

也可以单独指明缓存某个module数据：

```js
plugins: [
    createPersistedState({
      reducer(state) {
        return {
          countModule: state.countModule // 只会缓存countModule这个模块的数据
        }
      }
    })
  ],
```



## 十八. vue3组合式API

### 18.1、组合式API

#### 什么是组合式API

组合式 API (Composition API) 是一系列 API 的集合，使我们可以使用函数而不是声明选项的方式书写 Vue 组件。它是一个概括性的术语，涵盖了以下方面的 API：

- [响应式 API](https://cn.vuejs.org/api/reactivity-core.html)：例如 `ref()` 和 `reactive()`，使我们可以直接创建响应式状态、计算属性和侦听器。
- [生命周期钩子](https://cn.vuejs.org/api/composition-api-lifecycle.html)：例如 `onMounted()` 和 `onUnmounted()`，使我们可以在组件各个生命周期阶段添加逻辑。
- [依赖注入](https://cn.vuejs.org/api/composition-api-dependency-injection.html)：例如 `provide()` 和 `inject()`，使我们可以在使用响应式 API 时，利用 Vue 的依赖注入系统。

组合式 API 是 Vue 3 及 [Vue 2.7](https://blog.vuejs.org/posts/vue-2-7-naruto.html) 的内置功能。对于更老的 Vue 2 版本，可以使用官方维护的插件 [`@vue/composition-api`](https://github.com/vuejs/composition-api)。在 Vue 3 中，组合式 API 基本上都会配合<script setup>语法在单文件组件中使用。

#### 为什么使用它

##### 更好的逻辑复用[#](https://cn.vuejs.org/guide/extras/composition-api-faq.html#better-logic-reuse)

组合式 API 最基本的优势是它使我们能够通过[组合函数](https://cn.vuejs.org/guide/reusability/composables.html)来实现更加简洁高效的逻辑复用。在选项式 API 中我们主要的逻辑复用机制是 mixins，而组合式 API 解决了 [mixins 的所有缺陷](https://cn.vuejs.org/guide/reusability/composables.html#vs-mixins)。

组合式 API 提供的逻辑复用能力孵化了一些非常棒的社区项目，比如 [VueUse](https://vueuse.org/)，一个不断成长的工具型组合式函数集合。组合式 API 还为其他第三方状态管理库与 Vue 的响应式系统之间的集成提供了一套简洁清晰的机制，例如 [RxJS](https://vueuse.org/rxjs/readme.html#vueuse-rxjs)。

##### 更灵活的代码组织[#](https://cn.vuejs.org/guide/extras/composition-api-faq.html#more-flexible-code-organization)

许多用户喜欢选项式 API 的原因是因为它在默认情况下就能够让人写出有组织的代码：大部分代码都自然地被放进了对应的选项里。然而，选项式 API 在单个组件的逻辑复杂到一定程度时，会面临一些无法忽视的限制。这些限制主要体现在需要处理多个**逻辑关注点**的组件中，这是我们在许多 Vue 2 的实际案例中所观察到的。

我们以 Vue CLI GUI 中的文件浏览器组件为例：这个组件承担了以下几个逻辑关注点：

- 追踪当前文件夹的状态，展示其内容
- 处理文件夹的相关操作 (打开、关闭和刷新)
- 支持创建新文件夹
- 可以切换到只展示收藏的文件夹
- 可以开启对隐藏文件夹的展示
- 处理当前工作目录中的变更

这个组件[最原始的版本](https://github.com/vuejs/vue-cli/blob/a09407dd5b9f18ace7501ddb603b95e31d6d93c0/packages/@vue/cli-ui/src/components/folder/FolderExplorer.vue#L198-L404)是由选项式 API 写成的。如果我们为相同的逻辑关注点标上一种颜色，那将会是这样：

![](https://user-images.githubusercontent.com/499550/62783021-7ce24400-ba89-11e9-9dd3-36f4f6b1fae2.png)

你可以看到，处理相同逻辑关注点的代码被强制拆分在了不同的选项中，位于文件的不同部分。在一个几百行的大组件中，要读懂代码中的一个逻辑关注点，需要在文件中反复上下滚动，这并不理想。另外，如果我们想要将一个逻辑关注点抽取重构到一个可复用的工具函数中，需要从文件的多个不同部分找到所需的正确片段。

而如果[用组合式 API 重构](https://gist.github.com/yyx990803/8854f8f6a97631576c14b63c8acd8f2e)这个组件，将会变成下面右边这样：

![](https://user-images.githubusercontent.com/499550/62783026-810e6180-ba89-11e9-8774-e7771c8095d6.png)

现在与同一个逻辑关注点相关的代码被归为了一组：我们无需再为了一个逻辑关注点在不同的选项块间来回滚动切换。此外，我们现在可以很轻松地将这一组代码移动到一个外部文件中，不再需要为了抽象而重新组织代码，大大降低了重构成本，这在长期维护的大型项目中非常关键。

##### 更好的类型推导[#](https://cn.vuejs.org/guide/extras/composition-api-faq.html#better-type-inference)

近几年来，越来越多的开发者开始使用 [TypeScript](https://www.typescriptlang.org/) 书写更健壮可靠的代码，TypeScript 还提供了非常好的 IDE 开发支持。然而选项式 API 是在 2013 年被设计出来的，那时并没有把类型推导考虑进去，因此我们不得不做了一些[复杂到夸张的类型体操](https://github.com/vuejs/core/blob/44b95276f5c086e1d88fa3c686a5f39eb5bb7821/packages/runtime-core/src/componentPublicInstance.ts#L132-L165)才实现了对选项式 API 的类型推导。但尽管做了这么多的努力，选项式 API 的类型推导在处理 mixins 和依赖注入类型时依然不甚理想。

因此，很多想要搭配 TS 使用 Vue 的开发者采用了由 `vue-class-component` 提供的 Class API。然而，基于 Class 的 API 非常依赖 ES 装饰器，在 2019 年我们开始开发 Vue 3 时，它仍是一个仅处于 stage 2 的语言功能。我们认为基于一个不稳定的语言提案去设计框架的核心 API 风险实在太大了，因此没有继续向 Class API 的方向发展。在那之后装饰器提案果然又发生了很大的变动，在 2022 年才终于到达 stage 3。另一个问题是，基于 Class 的 API 和选项式 API 在逻辑复用和代码组织方面存在相同的限制。

相比之下，组合式 API 主要利用基本的变量和函数，它们本身就是类型友好的。用组合式 API 重写的代码可以享受到完整的类型推导，不需要书写太多类型标注。大多数时候，用 TypeScript 书写的组合式 API 代码和用 JavaScript 写都差不太多！这也让许多纯 JavaScript 用户也能从 IDE 中享受到部分类型推导功能。

##### 更小的生产包体积[#](https://cn.vuejs.org/guide/extras/composition-api-faq.html#smaller-production-bundle-and-less-overhead)

搭配 `<script setup>` 使用组合式 API 比等价情况下的选项式 API 更高效，对代码压缩也更友好。这是由于 `<script setup>` 形式书写的组件模板被编译为了一个内联函数，和 `<script setup>` 中的代码位于同一作用域。不像选项式 API 需要依赖 `this` 上下文对象访问属性，被编译的模板可以直接访问 `<script setup>` 中定义的变量，无需一个代码实例从中代理。这对代码压缩更友好，因为本地变量的名字可以被压缩，但对象的属性名则不能。



#### 第一个组合式API的例子

`composition.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>体验组合式API</title>
</head>
<body>
  <div id="app">
    <button @click="increment">点击了{{ count }}次</button>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp, ref, onMounted, onUpdated } = Vue

  const app = createApp({
    setup () { // 组合式API
      const count = ref(0)
      const increment = () => {
        count.value += 1
      }
      onMounted(() => { // 生命周期钩子函数
        document.title = `点击次数为${count.value}`
      })
      onUpdated(() => {
        document.title = `点击次数为${count.value}`
      })
      return {
        count,
        increment
      }
    }
  })
  app.mount('#app')
</script>
</html>
```

> 提取公共部分
>
> `composition_hooks.html`
>
> ```html
> <!DOCTYPE html>
> <html lang="en">
> <head>
> <meta charset="UTF-8">
> <meta http-equiv="X-UA-Compatible" content="IE=edge">
> <meta name="viewport" content="width=device-width, initial-scale=1.0">
> <title>提取复用代码</title>
> </head>
> <body>
> <div id="app">
>  <button @click="increment">点击了{{ count }}次</button>
> </div>
> </body>
> <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
> <script>
> const { createApp, ref, onMounted, onUpdated } = Vue
> 
> const useCount = () => {
>  const count = ref(0)
>  const increment = () => {
>    count.value += 1
>  }
>  return {
>    count,
>    increment
>  }
> }
> 
> const useTitle = (count) => {
>  onMounted(() => { 
>    document.title = `点击次数为${count.value}`
>  })
>  onUpdated(() => {
>    document.title = `点击次数为${count.value}`
>  })
> }
> const app = createApp({
>  setup () { // 组合式API
>    const { count, increment } = useCount() // 自定义hooks
>    useTitle(count) // 自定义hooks
>    return {
>      count,
>      increment
>    }
>  }
> })
> 
> app.mount('#app')
> </script>
> </html>
> ```





### 18.2、setup()函数

`setup()` 钩子是在组件中使用组合式 API 的入口，通常只在以下情况下使用：

1. 需要在非单文件组件中使用组合式 API 时。
2. 需要在基于选项式 API 的组件中集成基于组合式 API 的代码时。

**其他情况下，都应优先使用 [`<script setup>`](https://cn.vuejs.org/api/sfc-script-setup.html) 语法。**

#### 基本使用

我们可以使用[响应式 API](https://cn.vuejs.org/api/reactivity-core.html) 来声明响应式的状态，在 `setup()` 函数中返回的对象会暴露给模板和组件实例。其它的选项也可以通过组件实例来获取 `setup()` 暴露的属性

```vue
<script>
import { ref } from 'vue'

export default {
  setup() {
    const count = ref(0)
    // 返回值会暴露给模板和其他的选项式 API 钩子
    return {
      count
    }
  },
  mounted() {
    console.log(this.count) // 0
  }
}
</script>

<template>
  <button @click="count++">{{ count }}</button>
</template>

```



请注意在模板中访问从 `setup` 返回的 [ref](https://cn.vuejs.org/api/reactivity-core.html#ref) 时，它会[自动浅层解包](https://cn.vuejs.org/guide/essentials/reactivity-fundamentals.html#deep-reactivity)，因此你无须再在模板中为它写 `.value`。当通过 `this` 访问时也会同样如此解包。

> `setup()` 自身并不含对组件实例的访问权，即在 `setup()` 中访问 `this` 会是 `undefined`。你可以在选项式 API 中访问组合式 API 暴露的值，但反过来则不行。

`composition_setup_base.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>setup的基本使用</title>
</head>
<body>
  <div id="app">
    {{ count }}
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp, ref, onMounted, onUpdated } = Vue

  const app = createApp({
    setup () { // 组合式API
      // 创建了响应式变量
      const count = ref(0)
      // 返回值会暴露给模板和其他的选项式 API 钩子
      return {
        count
      }
    },
    data () { // 虽然设置了同名的变量，但是显示的是 组合式API中的数据
      return {
        count: 100
      }
    },
    mounted () {
      console.log(this.count) // 0
    }
  })

  app.mount('#app')
</script>
</html>
```



#### 访问 Prop

`setup` 函数的第一个参数是组件的 `props`。和标准的组件一致，一个 `setup` 函数的 `props` 是响应式的，并且会在传入新的 props 时同步更新。

```js
{
  props: {
    title: String,
    count: Number
  },
  setup(props) {
    console.log(props.title)
    console.log(props.count)
  }
}
```

> 请注意如果你解构了 `props` 对象，解构出的变量将会丢失响应性。因此我们推荐通过 `props.xxx` 的形式来使用其中的 props。

如果你确实需要解构 `props` 对象，或者需要将某个 prop 传到一个外部函数中并保持响应性，那么你可以使用 [toRefs()](https://cn.vuejs.org/api/reactivity-utilities.html#torefs) 和 [toRef()](https://cn.vuejs.org/api/reactivity-utilities.html#toref) 这两个工具函数：

```js
{
  setup(props) {
    // 将 `props` 转为一个其中全是 ref 的对象，然后解构
    const { title } = toRefs(props)
    // `title` 是一个追踪着 `props.title` 的 ref
    console.log(title.value)

    // 或者，将 `props` 的单个属性转为一个 ref
    const title = toRef(props, 'title')
  }
}
```

`composition_setup_props.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>setup访问props</title>
</head>
<body>
  <div id="app">
    {{ count }} <button @click="count++">加1</button>
    <my-com :count="count"></my-com>
  </div>
</body>
<template id="com">
  <div>
    <h1>子组件</h1>
    {{ count }} -- {{doubleCount}}
  </div>
</template>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp, ref, computed, toRefs, toRef } = Vue
  const Com = {
    template: '#com',
    props: {
      count: Number
    },
    setup (props) {
      // console.log(props)
      // 1.计算属性 - 响应式
      // const doubleCount = computed(() => props.count * 2)

      // 2.不要把props中的数据解构，解构会丢失响应式
      // const { count } = props // 模板中 doubleCount 始终为 0
      // const doubleCount = computed(() => count * 2)

      // 3.如果既需要解构，还要保持响应式 toRefs
      // const { count } = toRefs(props) // 将 `props` 转为一个其中全是 ref 的对象，然后解构
      // const doubleCount = computed(() => count.value * 2) // ref对象访问值通过 value 属性

      // 4.保持响应式 toRef
      const count = toRef(props, 'count') // 将 `props` 的单个属性转为一个 ref
      const doubleCount = computed(() => count.value * 2)

      return {
        doubleCount
      }
    }
  }

  const app = createApp({
   components: {
    myCom: Com
   },
   setup () {
    const count = ref(0)
    return {
      count
    }
   }
  })

  app.mount('#app')
</script>
</html>
```



#### Setup的上下文

传入 `setup` 函数的第二个参数是一个 **Setup 上下文**对象。上下文对象暴露了其他一些在 `setup` 中可能会用到的值：

```
{
  setup(props, context) {
    // 透传 Attributes（非响应式的对象，等价于 $attrs）
    console.log(context.attrs)

    // 插槽（非响应式的对象，等价于 $slots）
    console.log(context.slots)

    // 触发事件（函数，等价于 $emit）
    console.log(context.emit)

    // 暴露公共属性（函数）
    console.log(context.expose)
  }
}
```

该上下文对象是非响应式的，可以安全地解构：

```
{
  setup(props, { attrs, slots, emit, expose }) {
    ...
  }
}
```



`expose` 函数用于显式地限制该组件暴露出的属性，当父组件通过[模板引用](https://cn.vuejs.org/guide/essentials/template-refs.html#ref-on-component)访问该组件的实例时，将仅能访问 `expose` 函数暴露出的内容

`composition_setup_context.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>setup上下文对象-attrs-slots-emit-expose</title>
</head>
<body>
  <div id="app">
    <!-- 1.验证 上下文对象中的 attrs 属性 -->
    <!-- <my-com class="active" style="color: red" id="box" @click="test" @my-event="getData"></my-com> -->
    <!-- 2.验证上下文对象中的 slots 属性 -->
    <my-com ref="child" class="active" style="color: red" id="box" @click="test" @my-event="getData">
      <template #default>
        111
      </template>
      <template #footer>
        222
      </template>
    </my-com>
  </div>
</body>
<template id="com">
  <div>
    <h1>子组件</h1>
    <button @click="sendData">传值给父组件</button>
    <slot>333</slot>
    <slot name="footer"></slot>
  </div>
</template>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp, ref, computed, toRefs, toRef, onMounted } = Vue

  const Com = {
    template: '#com',
    // mounted(){
    //   console.log('this-->',this.$attrs,this.$slots)
    // },
    setup (props, context) {
      // 1.透传 Attributes（非响应式的对象，等价于 $attrs）
      // { class: 'active', id: 'box', style: {color:'red'}, onClick: fn,onMyEvent:fn}
      console.log(context.attrs)

      // 2.插槽（非响应式的对象，等价于 $slots）
      console.log(context.slots) // { default: fn, footer: fn }

      // 3. 触发事件（函数，等价于 $emit）
      const sendData = () => {
        // 选项式组件 this.$emit('my-event', 1000)
        // 组合式组件 不可以在setup中访问this
        context.emit('my-event', 1000)
      }

      // 4.暴露公共属性（函数） 
      const msg = ref('hello composition api')
      const name = ref('zhangsan')
      const changeName = () => {
        name.value = '张三'
      }
      context.expose({ // 父组件可以通过 ref 获取到暴露出去的数据和方法
        name, changeName
      })
      return {
        sendData
      }
    }
  }

  const app = createApp({
   components: {
    MyCom: Com
   },
   setup () {
    const test = () => {console.log('test...')}
    const getData = (val) => {
      console.log(val)
    }
    // 组合式api 给组件定义ref
    const child = ref()
    onMounted(() => {
      // console.log('msg', this) // this指向window,不能this.$refs.child使用！
      // console.log('msg', child.value.msg) // undefined 因为子组件没有 expose 这个值
      
      // child.value.changeName() // 调用child组件暴露的changeName方法
      // console.log('name', child.value.name) // zhangsan
    })
    return {
      child, // 一定将child向外暴露，在模板中通过ref='child'
      test,
      getData
    }
   },
  //  mounted () { // 选项式API获取子组件实例
  //   console.log('msg', this.$refs.child.msg) // undefined 因为子组件没有 expose 这个值
  //   console.log('name', this.$refs.child.name) // zhangsan
  //  }
  })

  app.mount('#app')
</script>
</html>
```

> 在父组件通过ref获取子组件的实例的属性和方法的需求中，需要注意：
>
> 1.如果子组件是 选项式API组件，基本不需要做任何操作
>
> 2.如果子组件是 组合式API组件，需要通过 context.expose 暴露给父组件需要使用的属性和方法
>
> 3.如果父组件使用 选项式API, 可以通过 this.$refs.refName 访问到子组件想要你看到的属性和方法
>
> 4.如果父组件使用 组合式API,需要在setup中先创建 refName，然后再访问子组件expose暴露的属性和方法（const refName = ref()    refName.value.X）



#### 与渲染函数一起使用

`setup` 也可以返回一个[渲染函数](https://cn.vuejs.org/guide/extras/render-function.html)，此时在渲染函数中可以直接使用在同一作用域下声明的响应式状态：

```
{
  setup() {
    const count = ref(0)
    return () => h('div', count.value)
  }
}
```

返回一个渲染函数将会阻止我们返回其他东西。对于组件内部来说，这样没有问题，但如果我们想通过模板引用将这个组件的方法暴露给父组件，那就有问题

我们可以通过调用 [`expose()`](https://cn.vuejs.org/api/composition-api-setup.html#exposing-public-properties) 解决这个问题：

```
{
  setup(props, { expose }) {
    const count = ref(0)
    const increment = () => ++count.value

    expose({
      increment
    })

    return () => h('div', count.value)
  }
}
```

`composition_setup_render_function.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>setup渲染函数</title>
</head>
<body>
  <div id="app">
    <button @click="add">加1</button>
    <my-com ref="com" ></my-com>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp, ref, h } = Vue
  const Com = {
    setup (props, { expose,emit }) {
      const count = ref(0)
      const increment = () => {
        count.value += 1
      } 
       expose({ // 关键将increment方法向外暴露给父组件调用
         increment
       })
      return () => h('div', { class: 'box' }, count.value)
    }
  }
  const app = createApp({
    components: {
      myCom: Com
    },
    setup (props,{emit}) { // 组合式API
      const com = ref()
      const add = () => {
        com.value.increment() // 获取到子组件向外暴露的increment方法
      }
      return {
        com,
        add,
      }
    }
  })

  app.mount('#app')
</script>
</html>
```



上述代码等价于：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>setup渲染函数</title>
</head>
<body>
  <div id="app">
    <button @click="add">加1</button>
    <my-com ref="com" ></my-com>
  </div>

  <template id="com">
    <div>{{count}}</div>
  </template>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp, ref, h } = Vue
  const Com = {
    template:'#com',
    setup (props, { expose,emit }) {
      const count = ref(0)
      const increment = () => {
        count.value += 1
      } 
      return {
        count,
        increment  // 可以放在此处向外暴露，也可以借助expose进行外部暴露
      }
    }
  }
  const app = createApp({
    components: {
      myCom: Com
    },
    setup (props,{emit}) { // 组合式API
      const com = ref()
      const add = () => {
        com.value.increment()
      }
      return {
        com,
        add,
      }
    }
  })

  app.mount('#app')
</script>
</html>
```



### 18.3、响应式核心

#### ref()

接受一个内部值，返回一个响应式的、可更改的 ref 对象，此对象只有一个指向其内部值的属性 `.value`。

ref 对象是可更改的，也就是说你可以为 `.value` 赋予新的值。它也是响应式的，即所有对 `.value` 的操作都将被追踪，并且写操作会触发与之相关的副作用。

如果将一个对象赋值给 ref，那么这个对象将通过 [reactive()](https://cn.vuejs.org/api/reactivity-core.html#reactive) 转为具有深层次响应式的对象。

**将一个 ref对象赋值给一个 reactive 对象属性值的时后，此 ref 会被自动解包**

`composition_ref.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>composition_ref</title>
</head>
<body>
  <div id="app">
    count: <button @click="add">加1</button>{{ count }} <br />
    state.count: <button @click="increment">加1</button> {{ state.count }} <br />
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp, ref, reactive } = Vue

  const app = createApp({
    setup () {
      // 1.ref 对象是可更改的，也就是说你可以为 `.value` 赋予新的值
      const count = ref(0)
      const add = () => {
        count.value += 1
      }

      // 2.如果将一个对象赋值给 ref，那么这个对象将通过 reactive() 转为具有深层次响应式的对象。
      const state = ref({ count: 10 })
      const increment = () => {
        state.value.count += 1
      }

      // 3.将一个 ref对象count赋值给一个 reactive对象属性值时候，此ref对象会被自动解包
      const obj = reactive({}) 
      obj.count = count 
      // 该 ref 会被自动解包
      console.log(obj.count) // 0

      // 一定要返回，暴露给页面模板使用
      return {
        count,
        add,
        state,
        increment
      }

    }
  })

  app.mount('#app')
</script>
</html>
```

> 以后创建 非 对象类型的数据 使用  ref， 创建对象类型的数据建议使用 reactive

#### computed ()

接受一个 getter 函数，返回一个只读的响应式 [ref](https://cn.vuejs.org/api/reactivity-core.html#ref) 对象。该 ref 通过 `.value` 暴露 getter 函数的返回值。它也可以接受一个带有 `get` 和 `set` 函数的对象来创建一个可写的 ref 对象。

创建一个只读的计算属性 ref：

```
const count = ref(1)
const plusOne = computed(() => count.value + 1)

console.log(plusOne.value) // 2

plusOne.value++ // 错误
```

创建一个可写的计算属性 ref：

```
const count = ref(1)
const plusOne = computed({
  get: () => count.value + 1,
  set: (val) => {
    count.value = val - 1
  }
})

plusOne.value = 1
console.log(count.value) // 0
```

`composition_computed.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>composition_computed</title>
</head>
<body>
  <div id="app">
    count: <button @click="add">加1</button>{{ count }} - {{ doubleCount }} - {{ plusOne }}<br />
    <button @click="updateComputed">改变计算属性的值</button>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp, ref, computed } = Vue

  const app = createApp({
    setup () {
      // 1.基本计算属性 - 一个只读的计算属性 ref
      const count = ref(0)
      const add = () => {
        count.value += 1
      }
      const doubleCount = computed(() => count.value * 2)


      // 2.创建一个可写的计算属性 ref：
      const plusOne = computed({
        get () { return count.value + 1 },
        set (val) { count.value = val - 1 }
      })

      const updateComputed = () => {
        plusOne.value = 100
        console.log('count', count.value) // 99
      }
      return {
        count,
        add,
        doubleCount,
        plusOne,
        updateComputed
      }

    }
  })

  app.mount('#app')
</script>
</html>
```

#### reactive()

返回一个对象的响应式代理。

响应式转换是“深层”的：它会影响到所有嵌套的属性。一个响应式对象也将深层地解包任何 [ref](https://cn.vuejs.org/api/reactivity-core.html#ref) 属性，同时保持响应性。

值得注意的是，当访问到某个响应式数组或 `Map` 这样的原生集合类型中的 ref 元素时，不会执行 ref 的解包。

返回的对象以及其中嵌套的对象都会通过 [ES Proxy](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy) 包裹，因此**不等于**源对象，建议只使用响应式代理，避免使用原始对象。

创建一个响应式对象：

```
const obj = reactive({ count: 0 })
obj.count++
```

ref 的解包：

```
const count = ref(1)
const obj = reactive({ count })

// ref 会被解包
console.log(obj.count === count.value) // true

// 会更新 `obj.count`
count.value++
console.log(count.value) // 2
console.log(obj.count) // 2

// 也会更新 `count` ref
obj.count++
console.log(obj.count) // 3
console.log(count.value) // 3
```

注意当访问到某个响应式数组或 `Map` 这样的原生集合类型中的 ref 元素时，**不会**执行 ref 的解包：

```
const books = reactive([ref('Vue 3 Guide')])
// 这里需要 .value
console.log(books[0].value)

const map = reactive(new Map([['count', ref(0)]]))
// 这里需要 .value
console.log(map.get('count').value)
```

将一个 [ref](https://cn.vuejs.org/api/reactivity-core.html#ref) 赋值给为一个 `reactive` 属性值时，该 ref 会被自动解包：（讲解ref时已经说明）

```
const count = ref(1)
const obj = reactive({count})


console.log(obj.count) // 1
console.log(obj.count === count.value) // true
```

`composition__reactive.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>composition_reactive</title>
</head>
<body>
  <div id="app">
    state.count: <button @click="add">加1</button>{{ state.count }}<br />
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp, ref, reactive } = Vue

  const app = createApp({
    setup () {
      const state = reactive({ count: 10})
      const add = () => {
        state.count++
      }

      // ref的解包
      const count = ref(1)
      const obj = reactive({ count })
      console.log(count.value === obj.count) // true

      count.value++
      console.log(count.value) // 2
      console.log(obj.count) // 2

      obj.count++
      console.log(count.value) // 3
      console.log(obj.count) // 3

      // 注意当访问到某个响应式数组或 `Map` 这样的原生集合类型中的 ref 元素时，不会执行 ref 的解包
      const books = reactive([ref('vue3 指南')])
      console.log(books[0].value) // vue3 指南
      const map = reactive(new Map([['count', ref(0)]]))
      console.log(map.get('count').value) // 0
      
      return {
        state,
        add
      }

    }
  })

  app.mount('#app')
</script>
</html>
```

>  对象响应式处理借助reactive  其余的用ref

#### readonly()

接受一个对象 (不论是响应式还是普通的) 或是一个 [ref](https://cn.vuejs.org/api/reactivity-core.html#ref)，返回一个原值的只读代理。

只读代理是深层的：对任何嵌套属性的访问都将是只读的。它的 ref 解包行为与 `reactive()` 相同，但解包得到的值是只读的。

```
const original = reactive({ count: 0 })

const copy = readonly(original)

watchEffect(() => {
  // 用来做响应性追踪
  console.log(copy.count)
})

// 更改源属性会触发其依赖的侦听器
original.count++

// 更改该只读副本将会失败，并会得到一个警告
copy.count++ // warning
```



`composition_readonly.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>composition_readonly</title>
</head>
<body>
  <div id="app">
    {{ count }} <button @click="addCount">修改count</button> <br />
    {{ copy }} <button @click="addCopy">修改copy</button>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp, ref, reactive, readonly } = Vue

  const app = createApp({
    setup () {
      const count = ref(10)
      const addCount = () => {
        count.value += 1
      }
      const copy = readonly(count)
      const addCopy = () => { // Set operation on key "value" failed: target is readonly. 
        copy.value += 1
      }
      return {
        count,
        addCount,
        copy,
        addCopy
      }
    }
  })

  app.mount('#app')
</script>
</html>
```



#### watchEffect()

立即运行一个函数，同时响应式地追踪其依赖，并在依赖更改时重新执行。

第一个参数就是要运行的副作用函数。这个副作用函数的参数也是一个函数，用来注册清理回调。清理回调会在该副作用下一次执行前被调用，可以用来清理无效的副作用，例如等待中的异步请求。

返回值是一个用来停止该副作用的函数。

```
const count = ref(0)

watchEffect(() => console.log(count.value))
// -> 输出 0

count.value++
// -> 输出 1
```

副作用清除：

```js
watchEffect((onInvalidate) => {
    console.log(id.value) 
    const timer = setTimeout(() => {
        console.log('请求成功') // 2秒之内点击列表 只显示一次
        data.value = '数据' + id.value
    }, 2000)
    onInvalidate(() => {
        clearTimeout(timer)
    })
})
```

停止侦听器：

```js
 const stop = watchEffect(() => {
     console.log(count.value)
 })
 // 当不再需要此侦听器时:
 const stopWatch = () => {
     stop()
 }
```

`composition_watchEffect.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>composition_watchEffect</title>
</head>
<body>
  <div id="app">
    <button @click="increment">点击了{{ count }}次</button>
    <button @click="stopWatch">停止监听</button>
    <ul>
      <li @click="id=1">请求第一条数据</li>
      <li @click="id=2">请求第二条数据</li>
    </ul>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp, ref, watchEffect } = Vue

  const app = createApp({
    setup () {
      const count = ref(0)
      const increment = () => {
        count.value = 1
      }

      const stop = watchEffect(() => {
        console.log(`监听到count的数据为${count.value}`)
      })
      // 停止监听后，当依赖项count发生改变了，也不会触发了
      const stopWatch = () => {
        stop()
      }
      
      const id = ref(1)
      watchEffect((onInvalidate) => {
        console.log(id.value) 
        const timer = setTimeout(() => {
          console.log(`请求第${id.value}条数据`)
        }, 3000)
        onInvalidate(() => { // 当id改变的时候，此回调就会执行，可以清除上一次的timer
          console.log('清除')
          clearTimeout(timer)
        })
      })
      return {
        count,
        increment,
        stopWatch,
        id
      }
    }
  })

  app.mount('#app')
</script>
</html>
```

> watchEffect没有具体监听哪一个值的变化，只要内部有某一个状态发生改变就会执行

#### watch()

侦听一个或多个响应式数据源，并在数据源变化时调用所给的回调函数。

- `watch()` 默认是懒侦听的，即仅在侦听源发生变化时才执行回调函数。

  第一个参数是侦听器的**源**。这个来源可以是以下几种：

  - 一个函数，返回一个值
  - 一个 ref
  - 一个响应式对象
  - ...或是由以上类型的值组成的数组

  第二个参数是在发生变化时要调用的回调函数。这个回调函数接受三个参数：新值、旧值，以及一个用于注册副作用清理的回调函数。该回调函数会在副作用下一次重新执行前调用，可以用来清除无效的副作用，例如等待中的异步请求。

  当侦听多个来源时，回调函数接受两个数组，分别对应来源数组中的新值和旧值。

  第三个可选的参数是一个对象，支持以下这些选项：

  - **`immediate`**：在侦听器创建时立即触发回调。第一次调用时旧值是 `undefined`。
  - **`deep`**：如果源是对象，强制深度遍历，以便在深层级变更时触发回调。参考[深层侦听器](https://cn.vuejs.org/guide/essentials/watchers.html#deep-watchers)。

  与 [`watchEffect()`](https://cn.vuejs.org/api/reactivity-core.html#watcheffect) 相比，`watch()` 使我们可以：

  - 懒执行副作用；
  - 更加明确是应该由哪个状态触发侦听器重新执行；
  - 可以访问所侦听状态的前一个值和当前值。

- **示例**

  侦听一个 getter 函数：

  ```
  const state = reactive({ count: 0 })
  watch(
    () => state.count,
    (count, prevCount) => {
      /* ... */
    }
  )
  ```

  侦听一个 ref：

  ```
  const count = ref(0)
  watch(count, (count, prevCount) => {
    /* ... */
  })
  ```

  当侦听多个来源时，回调函数接受两个数组，分别对应来源数组中的新值和旧值：

  ```
  watch([fooRef, barRef], ([foo, bar], [prevFoo, prevBar]) => {
    /* ... */
  })
  ```

  当使用 getter 函数作为源时，回调只在此函数的返回值变化时才会触发。如果你想让回调在深层级变更时也能触发，你需要使用 `{ deep: true }` 强制侦听器进入深层级模式。在深层级模式时，如果回调函数由于深层级的变更而被触发，那么新值和旧值将是同一个对象。

  ```
  const state = reactive({ count: 0 })
  watch(
    () => state,
    (newValue, oldValue) => {
      // newValue === oldValue
    },
    { deep: true }
  )
  ```

  当直接侦听一个响应式对象时，侦听器会自动启用深层模式：

  ```
  const state = reactive({ count: 0 })
  watch(state, () => {
    /* 深层级变更状态所触发的回调 */
  })
  ```

`composition_watch.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>composition_watch</title>
</head>
<body>
  <div id="app">
    <button @click="increment">点击了{{ count }}次</button>
    <button @click="foo='foo!!!'">改变foo</button>
    <button @click="bar='bar!!!'">改变bar</button>
    <button @click="state.obj.a=100">改变state</button>{{ state.obj.a }}

  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp, ref, watch, reactive } = Vue

  const app = createApp({
    setup () {
      const count = ref(0)
      const increment = () => {
        count.value += 1
      }
      // 函数作为监听源 --- 要的是那个数据 -- 需要value
      // watch(()=>count.value, (val, oldVal) => {
      //   console.log('fn', val, oldVal)
      // })

      // 侦听ref 不要写value
      // watch(count, (val, oldVal) => {
      //   console.log('ref', val, oldVal)
      // })

      // 侦听多个来源
      const foo = ref('foo')
      const bar = ref('bar')
      // watch([foo, bar], ([foo, bar], [oldFoo, oldBar]) => {
      //   console.log('f', foo, oldFoo)
      //   console.log('b', bar, oldBar)
      // })

      // 侦听源为函数，不会开启深度侦听
      const state = reactive({ obj: { a: 10 } })
  
      // 侦听源为函数,监听具体某个数据的变化
      // watch(()=>state.obj.a,(val,oldVal)=>{
      //   console.log(val,oldVal)
      // },{immediate:true})


      // 直接侦听一个响应式对象时,自动开启深度侦听
      // watch(state, (val, oldVal) => {
      //   console.log('auto', val, oldVal)
      // }, {
      //   immediate: true // 此处不需要写 deep: true
      // } )

      // 无法深度侦听
      // watch(() => state, (val, oldVal) => {
      //   console.log('s', val, oldVal)
      // } )
      // watch(() => state, (val, oldVal) => {
      //   console.log('d', val, oldVal)
      // }, {
      //   deep: true,
      //   immediate: true
      // } )
      return {
        count,
        increment,
        foo,
        bar,
        state
      }

    }
  })

  app.mount('#app')
</script>
</html>
```



### 18.4、工具函数

#### toRef()

基于响应式对象上的一个属性，创建一个对应的 ref。这样创建的 ref 与其源属性保持同步：改变源属性的值将更新 ref 的值，反之亦然。

`composition_toRef.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>composition_toRef</title>
</head>
<body>
  <div id="app">
    
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp, ref, toRef, reactive } = Vue

  const app = createApp({
    setup () {
      // 基于响应式对象上的一个属性，创建一个对应的 ref。
      // 这样创建的 ref 与其源属性保持同步：改变源属性的值将更新 ref 的值，反之亦然。
      const state = reactive({
        foo: 1,
        bar: 2
      })

      const count = toRef(state, 'foo')

      console.log(count.value) // 1

      count.value++
      console.log(state.foo) // 2
      console.log(count.value) // 2

      state.foo++
      console.log(state.foo) // 3
      console.log(count.value) // 3
    }
  })

  app.mount('#app')
</script>
</html>
```

#### toRefs()

将一个响应式对象转换为一个普通对象，这个普通对象的每个属性都是指向源对象相应属性的 ref。每个单独的 ref 都是使用 [`toRef()`](https://cn.vuejs.org/api/reactivity-utilities.html#toref) 创建的。

`composition_toRefs.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>composition_toRefs</title>
</head>
<body>
  <div id="app">
    
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp, ref, toRefs, reactive } = Vue

  const app = createApp({
    setup () {
      // 基于响应式对象上的一个属性，创建一个对应的 ref。
      // 这样创建的 ref 与其源属性保持同步：改变源属性的值将更新 ref 的值，反之亦然。
      const state = reactive({
        foo: 1,
        bar: 2
      })

      const newState = toRefs(state)

      console.log(newState.foo.value) // 1

      newState.foo.value ++

      console.log(newState.foo.value) // 2
      console.log(state.foo) // 2

      state.foo++
      console.log(newState.foo.value) // 3
      console.log(state.foo) // 3
    }
  })

  app.mount('#app')
</script>
</html>
```



> `toRefs` 在调用时只会为源对象上可以枚举的属性创建 ref。如果要为可能还不存在的属性创建 ref，请改用 [`toRef`](https://cn.vuejs.org/api/reactivity-utilities.html#toref)。



### 18.5、生命周期钩子

#### onBeforeMount()

注册一个钩子，在组件被挂载之前被调用。

当这个钩子被调用时，组件已经完成了其响应式状态的设置，但还没有创建 DOM 节点。它即将首次执行 DOM 渲染过程。

#### onMounted()

注册一个回调函数，在组件挂载完成后执行。

#### onBeforeUpdate()

注册一个钩子，在组件即将因为响应式状态变更而更新其 DOM 树之前调用。

这个钩子可以用来在 Vue 更新 DOM 之前访问 DOM 状态。在这个钩子中更改状态也是安全的。

#### onUpdated()

注册一个回调函数，在组件因为响应式状态变更而更新其 DOM 树之后调用。

父组件的更新钩子将在其子组件的更新钩子之后调用。

这个钩子会在组件的任意 DOM 更新后被调用，这些更新可能是由不同的状态变更导致的。如果你需要在某个特定的状态更改后访问更新后的 DOM，请使用 [nextTick()](https://cn.vuejs.org/api/general.html#nexttick) 作为替代。

#### onBeforeUnmount()

注册一个钩子，在组件实例被卸载之前调用。

当这个钩子被调用时，组件实例依然还保有全部的功能。

#### onUnmounted()

注册一个回调函数，在组件实例被卸载之后调用。

一个组件在以下情况下被视为已卸载：

- 其所有子组件都已经被卸载。
- 所有相关的响应式作用 (渲染作用以及 `setup()` 时创建的计算属性和侦听器) 都已经停止。

可以在这个钩子中手动清理一些副作用，例如计时器、DOM 事件监听器或者与服务器的连接。



`composition_lifeCycle.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>composition_lifeCycle</title>
</head>
<body>
  <div id="app">
    {{ count }}
    <button @click="add">加1</button>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { 
    createApp, 
    ref,
    onBeforeMount,
    onMounted,
    onBeforeUpdate,
    onUpdated,
    onBeforeUnmount,
    onUnmounted
  } = Vue
  
  const app = createApp({
    setup () {
      const count = ref(0)
      const add = () => {
        count.value += 1
        if (count.value === 5) {
          app.unmount()
        }
      }
      onBeforeMount(() => {
        console.log('onBeforeMount')
      })
      onMounted(() => {
        // DOM操作、数据请求、实例化、计时器、延时器、订阅数据
        console.log('onMounted')
      })
      onBeforeUpdate(() => {
        console.log('onBeforeUpdate')
      })
      onUpdated(() => {
        console.log('onUpdated')
      })
      onBeforeUnmount(() => {
        // 取消订阅，清除计时器、延时器等
        console.log('onBeforeUnmount')
      })
      onUnmounted(() => {
        console.log('onUnmounted')
      })

      return {
        count,
        add
      }
    }
  })
  
  app.mount('#app')
</script>
</html>
```



### 18.6、依赖注入

#### provide()

提供一个值，可以被后代组件注入。

`provide()` 接受两个参数：第一个参数是要注入的 key，可以是一个字符串或者一个 symbol，第二个参数是要注入的值。

#### inject()

默认情况下，`inject` 假设传入的注入名会被某个祖先链上的组件提供。如果该注入名的确没有任何组件提供，则会抛出一个运行时警告。

如果在注入一个值时不要求必须有提供者，那么我们应该声明一个默认值，和 props 类似

`composition_provide_inject.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>composition_provide_inject</title>
</head>
<body>
  <div id="app">
    <my-parent></my-parent>
  </div>
</body>
<template id="parent">
  <div>
    我是父组件 - {{ count }}
    <my-child></my-child>
  </div>
</template>
<template id="child">
  <div>
    我是子组件 <button @click="add">加10</button> {{ test }}
  </div>
</template>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp, ref, provide, inject } = Vue
  const Child = {
    template: '#child',
    setup () {
      // 注入值的默认方式
      const add = inject('add')
      // 设置注入的默认值
      const test = inject('test', '测试')
      return {
        add,
        test
      }
    }
  }
  const Parent = {
    template: '#parent',
    components: {
      myChild: Child
    },
    setup () {
      const count = inject('count')
      return {
        count
      }
    }
  }
  const app = createApp({
    components: {
      myParent: Parent
    },
    setup () {
      const count = ref(10)
      const add = () => {
        count.value += 10
      }
      // 提供值，可以是数据，也可以是函数
      provide('count', count)
      provide('add', add)
    }
  })

  app.mount('#app')
</script>
</html>
```



### 18.7、组合式函数

#### 什么是“组合式函数”？

在 Vue 应用的概念中，“组合式函数”(Composables) 是一个利用 Vue 的组合式 API 来封装和复用**有状态逻辑**的函数。

> 也可以叫做自定义hooks

当构建前端应用时，我们常常需要复用公共业务的逻辑。一个简单的例子是跟踪当前鼠标在页面中的位置。在实际应用中，也可能是像触摸手势或与数据库的连接状态这样的更复杂的逻辑。

如果我们要直接在组件中使用组合式 API 实现鼠标跟踪功能，它会是这样的

`composition_mouse.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>composition_mouse</title>
</head>
<body>
  <div id="app">
    鼠标的位置为：({{ x }}, {{ y }})
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp, ref, onMounted, onUnmounted } = Vue
  const app = createApp({
    setup () {
      const x = ref(0)
      const y = ref(0)
      function updatePosition (event) {
        x.value = event.pageX
        y.value = event.pageY
      }
      onMounted(() => {
        window.addEventListener('mousemove', updatePosition)
      }) 
      onUnmounted(() => {
        window.removeEventListener('mousemove', updatePosition)
      })
      return {
        x, y
      }
    }
  })

  app.mount('#app')
</script>
</html>
```

> 但是，如果我们想在多个组件中复用这个相同的逻辑呢？我们可以把这个逻辑以一个组合式函数的形式提取到外部文件中

#### 如何定义和使用组合式函数

`composition_mouse_hooks.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>composition_mouse_hooks</title>
</head>
<body>
  <div id="app">
    鼠标的位置为：({{ x }}, {{ y }})
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp, ref, onMounted, onUnmounted } = Vue
  function useMouse () {
    const x = ref(0)
    const y = ref(0)
    function updatePosition (event) {
      x.value = event.pageX
      y.value = event.pageY
    }
    onMounted(() => {
      window.addEventListener('mousemove', updatePosition)
    }) 
    onUnmounted(() => {
      window.removeEventListener('mousemove', updatePosition)
    })
    return { x, y }
  }
    
  const app = createApp({
    setup () {
      const { x, y } = useMouse()
      return {
        x, y
      }
    }
  })

  app.mount('#app')
</script>
</html>
```

如你所见，核心逻辑完全一致，我们做的只是把它移到一个外部函数中去，并返回需要暴露的状态。和在组件中一样，你也可以在组合式函数中使用所有的[组合式 API](https://cn.vuejs.org/api/#composition-api)。现在，`useMouse()` 的功能可以在任何组件中轻易复用了。

更酷的是，你还可以嵌套多个组合式函数：**一个组合式函数可以调用一个或多个其他的组合式函数**。

`composition_mouse_more_hooks.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>composition_mouse_more_hooks</title>
</head>
<body>
  <div id="app">
    鼠标的位置为：({{ x }}, {{ y }})
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp, ref, onMounted, onUnmounted } = Vue
  function useEventListener (target, event, callback) {
    onMounted(() => {
      target.addEventListener(event, callback)
    }) 
    onUnmounted(() => {
      target.removeEventListener(event, callback)
    })
  }

  function useMouse () {
    const x = ref(0)
    const y = ref(0)
    // function updatePosition (event) {
    //   x.value = event.pageX
    //   y.value = event.pageY
    // }
    // 调用另外一个带三个参数的组合式函数useEventListener
    useEventListener(window, 'mousemove', (event) => {
      x.value = event.pageX
      y.value = event.pageY
    })
    return { x, y }
  }
  const app = createApp({
    setup () {
      const { x, y } = useMouse()
      return {
        x, y
      }
    }
  })

  app.mount('#app')
</script>
</html>
```

#### 异步状态

在做异步数据请求时，我们常常需要处理不同的状态：加载中、加载成功和加载失败。

`composition_async.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>composition_async</title>
</head>
<body>
  <div id="app">
    <div v-if="error">{{ error }}</div>
    <div v-else-if="data">
      <ul>
        <li v-for="item of data" :key="item.proid">{{ item.proname }}</li>
      </ul>
    </div>
    <div v-else>加载中....</div>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp, ref, onMounted } = Vue

  const app = createApp({
    setup () { 
      const data = ref(null)
      const error = ref(null)
      // 接口文档 http://121.89.205.189:3001/apidoc/#api-Pro-GetProList
      fetch('http://121.89.205.189:3001/api/pro/list')
        .then(res => res.json())
        .then(res => {
          console.log(res)
          data.value = res.data
        }).catch(err => {
          error.value = err
        })
      return {
        data,
        error
      }
    }
  })

  app.mount('#app')
</script>
</html>
```

如果在每个需要获取数据的组件中都要重复这种模式，那就太繁琐了。让我们把它抽取成一个组合式函数：

`composition_async_hooks.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>composition_async</title>
</head>
<body>
  <div id="app">
    <div v-if="error">{{ error }}</div>
    <div v-else-if="data">
      <ul>
        <li v-for="item of data" :key="item.proid">{{ item.proname }}</li>
      </ul>
    </div>
    <div v-else>加载中....</div>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp, ref, onMounted } = Vue
  function useFetch(url) {
    const data = ref(null)
    const error = ref(null)
    fetch(url)
      .then((res) => res.json())
      .then((res) => (data.value = res.data))
      .catch((err) => (error.value = err))
    return { data, error }
  }
  const app = createApp({
    setup () { 
      const {data,error} = useFetch('http://121.89.205.189:3001/api/pro/list')
      return {
        data,
        error
      }
    }
  })

  app.mount('#app')
</script>
</html>
```

`useFetch()` 接收一个静态的 URL 字符串作为输入，所以它只执行一次请求，然后就完成了。但如果我们想让它在每次 URL 变化时都重新请求呢？那我们可以让它同时允许接收 ref 作为参数：

`composition_async_hooks_urls.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>composition_async_hooks</title>
</head>
<body>
  <div id="app">
    <button @click="type='list'">获取产品列表数据</button>
    <button @click="type='recommendlist'">获取推荐列表数据</button>
    <div v-if="error">{{ error }}</div>
    <div v-else-if="data">
      <ul>
        <li v-for="item of data" :key="item.proid">{{ item.proname }}</li>
      </ul>
    </div>
    <div v-else>加载中....</div>
  </div>
</body>
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
  const { createApp, ref, computed, unref, isRef, watchEffect } = Vue
  function useFetch (url) {
    const data = ref(null)
    const error = ref(null)
    // 接口文档 http://121.89.205.189:3001/apidoc/#api-Pro-GetProList
    function doFetch () {
      // 初始化数据
      data.value = null
      error.value = null
      // unref() 解包可能为 ref 的值  unref(ref('xx')) ==> 'xx'
      fetch(unref(url))
        .then(res => res.json())
        .then(res => {
          data.value = res.data
        }).catch(err => {
          error.value = err
        })
    }
    if (isRef(url)) {
      // 若输入的 URL 是一个 ref，那么启动一个响应式的请求
      watchEffect(doFetch)
    } else {
      // 否则只请求一次
      // 避免监听器的额外开销
      doFetch()
    }
    return { data, error }
  }
  const app = createApp({
    setup () { 
      const type = ref('list')
      const url = computed(()=>'http://121.89.205.189:3001/api/pro/'+ type.value)
      const { data, error } = useFetch(url)
      return {
        data,
        error,
        type
      }
    }
  })

  app.mount('#app')
</script>
</html>
```