# stash命令

## 保存改动点
`git stash`

## 把上次保存在本地的改动点找回
`git stash apply`

## 找回第1个
`git stash pop`

## 查看所有保存的版本
`git stash list`

## 删除stash
`git stash drop [stash@{0}]`
执行命令：`git stash drop`默认删除第一个stash

## 删除所有的stash
`git stash clear`

## 查看某个stash的详情
`gitk stash@{0}`

## 可以将你指定版本号为stash@{1}的改动点取出来
`git stash apply stash@{1}`

## git stash apply与git stash pop的区别

`git stash apply`只是把栈里面记录的内容运用到当前的版本上，这时候栈里面的记录还保存着。
`git stash pop`也是把栈里面记录的内容运用到当前的版本上，但是它会把出栈的记录删掉，也就是说如果之前栈里面有3个记录，当执行`git stash pop`之后，栈里的记录变成2个，这就是pop（出栈）的特点。

`git stash clear`如果误删之后，就可以执行命令: `git fsck --lost-found`，然后使用`git show commitid`来查看是否是自己想要的，如果是，则可以执行`git merge commitid`进行恢复
