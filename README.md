## 百分比流式布局(慢慢买官网用的就是这种思路)
- 遇到等分就用百分比
- 左浮动 + 右浮动(导航部分实现、折扣推荐导航部分) --> 适合于所有的元素宽度固定的
- 左浮动 + padding挤(见超值折扣推荐内容部分) 本质上元素大小在任何尺寸下面都是一致，改变的其实是元素与元素之间的间距大小 --> 适合一个元素宽度固定，另一个宽度自适应

### rem布局
- 见demo.html --> 之前上课时候大概的玩法(方便量尺寸)

- 更专业的玩法
https://github.com/amfe/lib-flexible

理论上每张图在各个手机上是比例一致的，我们很容易可以得出如下的结论：
由于：640下某元素容器的宽度 /  = 750下某元素容器的宽度 / 750
我们知道：(640下某元素容器的宽度 / 640) * 640 最终得到的还是原始的某元素容器的大小
所以，我们可以让html的font-size为640px，这样的话，实际上1px就相当于是 1 / 640 rem;
但这样算出来的值太小了，所以，我们可以让html为64px,这样，100px就相当于是100 / 64rem;
由于我们这个项目并没有psd图，我们的策略可以这样：
把慢慢买官网缩放到320px左右下面，然后比如量出来的是50px,其实相当于是100px,所以，相当于50 / 32 rem;
所以，我们把基准调成是32
这样，所有的尺寸可以用它的尺寸除以32得到rem的尺寸

### 注意事项
把慢慢买的项目切换到320尺寸下面

## 编辑器设置
### sublime
- rem-unit
```json
{
    "exts": [".html",".css", ".scss", ".less", ".sass", ".styl"], //启用此插件的文件类型。
    "fontsize": 32,//html元素font-size值，默认为16。
    "precision": 8,//px转rem的小数部分的最大长度，默认为8.
    "leadingzero": false,//是否保留前导0，默认不保留。
}
```

### vsCode设置
- px to rem

### webstorm设置
暂时没发现合适的插件

### less中字体自动生成mixin写法
#### 如何定义
```less
.ft(@fontSize){
    font-size: @fontSize;
    [data-dpr="2"] & {
        font-size: @fontSize * 2;
    }
    [data-dpr="3"] & {
        font-size: @fontSize * 3;
    }
}
```

#### 如何使用
```less
.ft(16px);
```

### sass中字体自动生成mixin写法
#### 如何定义
```scss
@mixin font-dpr($font-size){
    font-size: $font-size;
    [data-dpr="2"] & {
        font-size: $font-size * 2;
    }
    [data-dpr="3"] & {
        font-size: $font-size * 3;
    }
}
```

#### 如何使用
```scss
@include font-dpr(12px);
```

### 考拉如何使用(不需要安装任何插件最简单的使用less,sass的方法)
- [官网](http://koala-app.com/index-zh.html) 