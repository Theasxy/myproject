# myproject
the final project:
该项目是一个手写数字识别程序,主要内容是将MNIST应用部署到容器里面后，用户通过开放的端口网页提交带有手写体的数字图片，mnsit程序会先将图片识别出来，然后将识别的数字返回给用户。并且对MNIST中用户每次提交的图片、识别的文字和时间戳信息，都会记录到Cassandra以内尽兴存储。    

代码mnist.zip： 
mnist压缩包中包含了images，里面存放的是用于测试的手写数字图片；mnist_backword.py是用于训练mnist模型的python文件；mnist_test是用于测试模型的准确率的；mnist_app.py则实现了上传文件，连接网页端口，识别数字，在数据库中创建表格等功能。

容器:
在训练好模型后将mnist文件夹通过docker build -t mnsit .命令创建为mnist容器即完成了容器的包装。

连接cassandra数据库：
为了使得所创建的mnist容器和cassandra数据库互相连接，以实现将识别结果等数据存放其中的目的，我用了以下的两个命令：   
docker run -d --name mnist -p 4000:8080 mnist；   
docker run -d --name sxy-cassandra --network container:mnist Cassandra

总结报告：   
已存放在github的同一分支下。

实现功能的视频：  
![image](https://github.com/Theasxy/myproject/blob/master/mnist-2019-03-10_06.51.46.mp4)
