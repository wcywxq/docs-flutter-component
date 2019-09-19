---
description: flutter 相关组件的介绍
---

# flutter\_Widget\_intro

* [_**flutter官网网站**_](https://flutter.dev)
* [_**flutter中文网**_](https://flutterchina.club/)
* [_**flutter实战教程**_](https://book.flutterchina.club/)
* [_**flutter组件目录大全**_](https://flutterchina.club/widgets/)

## 一、基础 _**Widget**_ 组件

> [_**基础组件相关地址**_](https://flutter.dev/docs/development/ui/widgets/layout)

### 1.1 _**Text**_ 组件（类似于 p）

> _**说明**_：该 _**widget**_ 可让创建一个带格式的文本。
>
> _**介绍**_：_**Text**_小部件显示一个样式单一的文本字符串。根据布局约束，字符串可能跨多行显示，也可能全部显示在同一行上。
>
> _**常用属性**_：
>
> | 属性名 | 类型 | 含义 |
> | :--- | :--- | :--- |
> | _**data**_ | _**String**_ | 要显示的文本（位于第一个参数） |
> | _**locale**_ | _**Locale**_ | 设置语言环境  就是国际化，多语言支持 |
> | _**maxLines**_ | _**int**_ | 显示文本的最大行数 |
> | _**overflow**_ | _**TextOverflow**_ | 用来处理文本溢出 |
> | _**semanticsLabel**_ | _**String**_ | 该文本的另一种语义标签 |
> | _**softWrap**_ | _**bool**_ | 文本是否应该在换行符处断行 |
> | _**strutStyle**_ | _**StrutStyle**_ | 支撑样式 |
> | _**style**_ | _**TextStyle**_ | 文本样式 |
> | _**textAlign**_ | _**TextAlign**_ | 文本水平对齐方式 |
> | _**textDirection**_ | _**TextDirection**_ | 文本显示的方向 |
> | _**textScaleFactor**_ | _**double**_ | 每个逻辑像素的字体像素值 |
> | _**textWidthBasis**_ | _**TextWidthBasis**_ | 设置空值 |
> | _**Key**_ | _**Key**_ | 类似于 _**react**_ 组件中的 _**key**_ |
>
> _**例子：**_
>
> ```dart
> /// 这个例子展示了如何使用文本小部件显示文本。如果文本溢出，则使用省略号截断文本。
> Text(
>     'Hello, $_name! How are you?',
>     textAlign: TextAlign.center,
>     overflow: TextOverflow.ellipsis,
>     style: TextStyle(fontWeight: FontWeight.bold),
> )
> ```

### 1.2 _**TextSpan组件（类似于 span）**_

> _**说明**_：类似于 _**html**_ 中的 _**span**_，将文字放在一行。
>
> _**介绍**_：_**TextSpan**_ 需要套一层 _**Text.rich**_，可以有`children`，`children`同为 _**TextSpan**_，可以分别加不同的样式，这里只能加样式，不可以加其他的属性。
>
> _**属性：**_
>
> | 属性 | 类型 | 含义 |
> | :--- | :--- | :--- |
> | _**children**_ | _**List**_ | _**children**_ 子集，同为 _**TextSpan**_ |
> | _**recognizer**_ | _**GestureRecognizer**_ | 一个手势识别器，它将接收达到此范围的事件。 |
> | _**semanticsLabel**_ | _**String**_ | 此 _**TextSpan**_ 的替代语义标签 |
> | _**span**_ | _**String**_ | 文本内容 |
> | _**style**_ | _**TextStyle**_ | 要应用于此范围内的 _**TextStyle**_ 样式 |
> | _**runtimeType**_ | _**Type**_ | 表示对象的运行时类型。 |
>
> _**例子**_：
>
> ```dart
> /// 使用 Text.rich 构造函数，文本小部件可以显示具有不同样式 textspan 的段落。下面的示例为每个单词显示不同样式的“Hello beautiful world”。
> const Text.rich(
>  TextSpan(
>    text: 'Hello', // default text style
>    children: <TextSpan>[
>      TextSpan(text: ' beautiful ', style: TextStyle(fontStyle: FontStyle.italic)),
>      TextSpan(text: 'world', style: TextStyle(fontWeight: FontWeight.bold)),
>    ],
>  ),
> )
> ```

### 1.3 _**Row, Column**_ 组件

> _**说明**_： 其设计是基于_**web**_开发中的_**Flexbox**_布局模型。
>
> _**介绍**_：这些具有弹性空间的布局类_**Widget**_可让您在水平（_**Row**_）和垂直（_**Column**_）方向上创建灵活的布局。
>
> ​ _**Row**_：要使子项扩展以填充可用的水平空间，请将子项包装在[_**Expanded**_](https://api.flutter.dev/flutter/widgets/Expanded-class.html)小部件中。_**Row**_ 窗口小部件不会滚动，如果想要滚动，请使用 [_**ListView**_](https://api.flutter.dev/flutter/widgets/ListView-class.html)。
>
> ​ _**Column**_：要使子项扩展以填充可用的垂直空间，请将子项包装在[_**Expanded**_](https://api.flutter.dev/flutter/widgets/Expanded-class.html)小部件中。_**Column**_ 窗口小部件不会滚动，如果想要滚动，请使用 [_**ListView**_](https://api.flutter.dev/flutter/widgets/ListView-class.html)。
>
> _**例子：**_
>
> ```dart
> /// 此示例将可用空间划分为三个（水平），并将文本放在前两个单元格中心，将Flutter徽标放在第三个中心：
> Row(
>   children: <Widget>[
>     Expanded(
>       child: Text('Deliver features faster', textAlign: TextAlign.center),
>     ),
>     Expanded(
>       child: Text('Craft beautiful UIs', textAlign: TextAlign.center),
>     ),
>     Expanded(
>       child: FittedBox(
>         fit: BoxFit.contain, // otherwise the logo will be tiny
>         child: const FlutterLogo(),
>       ),
>     ),
>   ],
> )
>     
> /// 此示例使用Column垂直排列三个小部件，最后一个小部件用于填充所有剩余空间。
> Column(
>   children: <Widget>[
>     Text('Deliver features faster'),
>     Text('Craft beautiful UIs'),
>     Expanded(
>       child: FittedBox(
>         fit: BoxFit.contain, // otherwise the logo will be tiny
>         child: const FlutterLogo(),
>       ),
>     ),
>   ],
> )
> ```
>
> _**属性**_：
>
> ```dart
> const Row, Column (
>     List<Widget> children; // 子组件
>     CrossAxisAlignment crossAxisAlignment; // 十字轴上的排列方式
>     Axis direction; // 用作主轴的方向
>     int hashCode; 
>     Key key;
>      MainAxisAlignment mainAxisAlignment; // 如何将子项放在主轴上，默认为行的左侧或列的顶部
>     MainAxisSize mainAxisSize; // 主轴占用的空间
>     Type runtimeType;
>     TextBaseline textBaseline; // 对其哪个基线
>     TextDirection  textDirection; // 文本排列方向
>     VerticalDirection  verticalDirection; // 垂直放置的顺序
> )
> ```

### 1.4 _**Stack**_ 组件

> _**说明：\***_Stacks_**是基于**_Web_**开发中的绝度定位（**_absolute positioning_\*_ \)布局模型设计的。
>
> _**介绍**_：取代线性布局 \(译者语：和_**Android**_中的_**LinearLayout**_相似\)，_**Stack**_ 允许子 _**widget**_ 堆叠， 你可以使用 _**Positioned**_ 来定位他们相对于 _**Stack**_ 的上下左右四条边的位置。
>
> _**例子**_：
>
> ```dart
> /// 使用 Stack，您可以将小部件放在彼此之上。
> Stack(
>   children: <Widget>[
>     Container(
>       width: 100,
>       height: 100,
>       color: Colors.red,
>     ),
>     Container(
>       width: 90,
>       height: 90,
>       color: Colors.green,
>     ),
>     Container(
>       width: 80,
>       height: 80,
>       color: Colors.blue,
>     ),
>   ],
> )
>     
> /// 此示例显示如何通过添加渐变背景来使用Stack来增强文本可见性。
> SizedBox(
>   width: 250,
>   height: 250,
>   child: Stack(
>     children: <Widget>[
>       Container(
>         width: 250,
>         height: 250,
>         color: Colors.white,
>       ),
>       Container(
>         padding: EdgeInsets.all(5.0),
>         alignment: Alignment.bottomCenter,
>         decoration: BoxDecoration(
>           gradient: LinearGradient(
>             begin: Alignment.topCenter,
>             end: Alignment.bottomCenter,
>             colors: <Color>[
>               Colors.black.withAlpha(0),
>               Colors.black12,
>               Colors.black45
>             ],
>           ),
>         ),
>         child: Text(
>           "Foreground Text",
>           style: TextStyle(color: Colors.white, fontSize: 20.0),
>         ),
>       ),
>     ],
>   ),
> )
> ```
>
> _**属性**_：
>
> ```dart
> const Stack (
>     AlignmentGeometry alignment; // 将堆叠中未定位和部分定位的子项对齐
>     StackFit fit; // 调整堆栈中未定位的子项的大小
>     Overflow overflow; // 溢出部分的操作
>     TextDirection textDirection; // 文本对齐方向
>     List<Widget> children; // 子组件
>     int hashCode;
>     Key key;
>     Type runtimeType; 
> )
> ```

### _**1.5 Container**_ 组件

> _**说明**_： _**Container**_ 可让您创建矩形视觉元素。
>
> _**介绍**_： _**Container**_ 可以装饰为一个_**BoxDecoration**_, 如 _**background**_、一个边框、或者一个阴影。 _**Container**_ 也可以具有边距（_**margins**_）、填充\(_**padding**_\)和应用于其大小的约束\(_**constraints**_\)。另外， _**Container**_可以使用矩阵在三维空间中对其进行变换。
>
> _**例子：**_
>
> ```dart
> /// 此示例展示了 48 x 48 的琥珀色方块(放置在Center组件中, 以免父组件影响 Container 组件的大小，并带有边距，以便于远离其它相邻组件)
> Center(
>   child: Container(
>     margin: const EdgeInsets.all(10.0),
>     color: Colors.amber[600],
>     width: 48.0,
>     height: 48.0,
>   ),
> )
>
> /// 这个例子展示了如何使用 Container 组件的一些特性。
> Container(
>   constraints: BoxConstraints.expand(
>     height: Theme.of(context).textTheme.display1.fontSize * 1.1 + 200.0,
>   ),
>   padding: const EdgeInsets.all(8.0),
>   color: Colors.blue[600],
>   alignment: Alignment.center,
>   child: Text('Hello World',
>     style: Theme.of(context)
>         .textTheme
>         .display1
>         .copyWith(color: Colors.white)),
>   transform: Matrix4.rotationZ(0.1),
> )
> ```
>
> _**属性**_：
>
> ```dart
> const Container (
>     AlignmentGeometry alignment; // 将子组件在容器内对齐
>     Widget child; // 子组件
>      BoxConstraints constraints; // 约束条件
>     Decoration decoration; // 子组件的装饰
>     Decoration foregroundDecoration; // 前景装饰
>     EdgeInsetsGeometry margin; // 外边距
>     EdgeInsetsGeometry padding; // 内边距
>     Matrix4 transform; // 变换
>     int hashCode;
>     Key key;
>     Type runtimeType; 
> )
> ```

## 二、布局小组件

### 2.1 单子布局小组件

#### 2.1.1 _**Align 组件**_

> _**说明：**_一个小部件，它将其子组件与其自身对齐，并根据子级的大小自行调整大小。

#### _**2.1.2 AspectRatio 组件**_

> _**说明：**_将子组件调整为特定宽高比的小部件。

#### _**2.1.3 Baseline 组件**_

#### _**2.1.4 Center 组件**_

#### _**2.1.5 ConstrainedBox 组件**_

#### _**2.1.6 Container 组件**_

#### _**2.1.7 ConstrainedBox 组件**_

#### 2.1.8 _**FittedBox**_ 组件

#### 2.1.9 _**FractionallySizedBox**_ 组件

#### 2.1.10 _**IntrinsicHeight**_ 组件

#### 2.1.11 _**IntrinsicWidth**_ 组件

#### 2.1.12 _**LimitedBox**_ 组件

#### 2.1.13 _**Offstage**_ 组件

#### 2.1.14 _**OverflowBox**_ 组件

#### 2.1.15 _**Padding**_ 组件

#### 2.1.16 _**SizedBox**_ 组件

#### 2.1.17 _**SizedOverflowBox 组件**_

#### 2.1.18 _**Transform 组件**_

### 2.2 多子布局小组件

#### 2.2.1 _**Column 组件**_

#### 2.2.2 _**CustomMultiChildLayout 组件**_

#### 2.2.3 _**Expanded**_ 组件

#### 2.2.4 _**Flow**_ 组件

#### 2.2.5 _**GridView**_ 组件

#### 2.2.6 _**IndexedStack**_ 组件

#### 2.2.7 _**LayoutBuilder**_ 组件

#### 2.2.8 _**ListBody**_ 组件

#### 2.2.9 _**ListView**_ 组件

#### 2.2.10 _**Row**_ 组件

#### 2.2.11 _**Stack**_ 组件

#### 2.2.12 _**Table**_ 组件

#### 2.2.13 _**Wrap**_ 组件

## 三、_**Material**_ 组件

> [_**Material 相关组件地址**_](https://flutterchina.club/widgets/material/)

### 3.1 _**App 结构和导航组件**_

#### 3.1.1 _**Scaffold 组件**_

> _**说明**_：_**Material Design**_布局结构的基本实现。此类提供了用于显示_**drawer**_、_**snackbar**_和底部_**sheet**_的_**API**_。

#### 3.1.2 _**AppBar 组件**_

> _**说明**_：一个_**Material Design**_应用程序栏，由工具栏和其他可能的_**widget**_（如_**TabBar**_和_**FlexibleSpaceBar**_）组成。

#### 3.1.3 _**BottomNavigationBar 组件**_

> _**说明：**_底部导航条，可以很容易地在 _**tap**_ 之间切换和浏览顶级视图。

#### 3.1.4 _**TabBar 组件**_

> _**说明：**_一个显示水平选项卡的 _**Material Design widget**_。

#### 3.1.5 _**TabBarView 组件**_

> _**说明：**_显示与当前选中的选项卡相对应的页面视图。通常和 _**TabBar**_ 一起使用。

#### 3.1.6 _**MaterialApp 组件**_

> _**说明：**_一个方便的_**widget**_，它封装了应用程序实现 _**Material Design**_ 所需要的一些 _**widget**_。

#### 3.1.7 _**WidgetsApp 组件**_

> _**说明**_：一个方便的类，它封装了应用程序通常需要的一些_**widget**_。

#### 3.1.8 _**Drawer 组件**_

> _**介绍**_：水平滑动的抽屉组件
>
> _**说明：**_从_**Scaffold**_边缘水平滑动以显示应用程序中导航链接的_**Material Design**_面板。

### 3.2 _**按钮**_

#### 3.2.1 _**RaisedButton 组件**_

> _**说明：\***_Material Design _**中的**_ button_\*_， 一个凸起的材质矩形按钮

#### 3.2.2 _**FloatingActionButton 组件**_

> _**说明：**_一个圆形图标按钮，它悬停在内容之上，以展示应用程序中的主要动作。_**FloatingActionButton**_通常用于 _**Scaffold.floatingActionButton**_ 字段。

#### 3.2.3 _**FlatButton 组件**_

> _**说明：**_一个扁平的_**Material**_按钮

#### 3.2.4 _**IconButton 组件**_

> _**说明**_：一个_**Material**_图标按钮，点击时会有水波动画

#### 3.2.5 _**PopupMenuButton 组件**_

> _**介绍**_：右上角点击呼出菜单
>
> _**说明：**_当菜单隐藏式，点击或调用onSelected时显示一个弹出式菜单列表

#### 3.2.6 _**ButtonBar 组件**_

> _**说明：**_水平排列的按钮组

### 3.3 输入框和选择框

#### 3.3.1 _**TextField 组件**_

> _**说明：**_文本输入框

#### 3.3.2 _**Checkbox 组件**_

> _**说明：**_ 复选框，允许用户从一组中选择多个选项。

#### 3.3.3 _**Radio 组件**_

> _**说明：**_单选框，允许用户从一组中选择一个选项。

#### 3.3.4 _**Switch 组件**_

> _**说明：\***_On/off_\*_ 用于切换一个单一状态

#### 3.3.5 _**Slider 组件**_

> _**说明：**_ 滑块，允许用户通过滑动滑块来从一系列值中选择。

#### 3.3.6 _**Date & Time Pickers 组件**_

> _**说明：**_日期 _**&**_ 时间选择器

### 3.4 对话框、_**Alert**_、_**Panel**_

#### 3.4.1 _**SimpleDialog 组件**_

> _**说明：**_简单对话框可以显示附加的提示或操作

#### 3.4.2 _**AlertDialog 组件**_

> _**说明：**_一个会中断用户操作的对话款，需要用户确认

#### 3.4.3 _**BottomSheet 组件**_

> _**说明：\***_BottomSheet _**是一个从屏幕底部滑起的列表（以显示更多的内容）。你可以调用**_ showBottomSheet\(\)_**或**_ showModalBottomSheet_\*_ 弹出

#### 3.4.4 _**ExpansionPanel 组件**_

> _**说明：**_折叠面板，允许对元素进行轻量级编辑。

#### 3.4.5 _**SnackBar 组件**_

> _**说明：**_具有可选操作的轻量级消息提示，在屏幕的底部显示。

### 3.5 信息展示

#### 3.5.1 _**Image 组件**_

> _**说明：**_显示图片

#### 3.5.2 _**Icon 组件**_

> _**说明：**_图标

#### 3.5.3 _**Chip 组件**_

> _**说明：**_标签，一个_**Material widget**_。 它可以将一个复杂内容实体展现在一个小块中，如联系人。

#### 3.5.4 _**Tooltip 组件**_

> _**说明：**_一个文本提示工具，帮助解释一个按钮或其他用户界面，当_**widget**_长时间按下时（当用户采取其他适当操作时）显示一个提示标签。

#### 3.5.5 _**DataTable 组件**_

> _**说明：**_数据表显示原始数据集。它们通常出现在桌面企业产品中。_**DataTable Widget**_实现这个组件

#### 3.5.6 _**Card 组件**_

> _**说明：**_一个 _**Material Design**_ 卡片。拥有一个圆角和阴影

#### 3.5.7 _**LinearProgressIndicator 组件**_

> _**说明：**_一个线性进度条，另外还有一个圆形进度条 _**CircularProgressIndicator**_

### 3.6 布局

#### 3.6.1 _**ListTitle 组件**_

> _**说明：**_一个固定高度的行，通常包含一些文本，以及一个行前或行尾图标。

#### 3.6.2 _**Stepper 组件**_

> _**说明：**_一个_**Material Design**_ 步骤指示器，显示一系列步骤的过程

#### 3.6.3 _**Divider 组件**_

> _**说明：**_一个_**逻辑1像素厚**_的水平分割线，两边都有填充

## 四、手势操作

> [_**手势操作相关文档**_](https://flutterchina.club/gestures/)

