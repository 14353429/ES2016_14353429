

## DOL实例分析&编程

### 一、 实验内容

1. EXAMPLE1：

    ![EXAMPLE1](https://github.com/14353429/ES2016_14353429/blob/master/image/EXAMPLE1.png)

   在square.c中修改的部分就是``i = i * i * i``，即变成三次方。

2. EXAMPLE2：

    ![EXAMPLE2](https://github.com/14353429/ES2016_14353429/blob/master/image/EXAMPLE2.png)

   原本中间有3个square模块，可以从example2.xml文件中看到，是一个循环来定义的：

   ```xml
   <iterator variable="i" range="N">
     <process name="square">
           <append function="i"/>
           <port type="input" name="0"/>
           <port type="output" name="1"/>
           <source type="c" location="square.c"/>
     </process>
   </iterator>
   ```

   所以只需要改变这个循环的次数就能变成2个square模块，将N变成2：

   ```xml
   <variable value="2" name="N"/>
   ```

   ### 二、 实验感想

   实验很简单，只要懂这个原理，明白生产者到消费者中间这条路是怎么走过去的就可以了。
