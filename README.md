# categoryOverrideMethod

category的用法大家都不陌生。

苹果推荐：

* 可以把类的实现分开在几个不同的文件里面。这样做有几个显而易见的好处，a)可以减少单个文件的体积 b)可以把不同的功能组织到不同的category里 c)可以由多个开发者共同完成一个类 d)可以按需加载想要的category 等等。
* 声明私有方法

然而，当一个类足够复杂，业务交叉足够多时，除了抽象封装以外，总要在VC中添加category，将功能按category分模块，然后项目调用公开的方法。这样可以做到至少感官上的解耦，便于维护单个功能的代码。

然而，有些方法我们不愿意公开，例如，某个模块相关的代码是UI的初始化，这个代码写在了viewdidload方法里，为了代码整齐，我写了一个viewdidloadForxxx  放到了category中。而某一天，产品又让加一个新模块，于是乎又写一个category，viewdidloadForyyyy。显得很繁琐，也很重复。

但是相同命名的方法，在同一个类中会被最后一个编译的category中的同名方法给覆盖（优先调用）。那么怎样做到犹如继承一样[super viewdidload] 的方法，将所有的同名方法一起调用的。

同时调用时，我希望主类的方法优先调用，因为它里面经常会有[super xxxxx];

这个简单的demo就是为了解决这个问题。

目前只实现了无参数与只有一个BOOL参数的情况。。其他情况还在研究中。

