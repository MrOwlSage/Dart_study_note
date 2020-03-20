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
2. **mounted** 当调用createState时，一个buildContext被分派给了这个state

