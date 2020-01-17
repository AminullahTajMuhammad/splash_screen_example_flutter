
## Lunching Other Screen After Delay in Flutter.

### Using Duration & Timer to Create Simple Splash Screen in Flutter

![](https://cdn-images-1.medium.com/max/2000/1*s1CSC8UuLB3XLlj7cflCPA.gif)

Hello Guys, this is my third article of this series. In this article we’ll learn about splash screen in flutter. Most of the applications have splash screen. The working on splash screen is depends on the product. This article is basically part of **[Today I Learned](http://github.com/AminullahTajMuhammad/Today-I-learned/)**.

## Here is the video tutorial

In Android Development we use ```` postDelayed()```` Callback to hold the screen. But in Flutter this is much tricky because in Flutter there are ````async methods```` that perform such type of tasks.

In case you are not familiar, here’s a little overview about the difference between ````StatefulWidget```` and ````StatelessWidget````.

**StatefulWidget** is a widget that loads dynamically like it changes their states or rebuild at run time.

**StatelessWidget** is a widget that loads only compile time like it never rebuild by itself. It is usually use for build the UI of the screen.

So first add a class which extends from StatefulWidget like this.
````dart
  class SplashScreen extends StatefulWidget {
    @override                         
    State<StatefulWidget> createState() {
      return SplashState();
    }
  }
````

Now override the method ````createState```` that returns the state of the screen class. So, for this we create new class which extends from ````State```` class.

````dart
class SplashState extends State<SplashScreen> {
  @override
  void initState() {
    // TODO: implement initState
    super.initState();
    startTime();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: initScreen(context),
    );
  }
}
````

So, it will override ````initState```` and ````build```` methods. In ````initState```` method, we add delay functionality by adding these lines here.

````dart
startTime() async {
  var duration = new Duration(seconds: 6);
  return new Timer(duration, route);
}
````

The ````startTime```` method is an ````async```` method that perform task in background. We use ````Timer```` class for this where we pass duration for holding the screen and **route/designation** to indicate where to go. We use ````Navigator```` to set the route/designation. Here is the code.

````dart
route() {
  Navigator.pushReplacement(context, MaterialPageRoute(
      builder: (context) => AuthenticationScreen()
    )
  ); 
}
````

For Timer class import this file.

````dart
import 'dart:async';
````

So, after that their is a build method that helps to creates User Interface of the screen.

Here is the full code of the ````SplashScreen.dart````
````dart
import 'dart:async';
import 'package:flutter/material.dart';
import 'package:screens/SecondScreen';                                               

class SplashScreen extends StatefulWidget {
  @override
  State<StatefulWidget> createState() {
    return SplashState();
}

class SplashState extends State<SplashScreen> {
  @override
  void initState() {
    // TODO: implement initState
    super.initState();
    startTime();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: initScreen(context),
    );
  }

  startTime() async {
    var duration = new Duration(seconds: 6);
    return new Timer(duration, route);
  }

route() {
    Navigator.pushReplacement(context, MaterialPageRoute(
        builder: (context) => SecondScreen()
      )
    ); 
  }

  initScreen(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Container(
              child: Image.asset("images/logo.png"),
            ),
            Padding(padding: EdgeInsets.only(top: 20.0)),
            Text(
              "Splash Screen",
              style: TextStyle(
                fontSize: 20.0,
                color: Colors.white
              ),
            ),
            Padding(padding: EdgeInsets.only(top: 20.0)),
            CircularProgressIndicator(
              backgroundColor: Colors.whit*,
              strokeWidth: 1,
           )
         ],
       ),
      ),
    );
  }
}
````

### Here is the result.

![](https://cdn-images-1.medium.com/max/2000/1*tDUKpnVD59xp8NhwPgWvng.gif)

So, That’s all for now, Cheerssssss! 🍷

Article is orginally publish on my [Blog](https://aminullah.me)

Sharing is caring. Follow me on [GitHub](https://github.com/AminullahTajMuhammad), [Twitter](http://twitter.com/aminullah_taj), [YouTube](https://www.youtube.com/channel/UCM4b58vrfPJjr_nDqCLzuXA),
