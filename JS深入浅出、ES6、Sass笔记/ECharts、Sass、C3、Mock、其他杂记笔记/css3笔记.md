<-------------------双伪元素清除浮动   （伪元素的本质是插入一个行内元素）----------------------------------->
.clearfix:before,.clearfix:after{
   content:"";
   display:table;
}
.clearfix:after{
  clear:both;
}`
.clearfix{
  *zoom:1;
<---------------解决图片底测缝隙的问题--------------------------------------->
给 img vertical-align:middle | top 让图片不要和基线对齐
vertical-align 属性设置一个元素的垂直对齐方式。

 <----------------css3背景 ------------------------------------------------------->
（一）background-clip 设置背景图像区域
border-box	背景覆盖到到边框盒
padding-box	背景覆盖到内边距框
content-box	背景覆盖到内容框

（二）background-origin 设置背景图片的定位（原点）
background-origin 指定 background-position 的属性应该相对于谁进行定位，设置的是元素背景图片的原始起始位置。
background-clip 是规定背景图可以绘制并显示的区域，background-origin 决定了背景图在哪绘制。
如果 background-origin 的范围大于 background-clip 的范围，那超出的部分则不显示。

（三）background-size 设置背景图片的大小
1. 一个值
一个百分比背景图根据当前元素的宽度设置的，高度自动
2. 两个值
背景图的宽根据当前元素的宽，高根据当前元素的高设置。
3.cover  ！！！！
将背景图像等比缩放到完全覆盖容器，背景图像有可能超出容器。
4. contain
将背景图像等比缩放到宽度或高度与容器的宽度或高度相等，背景图像始终被包含在容器内。

（四）background-image 可以为元素设置多个背景图
多重背景图像 允许为元素设置多个背景图像
background-image: url(),url();/*前面的在上面*/ ！！！！

（五）background-position 属性设置背景图像的起始位置。 （搭配精灵图！!!!!!!!  )
第一个值是水平位置，第二个值是垂直位置。如果您仅规定了一个关键词，那么第二个值将是"center"。

<-----------------------css3文字效果 ------------------------------------------------->
text-shadow: 水平位置 垂直位置 模糊距离 阴影颜色

<--------------------css3边框------------------------------------------------------>
border-radius: 左上角 右上角 右下角 左下角
box-shadow: 水平位置 垂直位置 模糊距离 阴影颜色  // 盒子阴影
border-image: 路径  铺 (repeated)、铺满 (rounded) 或拉伸 (stretched)。

<--------------------------css3过渡属性 --------------------------------------------->
transition: 要过渡的属性 (all) 花费时间 运动曲线 何时开始

【1】transition-property：
规定应用过渡效果的 CSS 属性的名称（当指定的 CSS 属性改变时，过渡效果开始），其默认值为 all 。

【2】transition-duration：
规定完成过渡效果需要的时间（单位为 s 或 ms），其默认值为 0s ，意味着如果不指定这个属性，将不会呈现过渡效果。

【3】transition-timing-function：
规定过渡效果的时间曲线。

默认 ease ：慢速开始，中间变快，慢速结束；相当于 cubic-bezier(0.25, 0.1, 0.25, 1)。

可选 liner：匀速运动；相当于 cubic-bezier(0, 0, 1, 1)。

可选 ease-in：慢速开始；相当于 cubic-bezier(0.42, 0, 1, 1)。

可选 ease-out：慢速结束；相当于 cubic-bezier(0, 0, 0.58, 1)

可选 ease-in-out：慢速开始，慢速结束；相当于 cubic-bezier(0.42, 0, 0.58, 1)

可选 cubic-bezier(n, n, n, n)：在 bezier 函数中自定义 0 ~ 1 之间的数值。

贝塞尔时间曲线详解。

【4】transition-delay：

规定过渡效果的延迟时间，默认为 0s 。
如果在 hover 状态下也设置了 transition 属性，则 hover 状态下的为前进状态，非 hover 状态下的为反向状态。

<------------------------------css3 2D转换--------------------------------------->
translate(x,y) 移动  x 水平移动 y 垂直移动
transform: translate(x,y)  变形： 移动；  配合过渡和动画使用  这个属性给。active 点击触发 按钮动画不错

transform: translate(-50%,-50%) /* translate 移动距离如果是 % 不是以父级宽度为准，而是以自己的宽度 可以让定位的盒子居中对齐*/

scale(x,y) 缩小 放大

rotate(deg) 旋转 //deg 是度数 正值是顺时针 负值时逆时针
transform-origin: (xx)px,top 设置变形的中心点 // 如果时 4 个角 可以用 left top 如果想要精准的我为之 可以用 px 像素

skew(deg,deg) 倾斜      注意 X 轴是右往左  y 轴是下往上

<------------------------------css3 3D转换--------------------------------------->
transform: rotateX(deg)            类似翻转
transform: rotateY                 类似开合页
transform: rotateZ  三种 3d 旋转      类似平面旋转
backface-visibility: hidden;  // 只要不是正面对屏幕 就隐藏 作翻转两面的效果

perspective: 1000px // 视距 距离 眼睛到屏幕的距离 视距越小透视效果越明显

transform: translate3d(x,y,z); x 和 y 可是是 px 和 % z 只能是 px  z 越大 物体越大 离我们越近

<------------------------------css3 动画--------------------------------------->
 // 引用动画
animation: go 2s ease 0s 2 reverse；
animation: 动画名称 动画时间 运动曲线 何时开始 播放次数（默认一次，infinite- 无限循环） 是否反方向 (alternate- 先正后反 交替）
/* 定义动画 */
@keyframes 动画名称 {
        from {
            transform: translateX(0);
        }
        to {
            transform: translateX(600px);
        }
}

@keyframes 动画名称 {
    0% {
        transform: translate3d(0,0,0);
    }
    20% {
        transform: translate3d(700px,0,0);
    }
    50% {
        transform: translate3d(700px,300px,0);  // 如果有多组变形 用空格隔开就好了
    }
    70% {
        transform: translate3d(0,300px,0);
    }
    100% {
        transform: translate3d(0,0,0);
    }
}

CSS 选择器有哪些
*通用选择器：选择所有元素，不参与计算优先级，兼容性 IE6+

//# X id 选择器：选择 id 值为 X 的元素，兼容性：IE6+

.X 类选择器： 选择 class 包含 X 的元素，兼容性：IE6+
X Y 后代选择器： 选择满足 X 选择器的后代节点中满足 Y 选择器的元素，兼容性：IE6+
X 元素选择器： 选择标所有签为 X 的元素，兼容性：IE6+
:link，:visited，:focus，:hover，:active 链接状态： 选择特定状态的链接元素，顺序 LoVe HAte，兼容性：IE4+
X + Y 直接兄弟选择器：在 X 之后第一个兄弟节点中选择满足 Y 选择器的元素，兼容性： IE7+
X > Y 子选择器： 选择 X 的子元素中满足 Y 选择器的元素，兼容性： IE7+
X ~ Y 兄弟： 选择 X 之后所有兄弟节点中满足 Y 选择器的元素，兼容性： IE7+
[attr]：选择所有设置了 attr 属性的元素，兼容性 IE7+
[attr=value]：选择属性值刚好为 value 的元素
[attr~=value]：选择属性值为空白符分隔，其中一个的值刚好是 value 的元素
[attr|=value]：选择属性值刚好为 value 或者 value- 开头的元素
[attr^=value]：选择属性值以 value 开头的元素
[attr$=value]：选择属性值以 value 结尾的元素
[attr=value]*：选择属性值中包含 value 的元素
[:checked]：选择单选框，复选框，下拉框中选中状态下的元素，兼容性：IE9+
X:after, X::after：after 伪元素，选择元素虚拟子元素（元素的最后一个子元素），CSS3 中：: 表示伪元素。兼容性：after 为 IE8+，::after 为 IE9+
:hover：鼠标移入状态的元素，兼容性 a 标签 IE4+， 所有元素 IE7+
:not(selector)：选择不符合 selector 的元素。不参与计算优先级，兼容性：IE9+
::first-letter：伪元素，选择块元素第一行的第一个字母，兼容性 IE5.5+
::first-line：伪元素，选择块元素的第一行，兼容性 IE5.5+
:nth-child(an + b)：伪类，选择前面有 an + b - 1 个兄弟节点的元素，其中 n >= 0， 兼容性 IE9+
:nth-last-child(an + b)：伪类，选择后面有 an + b - 1 个兄弟节点的元素 其中 n >= 0，兼容性 IE9+
X:nth-of-type(an+b)：伪类，X 为选择器，解析得到元素标签，选择前面有 an + b - 1 个相同标签兄弟节点的元素。兼容性 IE9+
X:nth-last-of-type(an+b)：伪类，X 为选择器，解析得到元素标签，选择后面有 an+b-1 个相同标签兄弟节点的元素。兼容性 IE9+
X:first-child：伪类，选择满足 X 选择器的元素，且这个元素是其父节点的第一个子元素。兼容性 IE7+
X:last-child：伪类，选择满足 X 选择器的元素，且这个元素是其父节点的最后一个子元素。兼容性 IE9+
X:only-child：伪类，选择满足 X 选择器的元素，且这个元素是其父元素的唯一子元素。兼容性 IE9+
X:only-of-type：伪类，选择 X 选择的元素，解析得到元素标签，如果该元素没有相同类型的兄弟节点时选中它。兼容性 IE9+
X:first-of-type：伪类，选择 X 选择的元素，解析得到元素标签，如果该元素 是此此类型元素的第一个兄弟。选中它。兼容性 IE9+
