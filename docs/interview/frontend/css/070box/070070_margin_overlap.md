---
contributors: 'isboyjc'
---

# margin 重叠问题?

问题描述：

两个块级元素的上外边距和下外边距可能会合并（折叠）为一个外边距，其大小会取其中外边距值大的那个，这种行为就是外边距折叠。需要注意的是，浮动的元素和绝对定位这种脱离文档流的元素的外边距不会折叠。重叠只会出现在垂直方向。


计算原则：

折叠合并后外边距的计算原则如下：

- 如果两者都是正数，那么就去最大者
- 如果是一正一负，就会正值减去负值的绝对值
- 两个都是负值时，用0减去两个中绝对值大的那个


解决办法：

对于折叠的情况，主要有两种：兄弟之间重叠和父子之间重叠

- 兄弟之间重叠
  - 底部元素变为行内盒子：display: inline-block
  - 底部元素设置浮动：float
  - 底部元素的position的值为absolute/fixed

- 父子之间重叠
  - 父元素加入：overflow: hidden
  - 父元素添加透明边框：border:1px solid transparent
  - 子元素变为行内盒子：display: inline-block
  - 子元素加入浮动属性或定位