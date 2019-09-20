---
description: flutter中最基本的组件
---

# 基础组件

### **1. Container 组件**

### **2. Row 组件**

### 3. Column 组件

### 4. Image 组件

### 5. Text 组件
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

### 6. Icon 组件

### 7. RaisedButton 组件

### 8. Scaffold 组件

### 9. Appbar 组件

### 10. FlutterLogo 组件

### 11. Placeholder 组件



