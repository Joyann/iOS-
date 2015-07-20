在代码定义一个Button的时候，想要让Button上的文字距离边界更远或更近，我们可以通过重写__titleEdgeInsets__方法来实现。

比如我们用代码创建了一个自定义的button，如下图：

![](/Users/joyann/Desktop/文章/iOS碎片知识/4-代码修改自定义Button/1.png)

可以看到文字与Button的边缘很不好看，我们想让文字处于Button内的合适位置，这时候就可以在Button的类中重写__titleEdgeInsets__方法：

    - (UIEdgeInsets)titleEdgeInsets
    {
        return UIEdgeInsetsMake(4.0f, 28.0f, 4.0f, 28.0f);
    }
    
顾名思义，这个方法返回的就是button的title距离button边缘的距离。效果如下:

![](/Users/joyann/Desktop/文章/iOS碎片知识/4-代码修改自定义Button/2.png)

可以看到，这不是我们预期的那样。因为我们只是修改了title距离button边缘的距离，但并没有修改button的大小。解决方法如下：

在Button类中重写__intrinsicContentSize__方法。

    - (CGSize)intrinsicContentSize
    {
        CGSize s = [super intrinsicContentSize];
    
        return CGSizeMake(s.width + self.titleEdgeInsets.left + self.titleEdgeInsets.right,
                          s.height + self.titleEdgeInsets.top + self.titleEdgeInsets.bottom);
        
    }
    
现在我们告诉了button，你的contentSize不再是原来那样，而是__原来的内容大小加上文字距离边缘的距离__。效果如下：

![](/Users/joyann/Desktop/文章/iOS碎片知识/4-代码修改自定义Button/3.png)

---

另外，在自定义button的时候，需要设置button的type为custom，否则在修改字体之类的时候不会起作用（？）。

    + (instancetype)button
    {
        return [self buttonWithType:UIButtonTypeCustom];
    }
    - (instancetype)initWithFrame:(CGRect)frame
    {
        self = [super initWithFrame:frame];
        
        if (self) {
            [self setup];
        }
        
        return self;
    }