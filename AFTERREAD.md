# 我的Flutter注意事项

1. Flutter 的跨平台兼容性目前最好，前期开发调试完全在 Android 端进行的情况下，第一次在 IOS 平台运行居然没有任何错误，并且还没出现UI兼容问题
这些特点其实这得益于Flutter Engine 和 Skia。

2. Dart 下只有 bool 型可以用于 if 等判断，不同于 JS 这种使用方式是不合法的 var g = "null"; if(g){} ，DART中，switch 支持 String 类型

3. 设置了decoration的color，就不能设置Container的color

4. MainAxisSize的取值有两种：
max：根据传入的布局约束条件，最大化主轴方向的可用空间；
min：与max相反，是最小化主轴方向的可用空间;

5. 使用Card，用于快速简单的实现圆角和阴影

6. 设置缓存图片个数与大小
    缓存个数100：PaintingBinding.instance.imageCache.maximumSize = 100;
    缓存大小50M：PaintingBinding.instance.imageCache.maximumSizeBytes = 50 << 20;

7. flutter中的颜文字：\u{1f47f} //👿

## Dart的基础语法

1. num、int和double都是Dart中的类，也就是说它是对象级别的，所以他们的默认值为null

2. Map为若干个键值对的容器，想用映射之名。其中一个Map对象中的键不能重复，值是可以重复的:Map<int, String> map = {1: 'one', 2: 'two', 3: 'three'};

3. 对数组的所有元素做同一个操作，可用map方法：input.map((e){return e-5;})

4. Runes是一个类，是一个可比遍历的int型元素组合体

5. var 关键字:如果只是用var声明变量,该变量之后是可以修改数据类型的(未赋值的时候，类型是dynamic:动态的)
              如果声明的同时取赋值，那么该对象的类型就是固定的，不可修改

6. 如果一个变量你以后不打算修改，可以使用 final 或者 const进行修饰,当你试图修改它的值，就会报错。
   const与final的区别：一个final变量只能赋值一次：它的值在可以在运行时获取
                      一个const变量是编译时常量：代码还没有运行时我们就知道它声明变量的值
