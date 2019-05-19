# :incoming_envelope:UI #

在LayaAir的编译器中，我们可以去使用它的UI工具可以自动的帮我们编辑一些场景，动画之类的东西。但是使用工具只是会将图像UI转化为代码，一个UI类，需要我们去调用实现这个类。

首先使用工具完成一个UI制作,如下是UI的一些简单介绍与样式：




![](https://github.com/Lumnca/LayaAir/blob/master/img/a4.png)


实例UI只有一个标签（label）控件，取名为name，我们可以根据这个名称来获取到这个控件名称,制作好一定**要保存退出**，再返回到代码编辑界面。在

第一步建立UI实现类index.js：

![](https://github.com/Lumnca/LayaAir/blob/master/img/a5.png)

上图为我的项目文件目录。index.ui就是生成的UI文件类，index.JS为该UI的实现类（自己创建，并取名与UI名称一致），layaUI.max.all.js为总的UI注册类js文件，可以在这里面查看所有UI信息，接下里就是index.js为我们实现的类，如下编辑：

```javascript
var index = (function(_super){
    function index()
    {
        //继承UI类
        index.super(this);
        //初始化UI显示，自定义
        this.reset();
    }
    //注册类，将index.js注册到全局
    Laya.class(index,"index",_super);
    
    //为UI添加属性，便于操作UI
    var _proto = index.prototype;

    _proto.reset = function(){
        //name是我们命名label控件的名称，让他显示Lumnca
        this.name.text = "Lumnca";
    }

    return index;
})(ui.indexUI);
//继承indexUI类
```

如上面就编辑好了。最后在运行js中实例化这个类即可。

```javascript
Laya.init(600, 400);

var indexs = new index();

Laya.stage.addChild(indexs);
```

点击运行就可以看到我们的UI图像了。
