## **System Setup & Environment Used**

This project was developed and tested using the following environment:

### **Operating System**
- Ubuntu 18.04 (aarch64)  
- NVIDIA L4T 32.7  
- JetPack 4.6.4

### **AI and Vision Frameworks**
- DeepStream 6.0.1 
- Python 3.6

### **Hardware**
- EPC-r7000 (advantech)
- NVIDIA Jetson TX2
- USB Webcam

### **GPU / Compute Stack**
- CUDA 10.2
- TensorRT 8.2 
- cuDNN 8.2

---

For this inference example, we use YOLOv3 (Darknet).
The inference runs on the EPC's NVIDIA GPU, using an environment compatible with JetPack 4.6.

It's important to remember that, in JetPack 4.6, many modern frameworks (PyTorch, YOLOv8, etc.) do not have compatible versions for the aarch64 architecture, so we use Darknet, which is fully compatible and allows us to take advantage of CUDA acceleration.

## **Quick Start**

---

### **1. Install dependencies (all supported in JP4.6)**
```bash
sudo apt update
sudo apt install -y git make build-essential libopencv-dev

```

---

### **2. Download Darknet**
```bash
git clone https://github.com/AlexeyAB/darknet
cd darknet

```

---

### **3. Enable CUDA to use the GPU.**
```bash
sed -i 's/GPU=0/GPU=1/' Makefile
sed -i 's/CUDNN=0/CUDNN=1/' Makefile
sed -i 's/OPENCV=0/OPENCV=1/' Makefile

```

---

### **4. Compile**
```bash
make -j4

```

---

### **5. Download the YOLO-tiny template (very lightweight and works on JP4.6)**
```bash
wget https://raw.githubusercontent.com/pjreddie/darknet/master/cfg/yolov3-tiny.cfg
wget https://pjreddie.com/media/files/yolov3-tiny.weights

```

---

### **6. Run detection via WEBCAM (/dev/video0)**
```bash
./darknet detector demo cfg/coco.data cfg/yolov3-tiny.cfg yolov3-tiny.weights /dev/video0

```

---

### **7. Verify GPU usage**
```bash
jtop
```

## YOLOv3 running with NVIDIA GPU acceleration (monitored via jtop).
![demo2](https://github.com/user-attachments/assets/0f03891e-12f3-4455-8b75-8c881eaed2b0)
![demo](https://github.com/user-attachments/assets/51feac2b-42d2-4ef8-822a-bd5af9e4fd9e)


