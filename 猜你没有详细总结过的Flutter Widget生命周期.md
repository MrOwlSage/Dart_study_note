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

