## ffmpeg视频处理基本操作

1、从时间xx:xx:xx开始，截取视频中的n张图片：

	ffmpeg -i test.asf -y -f  image2  -ss xx:xx:xx -vframes n  test%d.jpg