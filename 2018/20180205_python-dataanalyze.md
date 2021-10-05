## python数据分析学习之matplotlib1

### content ###

1. numpy
1. matplotlib
1. scipy
1. pandas
1. scikit-learn
1. keras

> 来源：[https://www.imooc.com/learn/843](https://www.imooc.com/learn/843)

官网：matplotlib.org

## plot折线图 ##

1、引入：

    import matplotlib.pyplot as plt

2、sin和cos图

    import numpy as np 
    import matplotlib.pyplot as plt
    
    def main():
    	#line
    	x=np.linspace(-np.pi,np.pi,256,endpoint=True)
    	# 定义-pi到pi之间有256个点，且包含最后一个点
    	c,s=np.cos(x),np.sin(x)
    	plt.figure(1)
    	plt.plot(x,c)
    	plt.plot(x,s)
    	#括号里的是自变量和因变量
    	plt.show()
    
    if __name__ == "__main__":
    	main()

3、在前面的基础上，定义线的一些属性

    plt.plot(x,c,color="blue",linewidth=1.0,linestyle="-",label="cos",alpha=0.4)#alpha是透明度
	plt.plot(x,s,"r*",label="sin")

> plt.title("cos & sin") —— 加标题

4、设置坐标轴的位置（让左边和下面的坐标轴交于（0，0）点），让右边和上边的坐标轴消失

	ax=plt.gca()
	ax.spines["right"].set_color("none")
	ax.spines["top"].set_color("none")
	ax.spines["left"].set_position(("data",0))
	ax.spines["bottom"].set_position(("data",0))

> spines指的是轴线

5、设置下x，y的数据位于轴线的位置

	ax.xaxis.set_ticks_position("bottom")
	ax.yaxis.set_ticks_position("left")

6、设置x，y轴上的数值范围

	plt.xticks([-np.pi,-np.pi/2,0,np.pi/2,np.pi],
		[r'$-\pi$',r'$-\pi/2$',r'$0$',r'$+\pi/2$',r'$+\pi$'])
	plt.yticks(np.linspace(-1,1,5,endpoint=True))

7、坐标轴数值的属性设置

	for label in ax.get_xticklabels()+ax.get_yticklabels():
		label.set_fontsize(16)
		label.set_bbox(dict(facecolor="white",edgecolor="None",alpha=0.2))

> 每个数值都有一个“盒子”装起来一样

8、添加图例和网格线

	plt.legend(loc="upper left")
	plt.grid()

9、选择显示范围

	plt.axis([-1,1,-0.5,1])

10、填充颜色和在图中画线

	plt.fill_between(x,np.abs(x)<0.5,c,c>0.5,color="green",alpha=0.25)

	# 画线
	t=1
	plt.plot([t,t],[0,np.cos(t)],"y",linewidth=3,linestyle="--")

11、在图中加注释“cos（1）”

	plt.annotate("cos(1)",xy=(t,np.cos(1)),xycoords="data",xytext=(+10,+30),
		textcoords="offset points",arrowprops=dict(arrowstyle="->",connectionstyle="arc3,rad=.2"))