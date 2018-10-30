## CSS(3)

- [渐进增强和优雅降级](#渐进增强和优雅降级)
- [CSS选择器及优先级及权重](#CSS选择器及优先级及权重)
- [水平垂直居中](#水平垂直居中)


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

    关联点： 浮动及清除、定位（相对定位、绝对定位等）、盒模型
</span>