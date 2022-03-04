# pygame

## 最小开发框架

```python
import pygame,sys #sys是python的标准库，提供Python运行时环境变量的操控

pygame.init()  #内部各功能模块进行初始化创建及变量设置，默认调用
size = width,height = 800,600  #设置游戏窗口大小，分别是宽度和高度
screen = pygame.display.set_mode(size)  #初始化显示窗口
pygame.display.set_caption("小游戏程序")  #设置显示窗口的标题内容，是一个字符串类型
while True:  #无限循环，直到Python运行时退出结束
    for event in pygame.event.get():  #从Pygame的事件队列中取出事件，并从队列中删除该事件
        if event.type == pygame.QUIT:  #获得事件类型，并逐类响应
            sys.exit()   #用于退出结束游戏并退出          
    pygame.display.update()  #对显示窗口进行更新，默认窗口全部重绘

```



## 常用知识

pygame默认是采用的笛卡尔坐标系。左上角的顶点是(0,0)