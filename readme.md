界面是在*ultralytics*的[yolov5](https://github.com/ultralytics/yolov5)基础上建立的，界面使用*pyqt5*实现，内容较简单，娱乐而已。

**功能：**

1. 模型选择
2. 本地文件选择
3. 开关摄像头
4. 运行/终止
5. 统计检测结果

![新建 Microsoft Visio 绘图](D:\project\deeplearning\project\pytorch\objectdection\yolov5-master\笔记\新建 Microsoft Visio 绘图.jpg)
默认模型为*yolov5s.pt*，默认输入文件为电脑摄像头视频

使用视频：
[https://www.bilibili.com/video/BV1sQ4y1C7Vk?spm_id_from=333.999.0.0](https://www.bilibili.com/video/BV1sQ4y1C7Vk?spm_id_from=333.999.0.0)

摄像头检测画面：

![无标题](D:\project\deeplearning\project\pytorch\objectdection\yolov5-master\笔记\无标题.jpg)

本地视频检测画面：
![20210927_141438_Trim 00_00_00-00_00_30~1](D:\FFOutput\20210927_141438_Trim 00_00_00-00_00_30~1.gif)

图片检测画面：
![无标题2](D:\project\deeplearning\project\pytorch\objectdection\yolov5-master\笔记\无标题2.jpg)


## 要做的事

**一.** 将*yolov5*的*utils/datasets.py*中*LoadWebcam*类中*__ next __*的返回值改为

```python
return img_path, img, img0, self.cap #（位置在270行上下）。
```

**二.** 为了避免中文路径报错（路径不包含中文可以忽略这一步），将*utils/datasets.py*中*LoadImages*类中的

```python
img0 = cv2.imread(path)	#（位置在212行上下）。
```

改为

```python
img0 = cv2.imdecode(np.fromfile(path, dtype=np.uint8), 1)
```

**三.** 在*yolov5-master*根目录下创建*main_ui.py、yolo_win.py*和*icon*文件夹（存放图标）。

运行*yolo_win.py*即可开启检测界面。

存在的一个小问题，切换模型或者文件**过于频繁**，可能会卡住，重启一下即可。这种情况很少出现，问题不大。
