#presentedViewController和presentingViewController的区别

presentedViewController是指 ** presented by this view controller(modally) **

presentingViewController是指 ** presented this view controller(modally) **

所以通常viewControllerA ---(modally)--> viewControllerB, 设置A = B.delegate, 想要在A中使得B消失，则用

    [self.presentedViewController dismissViewControllerAnimated:YES completion:nil];

另外，push对应的是pop。比如：

    [self.navigationController popViewControllerAnimated:YES];
    
而modal对应的是dismiss,如第一个例子。