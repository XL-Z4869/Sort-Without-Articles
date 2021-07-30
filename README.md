# Sort-Without-Articles
https://xl-z4869.github.io/Sort-Without-Articles/
初始文件提供了一串无序列表元素，需要去除以a，an，the开头的元素后进行排序，并将排序后的效果以列表形式显示在页面中
### 一、知识点
#### 1.正则表达式
去除以a，an，the开头的元素可以用正则表达式进行筛选，之后可以用replace进行替换筛选
```
//^表示开头，i表示筛选全部内容

item.replace(/^(a|an|the)/i,'')
```
#### 2.Array.sort()对数组进行排序
```
arr.sort((a,b)=>a>b?1:-1)
```
### 二、主要步骤
#### 1.定义函数，用来对数组元素进行筛选
```
function strip(bandName) {
    return bandName.replace(/^(a|the|an)/i, '').trim()
}
```
#### 2.使用Array.sort()对数组进行排序
```
const newBands = bands.sort((a, b) => strip(a) > strip(b) ? 1 : -1)
```
#### 3.获取ul元素，并补充li内容
```
const ul = document.querySelector('#bands')
   
ul.innerHTML = newBands.map(band =>
    `<li>${band}</li>`
).join('')
```
