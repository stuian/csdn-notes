## Matlab基本操作

### 1、 ###
clc 清屏
clear all; 删除workplace变量
close all; 关掉显示图形窗口


### 2、生成矩阵——一般矩阵 ###

**linspace**

- linspace是Matlab中的一个指令，用于产生指定范围内的指定数量点数，相邻数据跨度相同，并返回一个行向量。
- 调用方法：linspace(x1,x2,N)
- 功能：用于产生x1，x2之间的N点行矢量，相邻数据跨度相同。其中x1、x2、N分别为起始值、终止值、元素个数。若缺省N，默认点数为100。

？三维矩阵怎么生成

    D2=[1,2,3;4,5,6;7,8,9];
    
    D3(:,:,1)=D2;
    
    D3(:,:,2)=2*D2;
    
    D3(:,:,3)=3*D2

？生成复数

    >> x1 = 1;
    >> x2 = 2;
    >> x3 = [x1*i,x1;x2,x2*i*i]
    
    x3 =
    
       0.0000 + 1.0000i   1.0000 + 0.0000i
       2.0000 + 0.0000i  -2.0000 + 0.0000i

ones(),eye(),rand().randn()

> 还有很多特殊矩阵，根本记不住，只能用的时候去查

### 3、矩阵运算 ###

### 4、基本图形绘制 ###

1、
matlab中t=0：pi/50：4*pi是什么意思
> t从0开始，以π/50为一步，到4π为止，就是t的取值为0，π/50,2*π/50，3*π/50，4*π/50......4π，这些

2、
matlab之plot函数
> [https://www.cnblogs.com/haore147/p/3633017.html](https://www.cnblogs.com/haore147/p/3633017.html)

> [subplot](http://blog.csdn.net/steelbasalt/article/details/48918001)是将多个图画到一个平面上的工具。

3、meshgrid

- meshgrid用于从数组a和b产生网格。生成的网格矩阵A和B大小是相同的。它也可以是更高维的。
- [A,B]=Meshgrid(a,b)
- 生成size(b)Xsize(a)大小的矩阵A和B。它相当于a从一行重复增加到size(b)行，把b转置成一列再重复增加到size(a)列。因此命令等效于：
- A=ones(size(b))*a;
- B=b'*ones(size(a))
- 如下所示：

    >> a=[1:2]
    a =
     1 2
    >> b=[3:5]
    b =
     3 4 5
    >> [A,B]=meshgrid(a,b)
    A =
     1 2
     1 2
     1 2
    
    B =
     3 3
     4 4
     5 5

[x,y]=meshgrid(-10:0.2:10) # 生成平面网格

定义数组x,y，x的行向量相当于(-10:0.01:10)，共有n行;y的列向量相当于(-10:0.01:10)，共有n列;n相当于(-10:0.01:10)中的值的数量。

4、hold on，如果你在新画图像之后不想覆盖原图像就要加上[hold on](http://blog.csdn.net/smf0504/article/details/51830963)这句话

5、grid on
> 网格化

6、colormap

> colormap 是用于控制曲面图的颜色。
> 例如: colormap(gray) 输出一个灰色系的曲面图
> 当然你也可以选择其他色系。
> 比如：autumn  spring  summer  winter   jet（默认）  bone  colorcube  cool  flag 等等

7、eps

> MATLAB中eps是一个函数，可以返回某一个数N，的最小浮点数精度，形式例如eps(N)

8、abs(X)求X的绝对值。

9、[mesh](http://blog.csdn.net/kobesdu/article/details/8640648)

10、v=[-10 10 -10 10 -100 100]

11、axis

- axis一般用来设置axes的样式，包括坐标轴范围，可读比例等
- axis([xmin xmax ymin ymax])
- axis([xmin xmax ymin ymax zmin zmax cmin cmax]) 坐标轴设置
- v = axis
- axis auto 
- axis manual
- axis tight
- axis fill
- axis ij
- axis xy
- axis equal
- axis image
- axis square
- axis vis3d
- axis normal 坐标轴刻度比例等
- axis off
- axis on 显示与否
- axis(axes_handles,...)  根据axes设置
- [mode,visibility,direction] = axis('state')  返回当前axes属性

12、hidden on/off

在用mesh画的3维图中，hidden off 是显示被前面图形遮挡的后面图形部分（隐藏关闭）。相反hidden on是不显示后面被遮挡的部分（隐藏打开）。

### 5、简单图像处理 ###

1、roicolor——根据颜色选定区域

BW=roicolor(A,low,high)

BW=roicolor(A,v)

2、im2bw函数

matlab中DIP工具箱函数im2bw使用阈值（threshold）变换法把灰度图像（grayscale image）转换成二值图像。所谓二值图像， 一般意义上是指只有纯黑（0）、纯白（255）两种颜色的图像。 当然， 也可以是其他任意两种颜色的组合。 在matlab命令行中键入doc im2b或help im2bw即可获得该函数的帮助信息。

例子：图像I中每个像素的取值范围是0~255， 设定阈值为0.5， 则图像数据中凡是超过255 * 0.5 = 127.5的都变为255， 否则都变为0。

### 6、建立函数文件 ###

定义函数柄

    >> fun1=@sin;
    >> y1=fun1(pi)
    
    y1 =
    
       1/8165619676597685
    
    >> fun2=@(x,y) (x+y)^2;
    >> y2=fun2(1,2)
    
    y2 =
    
       9   

定义函数文件

    function y =ysw_sum(a,b)
    y = a+b;
    end

### 7、常用数值拟合 ###

1、

- p = polyfit(x,y,n)
- f=polyval(p,x)
- plot出x和f即可

> r=corrcoef(x,y);——求相关系数

2、legend就是添加图例的标注

norm（x,2）—— 2-范数

### 8、常用数据插值 ###

