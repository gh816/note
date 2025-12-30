# CSS面试题

## CSS-图文样式

### line-height如何继承

1.如果line-height的值是具体数值，如何20px，则直接继承。

2.如果line-height的值是比例，如2或者1.5等，则继承该比例，如下面代码。p标签的font-size: 24px;

![image-20240109232127570](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240109232127570.png)

3.如果line-height的值是百分比，如200%,则先计算再继承算出来的值。如下面代码，先计算20px*200%再继承给子元素

![image-20240109232540254](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240109232540254.png)

## CSS响应式

### rem是什么？

![image-20240110130406781](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240110130406781.png)

### 响应式布局的常用方案

媒体查询（Media Queries）：使用CSS的媒体查询功能，根据不同的屏幕宽度、设备类型等条件，应用不同的样式规则。通过定义不同的CSS规则集，可以使网页在不同的屏幕尺寸下呈现不同的布局效果。

## margin负值问题

![image-20240110160304496](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240110160304496.png)

## BFC理解与应用



内容塌陷：如果父元素当中有子元素且子元素浮动了，可能会产生高度坍塌
BFC是用于控制块级元素布局的渲染区域，这个区域有自己的渲染规则，内部元素的布局不会影响

![image-20240110163055633](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240110163055633.png)

## CSS-布局

### 盒模型宽度计算

![image-20240110164321084](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240110164321084.png)

offset = (内容宽度 + 内边距 + 边框)，无外边距

因此答案就是122px 

 补充：如果让offsetWidth等于100px，该如何做？

![image-20240111141900081](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240111141900081.png)

### margin纵向重叠问题

![image-20240111143258075](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240111143258075.png)

相邻元素点margin-top和margin-bottom会发生重叠

空白内容的<p></p>也会重叠

答案15px

### float布局

知道怎么排布双飞翼布局以及圣杯布局就行

### flex布局

![image-20240113140844035](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240113140844035.png)

1. flex-direction：决定主轴的方向，可取值为row（默认，水平方向）、row-reverse（水平方向逆序）、column（垂直方向）或column-reverse（垂直方向逆序）。
2. justify-content：决定主轴上元素的对齐方式，可取值为flex-start（起始位置对齐，默认）、flex-end（结束位置对齐）、center（居中对齐）、space-between（两端对齐，元素之间等距分布）或space-around（每个元素周围等距分布）。
3. align-items：决定交叉轴上元素的对齐方式，可取值为flex-start（起始位置对齐）、flex-end（结束位置对齐）、center（居中对齐）、baseline（基线对齐，默认）或stretch（拉伸填满交叉轴）。
4. flex-wrap：决定是否换行，可取值为nowrap（默认，不换行）、wrap（换行，第一行在上方）或wrap-reverse（换行，第一行在下方）。
5. align-content：决定多行元素在交叉轴上的对齐方式，可取值为flex-start（起始位置对齐）、flex-end（结束位置对齐）、center（居中对齐）、space-between（两端对齐，行之间等距分布）、space-around（每行周围等距分布）或stretch（拉伸填满交叉轴，默认）

6.align-self属性可以应用于flex容器的子元素，用于控制该子元素在交叉轴上的对齐方式，而不影响其他子元素的对齐方式。它可以取以下值：

- auto：继承父容器的align-items属性。
- flex-start：在交叉轴起始位置对齐。
- flex-end：在交叉轴结束位置对齐。
- center：在交叉轴居中对齐。
- baseline：以基线对齐。
- stretch：拉伸填满交叉轴。

## CSS-定位

absolute和relative分别依据什么定位？

![image-20240113142428981](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240113142428981.png)

![image-20240113142702634](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240113142702634.png)

居中对齐有哪些实现方式？

水平居中

![image-20240113143402990](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240113143402990.png)

垂直居中

![image-20240113143628945](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240113143628945.png)