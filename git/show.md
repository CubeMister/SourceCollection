# show命令

## 查看某次提交的详细信息

首先执行：`git log`，找到那次提交的`commit id`，然后执行`git show [commit_id]`，例如:

```
> git log -1

commit 3109f44dcbc68f0525ca1ad3f3bd14ae64eb4a7b
Author: CubeMister <cube.mister.mail@gmail.com>
Date:   Sun Jan 1 17:15:53 2017 +0800

    [add]

> git show 3109f44dcb
```

> 只需要拷贝commit_id的开头一部分即可
