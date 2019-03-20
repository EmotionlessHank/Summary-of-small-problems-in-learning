### 解决mac上pyspider安装问题
搞了一天pyspider的安装，安装一键搞定
```
pip install pyspider
```
但是，验证安装
```
pyspider all
```
就出岔子了，
```
invalid sysntax
```
上网查阅了很多文章，不同的错误类型，我这个问题基本就是python版本的问题。python3.7 中把'async'添加到关键字里了，所以解决这个问题，就得把有'async'的文件全部修改。

#### 问题文件
```
/anaconda3/lib/python3.7/site-packages/pyspider/run.py

/anaconda3/lib/python3.7/site-packages/pyspider/fetcher/tornado_fetcher.py

/anaconda3/lib/python3.7/site-packages/pyspider/webui/app.py
```
文件路径各有不同，按自己的路径来查找

我的方法很笨（其实我也尝试使用vim的方法来进行修改，但是总是出现'file not found' 的情况，遂放弃，以后有时间专门学习vim的用法），就是把文件打开分别修改，用全局搜索找到'async'然后改成'async_'(怕改错了记不住改了啥就改成这个吧)，全部修改然后保存。

再次键入
``` 
pyspider all
``` 
运行成功，大功告成！！！