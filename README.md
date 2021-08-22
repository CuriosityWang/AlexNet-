# AlexNet-
## 文件结构说明
 ![image](https://user-images.githubusercontent.com/50990182/130341660-5ead2bcb-a9eb-4324-9726-4572de0ed07e.png)
## 笔记
由于笔记本的算力限制,我去下载了AlexNet的预训练模型(**由于模型大于100M,文件中未包含,读者可去[官网下载](https://download.pytorch.org/models/alexnet-owt-7be5be79.pth)**)
### 代码复现
#### 测试部分

我找了四张图片对AlexNet进行测试(**类别后面的数字代表概率**)

| ![img](https://img2020.cnblogs.com/blog/1906082/202108/1906082-20210822120956408-449587813.jpg) | ![image-20210822110838640](https://img2020.cnblogs.com/blog/1906082/202108/1906082-20210822120957893-1562028387.png) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![image-20210822110936033](https://img2020.cnblogs.com/blog/1906082/202108/1906082-20210822120956653-227324866.png) | ![image-20210822110946659](https://img2020.cnblogs.com/blog/1906082/202108/1906082-20210822120956448-354444044.png) |

可以看到模型的运行还不错,但是第三张图片把这个阴影的飞机识别成了wing.为此我去观察了,原数据集中的wing图片

#### Kernel可视化

由于第一个conv层的kernel size是 $64 \times 3 \times 11\times 11$因此具有可视化的潜质(其它层的kernel size都太小了)

![image-20210822111535021](https://img2020.cnblogs.com/blog/1906082/202108/1906082-20210822120957889-1136188767.png)

大概可以知道刚开始学习的主要是图片的一些基础的**纹理**和**色彩**特征.

然后以4张图片为例,查看卷积后的图片变成了什么样子.

| 输入size   $3 \times 224\times 224$                          |       | 输出size   $64 \times 55\times 55$                           |
| ------------------------------------------------------------ | ----- | ------------------------------------------------------------ |
| <img src="https://img2020.cnblogs.com/blog/1906082/202108/1906082-20210822120957067-855444717.jpg" alt="tiger cat" style="zoom: 67%;"> | conv1 | <img src="https://img2020.cnblogs.com/blog/1906082/202108/1906082-20210822120956830-2097963035.png" alt="image-20210822112649222" style="zoom:67%;"> |
| <img src="https://img2020.cnblogs.com/blog/1906082/202108/1906082-20210822120956650-954639518.jpg" alt="Golden Retriever from baidu" style="zoom:50%;"> | conv1 | <img src="https://img2020.cnblogs.com/blog/1906082/202108/1906082-20210822120957886-1828421023.png" alt="image-20210822113247735" style="zoom:67%;"> |
| <img src="https://img2020.cnblogs.com/blog/1906082/202108/1906082-20210822120958090-971763010.jpg" alt="airplane2" style="zoom:67%;"> | conv1 | <img src="https://img2020.cnblogs.com/blog/1906082/202108/1906082-20210822120956626-1583169791.png" alt="image-20210822113056113" style="zoom:67%;"> |
| <img src="https://img2020.cnblogs.com/blog/1906082/202108/1906082-20210822120957886-577579072.jpg" alt="airplane" style="zoom:67%;"> | conv1 | <img src="https://img2020.cnblogs.com/blog/1906082/202108/1906082-20210822120956662-2010826238.png" alt="image-20210822113144156" style="zoom:67%;"> |
