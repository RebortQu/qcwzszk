# windows下gitHub图片不显示

上传到github的图片在浏览器中不显示
![](resources/nonePic.PNG)

## 解决
打开`C:\Windows\System32\drivers\etc\hosts`文件,在文件尾部插入

```
# GitHub Start 
#图片
151.101.184.133    raw.githubusercontent.com
 # GitHub End
```

保存、关闭，如果不好使就刷新一会网页就好使。



