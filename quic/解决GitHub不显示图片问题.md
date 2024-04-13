# 解决GitHub不显示图片问题

>文章来自: https://blog.csdn.net/SL1029_/article/details/128601905

刚开始使用github时很多时候会碰到图片不显示的问题以下为解决方法。

不显示图片原因：一般是因为DNS无法解析到图片外链地址的ip地址

解决方法：很简单,我们可以通过外国的ip地址测试找到该域名具体对应的ip地址,之后手动地加到我们本机的host文件中(相当于DNS映射)

## 具体步骤

* 检查域名

我们可以右键点中不能显示的图片，点击检查，点击控制台，可以看到failed to load 字样，后面就是没有显示出来的图片地址(我这里是)：https://raw.githubusercontent.com/ivanzz1001/micro-service-learning/master/online-article-collection/image/4165417baea04f209353008a1dd712e1.png

这里我们查找: raw.githubusercontent.com

* 查找域名对应的IP

访问https://www.ipaddress.com/ ，在页面输入刚刚找到的域名：raw.githubusercontent.com

>ps: 这里我们访问该网站来查找域名https://site.ip138.com/


* 修改hosts文件

找到本机hosts文件，一般路径地址为：C:\Windows\System32\drivers\etc\hosts

打开hosts修改，将上面对应的IP和域名放到hosts文件末尾:

```
185.199.108.133   raw.githubusercontent.com
185.199.109.133   raw.githubusercontent.com
185.199.110.133   raw.githubusercontent.com
185.199.111.133   raw.githubusercontent.com
2606：50c0:8000::154 raw.githubusercontent.com
2606：50c0:8001::154 raw.githubusercontent.com
2606：50c0:8002::154 raw.githubusercontent.com
2606：50c0:8003::154 raw.githubusercontent.com
```

添加完此映射关系之后，可以使用这个命令刷新下本地的DNS缓存：ipconfig/flush，打开CMD，输入 ipconfig/flushdns 即可。