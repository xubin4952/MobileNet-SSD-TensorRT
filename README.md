# MobileNet-SSD-TensorRT
**To accelerate mobileNet-ssd with tensorRT**

**TensorRT-Mobilenet-SSD can run 50fps on jetson tx2**

---

**Requierments:**

1.tensorRT4

2.cudnn7

3.opencv

---

**Run:**

```shell
cmake .
make
./build/bin/mobileNet
```

---

**Reference:**

https://github.com/saikumarGadde/tensorrt-ssd-easy

https://github.com/chuanqi305/MobileNet-SSD

I replaced depthwise with group_conv,because group_conv  has been optimized in cudnn7

I retrianed mobileNet-SSD,my number of classfication is 5

---

**TODO:**

- [x] To save serialized model 
- [x] To solve the bug of getting different result with same input
- [ ] The bottleneck of time cost lies in the decoding of pictures. "imread" cost too much ,to resolve it.
- [x] To modify the architecture, decrease the time cost



*If want to decrease the time cost of "imread",you could rebuild OpenCV[https://github.com/jetsonhacks/buildOpenCVTX2]*

*Added producer-consumer*



**The bug has been fixed**

![image](testPic/test1.png)


# Jetson nano compiler
# you can not use:
mkdir build 
then cmake .. 

this will have some problem


# 1.fatal error: cblas.h: No such file or directory

sudo apt-get install libopenblas-dev

# 2.fatal error: glog/logging.h: No such file or directory

sudo apt-get install libgoogle-glog-dev

# 3./MobileNet-SSD-TensorRT/tensorNet.h:21:10: error: ‘vector’ in namespace ‘std’ does not name a template type
     std::vector<Record> mProfile;


tensorNet.h   add :#include <vector>
  
  
 # 4.complete the compiler
 
# 5.when we execute the program :  Segmentation fault (core dumped)

rm MobileNetSSD_deploy.caffemodel.1.tensorcache






