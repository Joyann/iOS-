修改UITableView的背景图片。

1.图片显示为'PatternImage'模式。

    // viewDidLoad

    self.tableView.backgroundColor = [UIColor colorWithPatternImage:[UIImage imageNamed:@"BackgroundImage"]];

    // cellForRowAtIndexPath

    cell.backgroundColor = [UIColor clearColor];

这种情况下背景图片像地板砖一样平铺。拉动tableView背景图片会随着动，若行数超过背景图片的高度，会接着显示下一张图片。

2.正常的背景图片。

    // viewDidLoad

    self.tableView.backgroundColor= [UIColor clearColor];

    UIImageView*imageView = [[UIImageView alloc]initWithImage:[UIImageimage Named:@"BackgroundImage"]];

    self.tableView.backgroundView = imageView;

    // cellForRowAtIndexPath

    cell.backgroundColor = [UIColor clearColor];

这种情况下背景图片不会动，即无论多少行看到的都是同样的背景。