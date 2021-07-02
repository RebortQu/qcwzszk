# gitignore无效

gitignore提交后并未忽略文件

## 解决
在git Base分别执行以下命令
```cmd
 git rm -r --cached .
git add .
git commit -m 'update .gitignore'
```
