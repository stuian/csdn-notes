## python数据分析学习之matplotlib2

### content ###

1. numpy
1. matplotlib
1. scipy
1. pandas
1. scikit-learn
1. keras

> 来源：[https://www.imooc.com/learn/843](https://www.imooc.com/learn/843)

官网：matplotlib.org

1、散点图

    import numpy as np 
    import matplotlib.pyplot as plt
    
    def main():
    	#scatter
    	fig=plt.figure()
    	fig.add_subplot(3,3,1)
    	n=128
    	X=np.random.normal(0,1,n)
    	Y=np.random.normal(0,1,n)
    	T=np.arctan2(Y,X)
    	# T是用来上色的
    	plt.axes([0.025,0.025,0.95,0.95])
    	#显示范围
    	plt.scatter(X,Y,s=75,c=T,alpha=.5)
    	#s代表大小，c是颜色
    	plt.xlim(-1.5,1.5),plt.xticks([])
    	plt.ylim(-1.5,1.5),plt.yticks([])
    	plt.axis()
    	plt.title("scatter")
    	plt.show()
    
    
    if __name__ == "__main__":
    	main()

> 让散点图处理子图(3，3，1)位置

	ax=fig.add_subplot(3,3,1)

	ax.scatter(X,Y,s=75,c=T,alpha=.5)

2、柱状图

    fig.add_subplot(332)
    	n=10
    	X=np.arange(n)
    	Y1=(1-X/float(n))*np.random.uniform(0.5,1.0,n)
    	Y2=(1-X/float(n))*np.random.uniform(0.5,1.0,n)
    
    	plt.bar(X,+Y1,facecolor='#9999ff',edgecolor='white')
    	plt.bar(X,-Y2,facecolor='#ff9999',edgecolor='white')
		#加注释
    	for x,y in zip(X,Y1):
    		plt.text(x + 0.4,y+0.05,'%.2f' % y,ha='center',va='bottom')
    	for x,y in zip(X,Y2):
    		plt.text(x + 0.4,-y-0.05,'%.2f' % y,ha='center',va='bottom')

3、扇形图

    #Pie
    	fig.add_subplot(333)
    	n = 20
    	Z = np.ones(n)
    	Z[-1] *= 2
    	# 最后一个值设为2
    	plt.pie(Z,explode=Z * .05,colors=['%f' % (i/float(n)) for i in range(n)],
    		labels=['%.2f' % (i/float(n)) for i in range(n)])
    	# explode代表每一个扇形面积距离中心点的位置，color使用的是灰度图，labels是打印灰度的数值
    	plt.gca().set_aspect('equal')
    	# 正圆的扇形
    	plt.xticks([]),plt.yticks([])

4、雷达图

    #polar
	fig.add_subplot(334)
	theta = np.arange(0.0,2*np.pi,2*np.pi/n)
	#0-2pi，间隔是2pi/n
	radii = 10*np.random.rand(n)
	# 半径
	plt.polar(theta,radii)

5、热图

    fig.add_subplot(335)
    	from matplotlib import cm
    	# 用来上色
    	data = np.random.rand(3,3)
    	cmap = cm.Blues
    	map = plt.imshow(data,interpolation='nearest',cmap=cmap,aspect='auto',vmin=0,vmax=1)
    	# interpolation指插值，vmin=0指为白色，vmax这里指蓝色

6、3D图

	from mpl_toolkits.mplot3d import Axes3D
	ax = fig.add_subplot(336,projection="3d")
	ax.scatter(1,1,3,s=100)

7、热力图

    fig.add_subplot(313)
    	# 第三行第一列到第二列
    	def f(x,y):
    		return (1-x/2+x**5+y**3)*np.exp(-x **2 -y**2)
    	n = 256
    	x = np.linspace(-3,3,n)
    	y = np.linspace(-3,3,n)
    	X,Y = np.meshgrid(x,y)
    	plt.contourf(X,Y,f(X,Y),8,alpha=.75,camp=plt.cm.hot)
    	plt.savefig("./data/fig.png")