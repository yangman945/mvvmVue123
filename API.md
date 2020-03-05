

### [Object.defineProperty()](https://www.jianshu.com/p/8fe1382ba135)

**object.defineProperty()，该方法是直接在一个对象上定义新的属性，或是修改已经存在的属性**

语法：`Object.defineProperty(obj, prop, desc`

- obj：需要定义属性的对象
- prop：当前需要定义的属性名称
- desc：属性描述符

------

属性描述符：`通过Object.defineProperty()为对象定义属性，有两种形式，且不能混合使用` 

- （1）数据描述符：特有的两个属性（value,writable） 

```js
let Person = {}
Object.defineProperty(Person, 'name', {
   value: 'jack', // 该属性的值
   writable: true // 是否允许修改该属性
})
```

- （2）存取描述符：是由一对 getter、setter 函数功能来描述的属性 

```js
let Person = {}
let temp = null
Object.defineProperty(Person, 'name', {
  get: function () {
    return temp
  }, //一个给属性提供getter的方法，该方法返回值被用作属性值。默认为undefined
  set: function (val) {
    temp = val
  } //一个给属性提供setter的方法，该方法将接受唯一参数，并将该参数的新值分配给该属性。默认值为undefined
})
```



**数据描述符和存取描述均具有以下描述符**

1. configrable 描述属性是否配置，以及可否删除；

   configurable: false 时，不能删除当前属性，且不能重新配置当前属性的描述符(有一个小小的意外：可以把writable的状态由true改为false,但是无法由false改为true),但是在writable: true的情况下，可以改变value的值

   configurable: true时，可以删除当前属性，可以配置当前属性所有描述符。

2. enumerable 描述属性是否会出现在for in 或者 Object.keys()的遍历中；



![](.\images\obj1.png)







