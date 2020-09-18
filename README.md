# Flutter Bottom Sheet
In this tutorial, we walk you through how to use bottom sheet in Flutter.

## What is Bottom Sheet?
Bottom sheet is a widget that slides up from the bottom of the screen to reveal more content.

## Types of Bottom Sheet
There are 2 types of Bottom Sheet
1. Persistent
   * Persistent Bottomsheet **allows** you to **interact** with other parts of the app.
   * Persistent bottom sheets can be created and displayed with the **ScaffoldState.showBottomSheet** function or by specifying the Scaffold.bottomSheet constructor parameter.
2. Modal
   * Modal Bottomsheet **does not** allows you to **interact** with other parts of the app.
   * Modal bottom sheets can be created and displayed with the **showModalBottomSheet** function.

## Implementing Bottom Sheet
Firstly, let's look at the code that shows the bottom sheet below.
```
Scaffold.of(context).showBottomSheet<T>(builder)
```
This implies that we need to show our bottomsheet **only inside a scaffold** otherwise the app will crash.
There are diffrent ways to solve this issue, but we'll teach you only the recommended method for building Bottom Sheet.
Our implementation method will required us to build a Bottom Sheet **under a piece of Widget**.This way we can avoid the context problem from either the Navigator or Scaffold. Noted that, we recommend you to define the fixed height for the bottom sheet for better display.

```
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      floatingActionButton: MyFloatingActionButton(),
      body: Center(
        child: Text('Bottom Sheet'),
      ),
    );
  }
}
class MyFloatingActionButton extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return FloatingActionButton(
      onPressed: () {
        showBottomSheet(
            context: context,
            builder: (context) => Container(
                  color: Colors.green,
                  height: 200;
                ));
      },
    );
  }
}
```
