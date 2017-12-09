## js加载的几个方法

1. window.onload= function(){}
2. `<script src="" async>`
3. `<script src="" defer>`

## BOM

- history  =>  (浏览器的浏览记录)
  - go()   前进或后退具体的值
  - forward()  前进
  - back()  后退
- location
  - hash
  - host
  - hostname
  - href     decodeURIComponent

## String

- localeCompare  => 比较字符的顺序
  - 'a'.localeCompare("b")    前面返回-1 , 后面返回1
- includes('a',index)  =>  判断字符串中是否有指定字符  返回值是true或者false  第二个参数是查找的起始位置
- repeat(index)   =>  将字符串重复几次
- startsWith('xx',index)  =>  第二个参数表示开始查找的索引
- endsWith
- padStart(hopeLength, 'str')   =>  第一个参数得到新字符串的长度,第二个参数从字符串中去除字符充填到新字符串的前面   `str.padStart(8,'aaa')`   充填的长度是期望的长度  -  调用字符串的长度
- padEnd(hopeLength,'str')

```javascript
Object.getOwnPropertyDescriptor(obj,attr);   // 检测对象某个属性的具体参数
```

## Array

- Array.of()
- Array.from()   =>  可以传数组或者类数组  ,  返回值是一个数组  =>  将类数组转数组或者复制数组
- Array.isArray()
- fill('str',n,m)  => 方法用一个固定值填充一个数组中从起始索引到终止索引内的全部元素。

`Array(7).fill(1)`    =>   得到一个有7个1的数组

数组的空位 =>  ES6 是 处理为undefined  ES5之前是略过  包括迭代方法都是如此ES5的会直接跳过空位的

- find

- copyWithin(target,start,end)   =>  截取start-end 然后从target位置开始覆盖  , 数组的长度也是不变的

- valueof()  当前的数组

- find()   回调函数函数的return的值为true 则停止查找返回当前项  返回 undefined

  - ```javascript
    find((item,index,arr)=>{
      //  回调函数函数的return的值为true 则停止查找返回当前项
      return typeof item == 'object';
    })
    ```

- findIndex()  回调函数函数的return的值为true 则停止查找返回当前项对应的索引  或者-1

- every((item,index,arr)=>{})   里面的回调函数都返回true的 返回值就是true 否则false

- some()   里面的回调函数只要有返回true的 返回值就是true  否则false

- reduce((prev,cur,index,arr)=>{},10)  =>   prev上一个函数的返回值,cur当前项

  - prev第一次默认为0 , 可以设置默认值 10   返回值 函数累计处理的结果

- reduceRight((prev,cur,index,arr)=>{},10)

## for of

> 遍历的是数组和类数组中的值
>
> ary.entries()  => 将每一项的索引和值放到一个数组中  ary.keys() => 数组中的索引  ary.values() => 数组的值
>
> 可以使用解构赋值

```javascript
var arr = [1,2,3,4];
for(var item of arr.keys()){
  
}
```

## classList

> 是一个数组

```javascript
var box = document.getElemenyById('box');
console.log(box.classList);
```

- add(classname,classname)
- remove(classname)

## 对象的解构赋值

```javascript
let obj = {a:1,b:2};
let {a,b} = obj; // a=1,b=2
let {a:n,b:m} = obj;  // n=1,n=2
```

#### 对象数组的嵌套

- 如果对象里面嵌套对象外面对象的值为undefined则会报错
- 如果后面的不是对象会将其转换为对象 Object()  基础数据类型会将其转化为对应类的实例
- null 和 undefined是无法转为对象的,所以会报错   


## 字符串的解构赋值及新方法

> 字符串的解构赋值是将字符串转为类似数组的对象进行赋值,一一对应,字符串中还有length这个属性,可以对其进行解构赋值

```javascript
let str = '12345';
let [x,y,z] = str // x=1,y=2,z=3
let {length} = str // length = 5;
```

- includes()  =>  字符串中的方法不会修改原字符串的方法  判断原字符串中是否含有这个字符
- startsWith('',2)  =>  第二个参数开始查找的索引
- endsWith
- repeat()  将字符串重复几次,正数向下取整,负数/Infinity会报错    NaN 0次 其他类型现将其他类型转换为数字