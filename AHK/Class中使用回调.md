在`AHKv2`的`class`中使用`回调函数`与顶层环境不同，因此必须使用`ObjBindMethod`方法创建一个函数对象作为回调，例如：
```js
class MyClass{
  ;.........

  __New(targetId){  
    ;.........

    ; 类中的回调函数使用方法
    this.timerFun := ObjBindMethod(this, 'Method')
    SetTimer(this.timerFun, 10)
  }

  ;.........

  Method(){
    ;......
  }
}
```
使用`ObjBindMethod`方法创建了一个类中`timerFun`函数对象,这个对象可以在类中直接传递给例如`SetTimer`这种可接受函数对象作为回调函数的方法使用。