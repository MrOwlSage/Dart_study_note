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

4. **didChangeDependencies():** 这个方法会在initState()方法后立即被调用。如果是InheritedWidget的StatefuWidget会在数据有变化时也会被调用（此处后期再进行补充）

5. 



