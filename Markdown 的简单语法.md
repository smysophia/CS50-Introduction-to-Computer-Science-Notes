# Markdown 的简单语法
请点开编辑(<>Edit file)以后查看每个功能是怎么实现的

## 字体格式
字体格式**两个星星是加粗**，或者 __两个下滑线也是加粗__ 加入`<br>`或者两个空格换行 <br>
还有*一个星星是斜体*， 或者 _一个下划线也是斜体_  
加两个波浪就是删除线，~~删除掉这句话~~  
\- \[ \] 不打勾  注意减号后的空格 方括号后面的空格
- [ ] 不打勾  
- [X] 打钩
  - [X] 嵌套一个
 
## 标题
大标题下面打一排等号，等号没有长度限制
====
然后写第二个标题，下面打一排减号
---------------
减号也没有长度限制  
 <br>
## 引用
> 这样就可以引用啦  
换行不加也会继续引用
>记得打空格啊，不打不行哦

空一行退出引用
 <br>
## 列表
* 星星变成原点
  * 按4个空格然后嵌套一个
    * 再嵌套一个
+ 加号也变成原点
- 还有减号
*不打空格是不行的
1. 一号
2. 二号
4. 这个是有序列表哦，写4也会变成3的
4. 如果行首想输入数字加点，可以用数字\点来取消列表 

## 代码  
在一行中引入代码用一个反引号`<title>Markdown</title>` 这样。或者使用一个缩进来插入块代码

    if (isAwesome){

        return true

    }
  
代码块前后需要有至少一个空行，且每行代码前需要有至少一个 Tab 或四个空格  
还是用三个反引号比较方便
```
if (isAwesome){
return true
}
```
有没有缩进都无所谓，要高亮就在第一个反引号后面打上要用的语言
```javascript
 if (isAwesome){

      return true

    }
```
就可以了。
 <br>
 ## 分割线
 可以插入星星，减号-和下划线_
 *********
 几个都行
 ----------
 有空格也行
 _ _ _ _ _ _ _ _ _ _

## 超链接
 格式为`[link text](URL 'title text')`  
 [google](http://www.google.com/ "Google")  
 或者使用识别符link（也可为空，直接使用Google）  
 [Google][link]
 
[link]: http://www.google.com/ "Google"
好处是可以多处引用这个url  
比如这样：[link]  
 或者直接放url也行   
<http://www.google.com/>

 
 ## 图片
 ![GitHub](https://avatars2.githubusercontent.com/u/3265208?v=3&s=100 "GitHub,Social Coding")
或者
![GitHub][github]

[github]: https://avatars2.githubusercontent.com/u/3265208?v=3&s=100 "GitHub,Social Coding"

Markdown 不支持指定图片的显示大小，不过可以通过直接插入<img />标签来指定相关属性：  
<img src="https://avatars2.githubusercontent.com/u/3265208?v=3&s=100" alt="GitHub" title="GitHub,Social Coding" width="50" height="50" />

## 表格
Name | Age
----- | -----
张三 | 23
李四 | 43

