## 前言
在我们日常Flutter开发中，详细大家用的最多的就是StatelessWidget和StatefulWidget。那你有么有认真总结过Flutter Widget的生命周期呢？

## StatelessWidget
StatelessWidget在被创建以后只能被绘制一次。一个StatelessWidget不会因为任何事件活着用户的操作而进行重绘。
```dart
class TestStlWidget extends StatelessWidget {
   const TestStlWidget ({ Key key }) : super(key: key);
    @override
    Widget build(BuildContext context) {
      return Container();
    }
}

```

##  StatefulWidget
与StatelessWidget相反，StatefulWidget是一个可以根据事件或者用户操作进行重绘的widget。在它的生命周期中可以多次的被重绘。下面来看一下StatefulWidget的生命周期

![WeChatf6883bab3c7b5904adb5c6ae7cf83ba5.png](0)

1. **createState():** 当创建一个StatefulWidget时，会调用一个createState方法来创建State
```dart
class FirstPage extends StatefulWidget {
  FirstPage({Key key}) : super(key: key);
  _FirstPagePageState createState() => _FirstPagePageState();
}
```
2. **mounted:** 当调用createState时，一个BuildContext被分派给了这个state。那BuildContext怎么理解呢？其实你可以将BuildContext理解为它所对应的widget在这个渲染树上的一个点。
所有的widget都有mounted这个属性。只有widget的BuildContext被分配了，mounted才会为ture。我们不应该在mounted为false时调用setState方法

3. **initState():** 这是widget被创建以后在构造函数后，第一个被调用的方法。只调用一次，可以在里面初始化一些数据，以及绑定控制器，订阅一些stream，添加一些监听等等

4. **didChangeDependencies():** 这个方法会在initState()方法后立即被调用。如果继承自InheritedWidget的Widget会在数据有变化时其父类的didChangeDependencies也会被调用

5. **build()** 这个方法可以说是最重要的一个方法，用来构建widget。这个方法会再didChangeDependencies()方法后立即被调用。

6. **didUpdateWidget():** 如果父类的widget有变化并且需要重绘UI的时候会被调用。此方法会带有一个oldWidget的参数，你可以和当前的widge做一下对比来处理一些额外的逻辑。

7. **setState():** 此方会经常被Flutter framework自己或者开发者所实使用，以用来重新构建widget

8. **deactivate():** 当state被从树中移除时会被调用。但是它也有可能被重新插入到一个新的地方

9. **dispose():** 当state被渲染树永久移除时，会被调用。

10. **mounted = false** state再也不回被重新分配BuildContext，如果再调用setState则会抛出异常

## WidgetsBindingObserver
如果我们想知道应用什么时候进入后台，什么时候






