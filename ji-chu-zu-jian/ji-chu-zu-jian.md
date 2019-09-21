---
description: flutter中最基本的组件
---

# 基础组件

## **1. Container 组件**

_**说明**_： 由于 _**Container**_ 组合了许多其他小部件，每个小部件都具有自己的布局行为，因此 _**Container**_ 的布局行为有些复杂。

_**介绍**_： _**Container**_ 是一个组合类容器，它是由常见的 _**绘画**_，_**定位**_ 和 _**尺寸调整**_ 等相关组件所组成的一个多功能容器，所以我们只需通过一个 _**Container**_ 组件可以实现同时需要 _**装饰**_、_**变换**_、_**限制**_ 的场景。

_**注意**_：

*  容器的大小可以通过 `width`、`height` 属性来指定，也可以通过`constraints` 来指定；如果它们同时存在时，`width`、`height` 优先。实际上 _**Container**_ 内部会根据 `width`、`height` 来生成一个 `constraints`。
* `color` 和 `decoration` 是互斥的，如果同时设置它们则会报错！实际上，当指定 `color` 时，_**Container**_ 内会自动创建一个 _**decoration**_。

_**属性**_：

```dart
const Container({
    Key key; // 类似于 react 中的 key
    AlignmentGeometry alignment; // 对齐方式
    EdgeInsetsGeometry padding; // 容器内补白，属于decoration的装饰范围
    Color color; // 背景色
    Decoration decoration; // 背景装饰
    Decoration foregroundDecoration; // 前景装饰
    double width; // 容器的宽度
    double height; // 容器的高度
    BoxConstraints constraints; // 容器大小的限制条件
    EdgeInsetsGeometry margin; // 容器外补白，不属于decoration 的装饰范围
    Matrix4 transform; // 变换
    Widget child; // 子组件
})
```

_**例子**_：

```dart
/// 此示例显示了一个 48x48 的琥珀色正方形，放置在 Center 组件内，以免造成其它影响
Center(
  child: Container(
    margin: const EdgeInsets.all(10.0),
    color: Colors.amber[600],
    width: 48.0,
    height: 48.0,
  ),
)

/// 展示了 Container 的一些功能，显示的是一个旋转的矩形，矩形的中心是一个 Hello World
Container(
  constraints: BoxConstraints.expand(
    height: Theme.of(context).textTheme.display1.fontSize * 1.1 + 200.0,
  ),
  padding: const EdgeInsets.all(8.0),
  color: Colors.blue[600],
  alignment: Alignment.center,
  child: Text('Hello World',
    style: Theme.of(context)
        .textTheme
        .display1
        .copyWith(color: Colors.white)),
  transform: Matrix4.rotationZ(0.1),
)
```

## **2. Row 组件**

_**说明**_： 其设计是基于_**web**_ 开发中的 _**Flexbox**_ 布局模型。

_**介绍**_：_**Row**_  可以在水平方向排列其子_**widget**_。

* 如果想要将子项自适应所剩余的空间，则需要包装在 _**Expanded  组件**_ 中（类似于 _**css 弹性盒模型**_）。_**Row**_ 组件不会滚动，如果想要滚动，请使用 _**ListView 组件**_。

_**属性**_：

```dart
const Row({
    // 类似 React 组件中的 key
    Key key;
    // 如何将子项放在主轴上，默认为行的左侧或列的顶部
    MainAxisAlignment mainAxisAlignment = MainAxisAlignment.start;   
    // 主轴占用的空间，默认为最大
    MainAxisSize mainAxisSize = MainAxisSize.max;    
    // 十字轴上的排列方式
    CrossAxisAlignment crossAxisAlignment = CrossAxisAlignment.center;
    // 用作主轴的方向
    TextDirection textDirection;
    // 垂直放置的顺序
    VerticalDirection verticalDirection = VerticalDirection.down;
    // 对其哪个基线
    TextBaseline textBaseline;
    // 子部件
    List<Widget> children = const <Widget>[];    
})
```

_**例子**_：

```dart
/// 此示例将可用空间划分为三个（水平），并将文本放在前两个单元格中心，将Flutter徽标放在第三个中心：
Row(
  children: <Widget>[
    Expanded(
      child: Text('Deliver features faster', textAlign: TextAlign.center),
    ),
    Expanded(
      child: Text('Craft beautiful UIs', textAlign: TextAlign.center),
    ),
    Expanded(
      child: FittedBox(
        fit: BoxFit.contain, // otherwise the logo will be tiny
        child: const FlutterLogo(),
      ),
    ),
  ],
)
```

## 3. Column 组件 

_**说明**_： 其设计是基于_**web**_ 开发中的 _**Flexbox**_ 布局模型。

_**介绍**_：_**Column**_  可以在垂直方向排列其子_**widget**_。

* 如果想要将子项自适应所剩余的空间，则需要包装在 _**Expanded  组件**_ 中（类似于 _**css 弹性盒模型**_）。_**Column**_ 组件不会滚动，如果想要滚动，请使用 _**ListView 组件**_。

_**属性**_：

```dart
const Column({
    // 类似 React 组件中的 key
    Key key;
    // 如何将子项放在主轴上，默认为行的左侧或列的顶部
    MainAxisAlignment mainAxisAlignment = MainAxisAlignment.start;   
    // 主轴占用的空间，默认为最大
    MainAxisSize mainAxisSize = MainAxisSize.max;    
    // 十字轴上的排列方式
    CrossAxisAlignment crossAxisAlignment = CrossAxisAlignment.center;
    // 用作主轴的方向
    TextDirection textDirection;
    // 垂直放置的顺序
    VerticalDirection verticalDirection = VerticalDirection.down;
    // 对其哪个基线
    TextBaseline textBaseline;
    // 子部件
    List<Widget> children = const <Widget>[];    
})
```

_**例子**_：

```dart
/// 此示例使用Column垂直排列三个小部件，最后一个小部件用于填充所有剩余空间。
Column(
  children: <Widget>[
    Text('Deliver features faster'),
    Text('Craft beautiful UIs'),
    Expanded(
      child: FittedBox(
        fit: BoxFit.contain, // otherwise the logo will be tiny
        child: const FlutterLogo(),
      ),
    ),
  ],
)
```

## 4. Image 组件
_**说明**_：创建图片的组件

_**介绍**_：

* 支持以下图像格式：`JPEG`，`PNG`，`GIF`，`GIF`，`WebP`，`BMP` 和 `WBMP`。

* 提供了几种可用于指定图像的方法的构造函数：

  * `new Image`，用于从 `ImageProvider` 获得图像。

  * `new Image.asset`，用于从资源目录显示图片。

  * `new Image.network`，用于从 URL 获取图像（获取网路图片）。

  * `new Image.file`，用于从 File 获取图像。

  * `new Image.memory`，用于从 `Uint8List（内存）` 获取图像。

```dart
// 资源图片
new Image.asset('imgs/logo.jpeg'),
//网络图片
new Image.network(
    'https://flutter.io/images/homepage/header-illustration.png'),
// 本地文件图片
new Image.file(new File("/Users/gs/Downloads/1.jpeg")),
// Uint8List 图片
new Image.memory(bytes),
//使用 ImageProvider 加载图片
new Image(image: new NetworkImage("https://flutter.io/images/homepage/screenshot-2.png"))
```

_**属性**_：

```dart
const Image({
  Key key; // 类似 react 组件中的 key
  ImageProvider<dynamic> image;
  Widget Function(BuildContext, Widget, int, bool) frameBuilder;
  Widget Function(BuildContext, Widget, ImageChunkEvent) loadingBuilder;
  String semanticLabel;
  bool excludeFromSemantics = false;
  double width; // 图片的宽
  double height; // 图片的高
  Color color; // 图片的混合色值
  BlendMode colorBlendMode;
  BoxFit fit; // 缩放模式
  AlignmentGeometry alignment = Alignment.center;// 对其方式，默认为居中
  ImageRepeat repeat = ImageRepeat.noRepeat; // 重复方式，默认不重复
  Rect centerSlice;
  bool matchTextDirection = false;
  bool gaplessPlayback = false;
  FilterQuality filterQuality = FilterQuality.low;
})
```

## 5. Text 组件（类似于 &lt;p&gt;）

_**说明**_：该 _**widget**_ 可让创建一个带格式的文本。

_**介绍**_：_**Text 组件**_ 显示一个样式单一的文本字符串。根据布局约束，字符串可能跨多行显示，也可能全部显示在同一行上。

_**属性**_：

```dart
const Text(
    String data; // 要显示的文本
    {
        Key key; // 类似于 react 组件中的 key 
        TextStyle style； // 文本样式
        StrutStyle strutStyle; // 支撑样式
        TextAlign textAlign; // 对齐方式
        TextDirection textDirection; // 文本显示的方向
        Locale locale; // 设置语言环境，就是国际化，多语言支持
        bool softWrap; // 文本是否应该在换行符处断行 
        TextOverflow overflow; // 用来处理文本溢出
        double textScaleFactor; // 每个逻辑像素的字体像素值
        int maxLines; // 显示文本的最大行数
        String semanticsLabel; // 该文本的另一种语义标签
        TextWidthBasis textWidthBasis; // 设置空值
    }
)
```

_**例子**_：

```dart
/// 这个例子展示了如何使用文本小部件显示文本。如果文本溢出，则使用省略号截断文本。
Text(
    'Hello, $_name! How are you?',
    textAlign: TextAlign.center,
    overflow: TextOverflow.ellipsis,
    style: TextStyle(fontWeight: FontWeight.bold),
)
```

### _**5.1 TextSpan组件（类似于 &lt;span&gt;）**_

_**说明**_：类似于 _**html**_ 中的 _**span**_，将文字放在一行。

_**介绍**_：_**TextSpan**_ 需要套一层 _**`Text.rich`**_，可以有`children`，`children`同为 _**TextSpan**_，可以分别加不同的样式，这里只能加样式，不可以加其他的属性。

_**属性**_：

```dart
const TextSpan({
    String text; // 要显示的内容
    List children; // 子部件，同为 TextSpan
    TextStyle style; // 要应用于此范围内的 TextStyle 样式
    GestureRecognizer recognizer; // 一个手势识别器，它将接收达到此范围的事件。
    String semanticsLabel; // 此 TextSpan 的替代语义标签
})
```

_**例子**_：

```dart
/// 使用 Text.rich 构造函数，文本小部件可以显示具有不同样式 textspan 的段落。下面的示例为每个单词显示不同样式的“Hello beautiful world”。
const Text.rich(
 TextSpan(
   text: 'Hello', // default text style
   children: <TextSpan>[
     TextSpan(text: ' beautiful ', style: TextStyle(fontStyle: FontStyle.italic)),
     TextSpan(text: 'world', style: TextStyle(fontWeight: FontWeight.bold)),
   ],
 ),
)
```

## 6. Icon 组件

## 7. RaisedButton 组件

## 8. Scaffold 组件

## 9. Appbar 组件

## 10. FlutterLogo 组件

## 11. Placeholder 组件

