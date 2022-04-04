# os笔记

**open()函数**

语法：file = open('地址','读取方式')

操作完成后调用close()方法关闭该文件



**read()和readline()方法**

read()方法返回整个字符串，包含文件中的所有内容。而readline()将内容以换行符\n为分割标志，将文件内容放入列表中，每个元素都为字符串，含有一行的内容。

```python
content = file.read()
print(type(content))
print(content)
'''
输出：
<class 'str'>
BKM5001,绿毛虫,lvmaochong@bkm.com
BKM5002,宝石海星,baoshihaixing@bkm.com
BKM5003,袋兽,daishou@bkm.com
...
'''

content = file.readlines()
print(type(content))
print(content)
'''
输出：
<class 'list'>
['BKM5001,绿毛虫,lvmaochong@bkm.com\n',
'BKM5002,宝石海星,baoshihaixing@bkm.com\n',
'BKM5003,袋兽,daishou@bkm.com\n',
...]
'''
```



