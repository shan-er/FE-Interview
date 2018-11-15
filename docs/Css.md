## CSS(3)

- [渐进增强和优雅降级](#渐进增强和优雅降级)
- [CSS选择器及优先级及权重](#CSS选择器及优先级及权重)
- [水平垂直居中](#水平垂直居中)
- [常见兼容性问题](#常见兼容性问题)
- [position的值relative和absolute定位原点是](#position的值relative和absolute定位原点是)
- [css定义的权重](#css定义的权重)
- [请解释一下为什么会出现浮动和什么时候需要清除浮动？清除浮动的方式](#请解释一下为什么会出现浮动和什么时候需要清除浮动？清除浮动的方式)


### 渐进增强和优雅降级

渐进增强（Progressive Enhancement）：一开始就针对低版本浏览器进行构建页面，完成基本的功能，然后再针对高级浏览器进行效果、交互、追加功能达到更好的体验。

优雅降级（Graceful Degradation）：一开始就构建站点的完整功能，然后针对浏览器兼容。

<span style="color: grey">

    关联点： CSS hack（原理：利用不同浏览器对CSS的支持和解析结果不一样编写针对特定浏览器样式。）
</span>


### 水平垂直居中
文章原文及DEMO实现： [CSS实现水平垂直居中](https://blog.csdn.net/Scarlett_Dream/article/details/83416029)

#### 1. 水平居中
1. 元素为行内元素，设置父元素 ```text-align:center```;
2. 如果水平居中元素为块级固定，则需设置```margin: 0 auto```;(IE6下需在父元素上设置text-align: center;,再给子元素恢复需要的值)
3. 如果元素为绝对定位，法一：设置父元素position为relative，元素设left:0;right:0;margin:auto;
法二：设置父元素position为relative，负值的margin-left, 设置子元素;
4. 如果元素为浮动，该元素设置```position: relative```， 并且浮动方向偏移量（left或者right）设置为50%，浮动方向上的margin设置为元素宽度一半乘以-1;
5. 使用flex-box布局，父元素指定justify-content属性为center;

#### 2. 垂直居中
1. 若元素为单行：可设置line-height;
2. 若元素是行内块级元素,display: inline-block, vertical-align: middle和一个伪元素让内容块处于容器中央(注：该方法指针对不折行的子元素)。
3. 将显示方式设置为表格，display:table-cell,同时设置vertial-align：middle;
4. 使用flex布局，设置为align-item：center;
5. 如果元素为绝对定位，法一：子元素中设置bottom:0,top:0,并设置margin:auto;
法二：子元素设置top:50%，margin-top值为高度一半的负值;

<span style="color: grey">

    关联点： 浮动及清除、定位（相对定位、绝对定位等）、盒模型、行內元素与块级元素
</span>

### 常见兼容性问题
1. png24位的图片在IE6浏览器上出现背景；

    解决方案是：做成PNG8；

2. 浏览器默认的 margin 和 padding 不同。
    
    解决方案是：加一个全局的*{margin:0;padding:0;}来统一。

3. IE6双边距bug：块属性标签float后，又有横行的 margin 情况下，在 IE6 显示 margin 比设置的大。浮动IE产生的双倍距离 #box{float:left;width:10px;margin:0 0 0 100px;} 这种情况下IE6会产生200px的距离。
    
    解决方法：加上_display：inline，使浮动忽略

4. IE下，可以使用获取常规属性的方法来获取自定义属性，也可以使用getAttribute()获取自定义属性； Firefox下，只能使用getAttribute()获取自定义属性。
    
    解决方法：统一通过getAttribute()获取自定义属性。

5. IE下，even对象有x，y属性，但是没有pageX，pageY属性，但是没有x，y属性；
    
    解决方法：（条件注释）缺点是在IE浏览器下可能会增加额外的HTTP请求数。

6. Chrome中文界面下默认会将小于 12px 的文本强制按照 12px 显示
    
    解决方法：可通过加入 CSS 属性 -webkt-text-size-adjust:none;解决

7. 超链接访问过后 hover 样式就不出现了，被点击访问过的超链接样式不在具有 hover 和 active ；
    
    解决方法：改变CSS属性的排列顺序：L-V-H-A: a:link{ }  a:visited{ } a:hover{ } a:active{ } 


### position的值relative和absolute定位原点是
##### absolute
生成绝对定位的元素，相对于值不为 static的第一个父元素进行定位。
##### fixed （老IE不支持）
生成绝对定位的元素，相对于浏览器窗口进行定位。
##### relative
生成相对定位的元素，相对于其正常位置进行定位。
##### static
默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right z-index 声明）。
##### inherit
规定从父元素继承 position 属性的值。

### css定义的权重
以下是权重的规则：标签的权重为1，class的权重为10，id的权重为100，以下例子是演示各种定义的权重值：
```
/*权重为1*/
div{
}
/*权重为10*/
.class1{
}
/*权重为100*/
#id1{
}
/*权重为100+1=101*/
#id1 div{
}
/*权重为10+1=11*/
.class1 div{
}
/*权重为10+10+1=21*/
.class1 .class2 div{
}
```
如果权重相同，则最后定义的样式会起作用，但是应该避免这种情况出现

### 请解释一下为什么会出现浮动和什么时候需要清除浮动？清除浮动的方式
