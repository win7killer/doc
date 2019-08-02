## Array && Set && WeakSet

### Array
#### 属性
- length
- prototype
#### 方法
- from
- isArray
- of
- prototype[fn]
  - concat： 合并
  - copyWithin

  - fill：填充？

###### 遍历
  - every：判断每一个元素 相当于 &&。 区分 some
  - filter：过滤
  - forEach：常规遍历 Array.forEach((item, index, arr) => {}, thisArg) // this 会指向 thisArg. return undefined
  - map: 返回一个新数组，每个元素为 cb 函数的返回值, 区分 forEach
  - flatMap：和 map 方法区分。
##### 查找
  - find：查询，[].find(value) => someValue，注意和 indexOf/findIndex 区分
  - findIndex：查询，[].findIndex(value) => index indexOf/find 区分
  - includes: (value, startIndex) => true / false
  - indexOf: (value) => index
  - lastIndexOf： 返回数组中最后一项 value 的 index。 [1,2,3,1].indexOf(1) // 0;  [1,2,3,1].lastIndexOf(1) // 3;
###### 迭代器
- keys：key 组成的可遍历对象，用于 for of 遍历
- values：// 返回一个由 value 组成的可遍历对象，用于 for of 遍历
  - arr[Symbol.iterator]： for of 循环使用，和 values 返回的相同
  - entries： [[value, value], [value, value]] 可遍历对象，用于 for of 遍历

###### 增删元素
- pop: 尾部弹出一个元素，影响原 array
- push: 数组中从后假如 n 个 元素
- shift
- unshift： 从前加入多个元素
- splice： (start, [deleCount, [item, [item1]]]) // 删除或者替换或者增加，返回 delete 的元素，操作原数组



##### 其他
- flat: 数字扁平化，不太兼容【扁平化还可以用 toString/join  然后 split。需要注意元素类型】
- reduce： 数组的每一项处理，返回累计处理的值。 fb = (count, item, index, array) => count
- reduceRight: 同上，但是从右侧开始
- some: // 类似于 filter，有一个满足即可，相当于 ||
- sort： 排序

- join: 数组到字符串，不传参数的时候，和 toString 一个效果
- reverse： 倒序数组
- slice： (begin, end) => [] // 不修改原数组

- toLocalString
- toSource
- toString



### Set
#### 属性
- size: 对应数组的 length
#### 方法
- prototype
  - add: 增加1个元素，返回 原 set
  - delete: 删除一个元素，返回是否成功
  - clear: 清空 set 所有元素
  - entries: 返回迭代器，[value, value]
  - forEach: (item, index. set) => undefined
  - has: 返回是否包含 value
  - values: set迭代器
  - keys: 同上，无差异
  - [@@iterator](): 直接迭代。

### WeakSet
> 弱 set，顾名思义，没有 set 强大。元素只能是 对象 object，不能使原始值
#### 方法
- prototype
  - add: 添加一个对象类型的元素，必须是对象
  - delete: 方法从 WeakSet 对象中移除指定的元素
  - has: 是否包含某个独享元素


### 对比
| 对照           | Array                                        | Set       | WeakSet   |
| -------------- | -------------------------------------------- | --------- | --------- |
| 长度           | length                                       | size      | -         |
| 增加元素       | push、unshift、赋值                          | add       | add       |
| 删除元素       | pop、shift、splice、改变 length              | delete    | delete    |
| 清空           | length = 0、splice                           | clear     | -         |
| 元素类型       | all                                          | all       | object    |
| 获取迭代器     | keys/values/entries/直接for of               | ext: next | ext: next |
| 遍历方法       | forEach/map/                                      | forEach   | -         |
| 是否有某个元素 | includes/indexOf/lastIndexOf/find/findIndex/ | has       | has       |
|其他|filter/some/every/reduce/reduceRight/flat/join/reverse/slice|-|-|


### 未完待续

### 相关知识点
- 迭代器
- Map
- Object
- WeakMap




