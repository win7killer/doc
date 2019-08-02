## Object && Map && WeakMap

### Object
#### 属性

#### 方法
##### 工具方法
- assign: (target, [source1, [source2]]) 返回复制后的目标对象，浅拷贝
- create: (obj, propertiesObject),返回一个新对象subObj, subObj.__proto__ 指向 obj, 可用于继承
- defineProperties: 直接在一个对象上定义n个新属性或修改现有属性，并返回该对象。
```js
Object.defineProperties(obj, {
    a: {
        configurable, // 是否可配置？
        enumerable, // 是否可枚举
        value, // value 设置
        writable, // 是否可写
        get, // 读取拦截
        set, // 赋值拦截
    },
    b: {}
})
```
- defineProperty:   直接在一个对象上定义1个新属性或修改现有属性，并返回这个对象。
```js
Object.defineProperty(obj, key, {
    writeable: true,
    ...
})
```
- entries: 返回一个给定对象自身可枚举属性的键值对数组，其排列与使用 for...in 循环遍历该对象时返回的顺序一致（区别在于 for-in 循环也枚举原型链中的属性）# 返回数组，不是迭代器， => [[key, value]] 【区分 for in】
- keys:  => [key, key1]
- values: => [value, value1]
- freeze: 冻结对象，该对象一切都不可以操作。单不是 deep 的冻结，元素为 object 的话，子元素的属性可操作。
- <del>fromEntries 把键值对列表转换为一个对象</del> 【不兼容】
- is: (val1, val2) => Boolean,两个值是否相等。【区分 == && ===】不转换类型，可判断 NaN,可处理 +0 && -0
-
### Map


### WeakMap
