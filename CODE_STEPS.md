#steps for collective minds
```bash
sudo apt update -y
sudo apt install -y python3 python3-pip python3-venv git git-lfs wget curl
```
```bash
export HOME=$PWD
```
```bash
python3 -m venv cm
source cm/bin/activate
```
```bash
python3 -m pip install cmind -U
```
```bash
export CM_REPOS="$HOME/CM"
```
```bash
cm init --repo=mlcommons@cm4mlops --branch=mlperf-inference
```
```bash
git clone https://github.com/mlcommons/ck
```
```bash
export CM_HOME="$PWD/ck/cm/cmind"
```

```bash
cm reindex repo
cm test core
```


```bash
#run.sh script for resnet-50model used for image-classification from ImageNet dataset
cm run script --tags=run-mlperf,inference,_r4.1-dev,_all-modes,_performance-only,_short  \
   --division=open \
   --category=edge \
   --device=cpu \
   --model=resnet-50 \
   --precision=float32 \
   --implementation=mlcommons-python \
   --backend=onnxruntime \
   --scenario=Offline \
   --mode=accuracy \
   --execution_mode=test \
   --power=no \
   --adr.python.version_min=3.8 \
   --clean \
   --compliance=no \
   --quiet \
   --time
```
![Alt text](https://github.com/SHASHANKTM7/COLLECTIVE_MINDS/blob/main/result%20of%20benchmarking.png)

```bash
#script for running retina-model for object detection with CPU device and dataset used in open image
cm run script --tags=run-mlperf,inference,_r4.1-dev,_all-modes,_submission,_short  \
   --division=open \
   --category=edge \
   --device=cpu \
   --model=retinanet \
   --precision=float32 \
   --implementation=mlcommons-python \
   --backend=onnxruntime \
   --scenario=Offline \
   --mode=accuracy \
   --execution_mode=test \
   --power=no \
   --adr.python.version_min=3.8 \
   --clean \
   --compliance=no \
   --quiet \
   --time
   ```
![Alt text](https://github.com/SHASHANKTM7/COLLECTIVE_MINDS/blob/main/retina_net%20model%20_object_detection.png)





