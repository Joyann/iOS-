##设置statusBar,navigationBar,tabBar的颜色

    //AppDelegate.m
    //设置navigationBarColor
    
    [[UINavigationBar appearance] setTranslucent:YES];
    [[UINavigationBar appearance] setBarTintColor:[UIColor colorWithRed:128/255.0f green:128/255.0f blue:128/255.0f alpha:1.0]];
    
    
    // 设置tabBarColor
    [[UITabBar appearance] setTranslucent:NO];
    [[UITabBar appearance] setBarTintColor:[UIColor colorWithRed:128/255.0f green:128/255.0f blue:128/255.0f alpha:1.0]];
    
    // 设置status文字颜色
    
    [[UIApplication sharedApplication] setStatusBarHidden:NO];
    [[UIApplication sharedApplication] setStatusBarStyle:UIStatusBarStyleLightContent];
    
此外，需要在.plist文件增加一行:

> View controller-based status bar appearance = NO 

表示viewController不对status bar进行操作。



    
