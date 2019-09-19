## ***flutter*** 知识

+ [***flutter官网网站***](https://flutter.dev)
+ [***flutter中文网***](https://flutterchina.club/)
+ [***flutter实战教程***](https://book.flutterchina.club/)
+ [***flutter组件目录大全***](https://flutterchina.club/widgets/)

#### 一、基础 ***Widget*** 组件

> [***基础组件相关地址***](https://flutter.dev/docs/development/ui/widgets/layout)

##### 1.1 ***Text*** 组件（类似于 p）

> ***说明***：该 ***widget*** 可让创建一个带格式的文本。
>
> ***介绍***：***Text***小部件显示一个样式单一的文本字符串。根据布局约束，字符串可能跨多行显示，也可能全部显示在同一行上。
>
> ***常用属性***：
>
> | 属性名                | 类型                 | 含义                                  |
> | --------------------- | -------------------- | ------------------------------------- |
> | ***data***            | ***String***         | 要显示的文本（位于第一个参数）        |
> | ***locale***          | ***Locale***         | 设置语言环境  就是国际化，多语言支持  |
> | ***maxLines***        | ***int***            | 显示文本的最大行数                    |
> | ***overflow***        | ***TextOverflow***   | 用来处理文本溢出                      |
> | ***semanticsLabel***  | ***String***         | 该文本的另一种语义标签                |
> | ***softWrap***        | ***bool***           | 文本是否应该在换行符处断行            |
> | ***strutStyle***      | ***StrutStyle***     | 支撑样式                              |
> | ***style***           | ***TextStyle***      | 文本样式                              |
> | ***textAlign***       | ***TextAlign***      | 文本水平对齐方式                      |
> | ***textDirection***   | ***TextDirection***  | 文本显示的方向                        |
> | ***textScaleFactor*** | ***double***         | 每个逻辑像素的字体像素值              |
> | ***textWidthBasis***  | ***TextWidthBasis*** | 设置空值                              |
> | ***Key***             | ***Key***            | 类似于 ***react*** 组件中的 ***key*** |
>
> ***例子：***
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
>

##### 1.2 ***TextSpan组件（类似于 span）***

>***说明***：类似于 ***html*** 中的 ***span***，将文字放在一行。
>
>***介绍***：***TextSpan*** 需要套一层 ***Text.rich***，可以有`children`，`children`同为 ***TextSpan***，可以分别加不同的样式，这里只能加样式，不可以加其他的属性。
>
>***属性：***
>
>| 属性                 | 类型                    | 含义                                       |
>| -------------------- | ----------------------- | ------------------------------------------ |
>| ***children***       | ***List<InlineSpan>***  | ***children*** 子集，同为 ***TextSpan***   |
>| ***recognizer***     | ***GestureRecognizer*** | 一个手势识别器，它将接收达到此范围的事件。 |
>| ***semanticsLabel*** | ***String***            | 此 ***TextSpan*** 的替代语义标签           |
>| ***span***           | ***String***            | 文本内容                                   |
>| ***style***          | ***TextStyle***         | 要应用于此范围内的 ***TextStyle*** 样式    |
>| ***runtimeType***    | ***Type***              | 表示对象的运行时类型。                     |
>
>***例子***：
>
>```dart
>/// 使用 Text.rich 构造函数，文本小部件可以显示具有不同样式 textspan 的段落。下面的示例为每个单词显示不同样式的“Hello beautiful world”。
>const Text.rich(
>  TextSpan(
>    text: 'Hello', // default text style
>    children: <TextSpan>[
>      TextSpan(text: ' beautiful ', style: TextStyle(fontStyle: FontStyle.italic)),
>      TextSpan(text: 'world', style: TextStyle(fontWeight: FontWeight.bold)),
>    ],
>  ),
>)
>```
>

##### 1.3 ***Row, Column*** 组件

> ***说明***： 其设计是基于***web***开发中的***Flexbox***布局模型。
>
> ***介绍***：这些具有弹性空间的布局类***Widget***可让您在水平（***Row***）和垂直（***Column***）方向上创建灵活的布局。
>
> ​		***Row***：要使子项扩展以填充可用的水平空间，请将子项包装在[***Expanded***](https://api.flutter.dev/flutter/widgets/Expanded-class.html)小部件中。***Row*** 窗口小部件不会滚动，如果想要滚动，请使用 [***ListView***](https://api.flutter.dev/flutter/widgets/ListView-class.html)。
>
> ​	***Column***：要使子项扩展以填充可用的垂直空间，请将子项包装在[***Expanded***](https://api.flutter.dev/flutter/widgets/Expanded-class.html)小部件中。***Column*** 窗口小部件不会滚动，如果想要滚动，请使用 [***ListView***](https://api.flutter.dev/flutter/widgets/ListView-class.html)。
>
> ***例子：***
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
> ***属性***：
>
> ```dart
> const Row, Column (
>     List<Widget> children; // 子组件
>     CrossAxisAlignment crossAxisAlignment; // 十字轴上的排列方式
>     Axis direction; // 用作主轴的方向
>     int hashCode; 
>     Key key;
>  	MainAxisAlignment mainAxisAlignment; // 如何将子项放在主轴上，默认为行的左侧或列的顶部
>     MainAxisSize mainAxisSize; // 主轴占用的空间
>     Type runtimeType;
>     TextBaseline textBaseline; // 对其哪个基线
>     TextDirection  textDirection; // 文本排列方向
>     VerticalDirection  verticalDirection; // 垂直放置的顺序
> )
> ```
>
> 

##### 1.4 ***Stack*** 组件

> ***说明：******Stacks***是基于***Web***开发中的绝度定位（***absolute positioning*** )布局模型设计的。
>
> ***介绍***：取代线性布局 (译者语：和***Android***中的***LinearLayout***相似)，***Stack*** 允许子 ***widget*** 堆叠， 你可以使用 ***Positioned*** 来定位他们相对于 ***Stack*** 的上下左右四条边的位置。
>
> ***例子***：
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
> ***属性***：
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
>
> 

##### ***1.5 Container*** 组件

> ***说明***： ***Container*** 可让您创建矩形视觉元素。
>
> ***介绍***： ***Container*** 可以装饰为一个***BoxDecoration***, 如 ***background***、一个边框、或者一个阴影。 ***Container*** 也可以具有边距（***margins***）、填充(***padding***)和应用于其大小的约束(***constraints***)。另外， ***Container***可以使用矩阵在三维空间中对其进行变换。
>
> ***例子：***
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
> ***属性***：
>
> ```dart
> const Container (
> 	AlignmentGeometry alignment; // 将子组件在容器内对齐
>     Widget child; // 子组件
>  	BoxConstraints constraints; // 约束条件
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
>
> 

---

#### 二、布局小组件

##### 2.1 单子布局小组件

###### 2.1.1 ***Align 组件***

> ***说明：***一个小部件，它将其子组件与其自身对齐，并根据子级的大小自行调整大小。

###### ***2.1.2 AspectRatio 组件***

> ***说明：***将子组件调整为特定宽高比的小部件。

###### ***2.1.3 Baseline 组件***

###### ***2.1.4 Center 组件***

###### ***2.1.5 ConstrainedBox 组件***

###### ***2.1.6 Container 组件***

###### ***2.1.7 ConstrainedBox 组件***

###### 2.1.8 ***FittedBox*** 组件

###### 2.1.9 ***FractionallySizedBox*** 组件

###### 2.1.10 ***IntrinsicHeight*** 组件

###### 2.1.11 ***IntrinsicWidth*** 组件

###### 2.1.12 ***LimitedBox*** 组件

###### 2.1.13 ***Offstage*** 组件

###### 2.1.14 ***OverflowBox*** 组件

###### 2.1.15 ***Padding*** 组件

###### 2.1.16 ***SizedBox*** 组件

###### 2.1.17 ***SizedOverflowBox 组件***

###### 2.1.18 ***Transform 组件***

---



##### 2.2 多子布局小组件

###### 2.2.1 ***Column 组件***

###### 2.2.2 ***CustomMultiChildLayout 组件***

###### 2.2.3 ***Expanded*** 组件

###### 2.2.4 ***Flow*** 组件

###### 2.2.5 ***GridView*** 组件

###### 2.2.6 ***IndexedStack*** 组件

###### 2.2.7 ***LayoutBuilder*** 组件

###### 2.2.8 ***ListBody*** 组件

###### 2.2.9 ***ListView*** 组件

###### 2.2.10 ***Row*** 组件

###### 2.2.11 ***Stack*** 组件

###### 2.2.12 ***Table*** 组件

###### 2.2.13 ***Wrap*** 组件



---



#### 三、***Material*** 组件

> [***Material 相关组件地址***](https://flutterchina.club/widgets/material/)

##### 3.1 ***App 结构和导航组件***

###### 3.1.1 ***Scaffold 组件***

> ***说明***：***Material Design***布局结构的基本实现。此类提供了用于显示***drawer***、***snackbar***和底部***sheet***的***API***。

###### 3.1.2 ***AppBar 组件***

> ***说明***：一个***Material Design***应用程序栏，由工具栏和其他可能的***widget***（如***TabBar***和***FlexibleSpaceBar***）组成。

###### 3.1.3 ***BottomNavigationBar 组件***

> ***说明：***底部导航条，可以很容易地在 ***tap*** 之间切换和浏览顶级视图。

###### 3.1.4 ***TabBar 组件***

> ***说明：***一个显示水平选项卡的 ***Material Design widget***。

###### 3.1.5 ***TabBarView 组件***

> ***说明：***显示与当前选中的选项卡相对应的页面视图。通常和 ***TabBar*** 一起使用。

###### 3.1.6 ***MaterialApp 组件***

> ***说明：***一个方便的***widget***，它封装了应用程序实现 ***Material Design*** 所需要的一些 ***widget***。 

###### 3.1.7 ***WidgetsApp 组件***

> ***说明***：一个方便的类，它封装了应用程序通常需要的一些***widget***。

###### 3.1.8 ***Drawer 组件***

> ***介绍***：水平滑动的抽屉组件
>
> ***说明：***从***Scaffold***边缘水平滑动以显示应用程序中导航链接的***Material Design***面板。

##### 3.2 ***按钮***

###### 3.2.1 ***RaisedButton 组件***

> ***说明：******Material Design*** 中的 ***button***， 一个凸起的材质矩形按钮

###### 3.2.2 ***FloatingActionButton 组件***

> ***说明：***一个圆形图标按钮，它悬停在内容之上，以展示应用程序中的主要动作。***FloatingActionButton***通常用于 ***Scaffold.floatingActionButton*** 字段。

###### 3.2.3 ***FlatButton 组件***

> ***说明：***一个扁平的***Material***按钮

###### 3.2.4 ***IconButton 组件***

> ***说明***：一个***Material***图标按钮，点击时会有水波动画

###### 3.2.5 ***PopupMenuButton 组件***

> ***介绍***：右上角点击呼出菜单
>
> ***说明：***当菜单隐藏式，点击或调用onSelected时显示一个弹出式菜单列表

###### 3.2.6 ***ButtonBar 组件***

> ***说明：***水平排列的按钮组

##### 3.3 输入框和选择框

###### 3.3.1 ***TextField 组件***

> ***说明：***文本输入框

###### 3.3.2 ***Checkbox 组件***

> ***说明：*** 复选框，允许用户从一组中选择多个选项。

###### 3.3.3 ***Radio 组件***

> ***说明：***单选框，允许用户从一组中选择一个选项。

###### 3.3.4 ***Switch 组件***

> ***说明：******On/off*** 用于切换一个单一状态

###### 3.3.5 ***Slider 组件***

> ***说明：*** 滑块，允许用户通过滑动滑块来从一系列值中选择。

###### 3.3.6 ***Date & Time Pickers 组件***

> ***说明：***日期 ***&*** 时间选择器

##### 3.4 对话框、***Alert***、***Panel***

###### 3.4.1 ***SimpleDialog 组件***

> ***说明：***简单对话框可以显示附加的提示或操作

###### 3.4.2 ***AlertDialog 组件***

> ***说明：***一个会中断用户操作的对话款，需要用户确认

###### 3.4.3 ***BottomSheet 组件***

> ***说明：******BottomSheet*** 是一个从屏幕底部滑起的列表（以显示更多的内容）。你可以调用 ***showBottomSheet()***或 ***showModalBottomSheet*** 弹出

###### 3.4.4 ***ExpansionPanel 组件***

> ***说明：***折叠面板，允许对元素进行轻量级编辑。

###### 3.4.5 ***SnackBar 组件***

> ***说明：***具有可选操作的轻量级消息提示，在屏幕的底部显示。

##### 3.5 信息展示

###### 3.5.1 ***Image 组件***

> ***说明：***显示图片

###### 3.5.2 ***Icon 组件***

> ***说明：***图标

###### 3.5.3 ***Chip 组件***

> ***说明：***标签，一个***Material widget***。 它可以将一个复杂内容实体展现在一个小块中，如联系人。

###### 3.5.4 ***Tooltip 组件***

> ***说明：***一个文本提示工具，帮助解释一个按钮或其他用户界面，当***widget***长时间按下时（当用户采取其他适当操作时）显示一个提示标签。

###### 3.5.5 ***DataTable 组件***

> ***说明：***数据表显示原始数据集。它们通常出现在桌面企业产品中。***DataTable Widget***实现这个组件

###### 3.5.6 ***Card 组件***

> ***说明：***一个 ***Material Design*** 卡片。拥有一个圆角和阴影

###### 3.5.7 ***LinearProgressIndicator 组件***

> ***说明：***一个线性进度条，另外还有一个圆形进度条 ***CircularProgressIndicator***

##### 3.6 布局

###### 3.6.1 ***ListTitle 组件***

> ***说明：***一个固定高度的行，通常包含一些文本，以及一个行前或行尾图标。

###### 3.6.2 ***Stepper 组件***

> ***说明：***一个***Material Design*** 步骤指示器，显示一系列步骤的过程

###### 3.6.3 ***Divider 组件***

> ***说明：***一个***逻辑1像素厚***的水平分割线，两边都有填充

#### 四、手势操作

> [***手势操作相关文档***](https://flutterchina.club/gestures/)