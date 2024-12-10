#steps for collective minds

sudo apt update -y
sudo apt install -y python3 python3-pip python3-venv git git-lfs wget curl

export HOME=$PWD

python3 -m venv cm
source cm/bin/activate

python3 -m pip install cmind -U

export CM_REPOS="$HOME/CM"

cm init --repo=mlcommons@cm4mlops --branch=mlperf-inference

git clone https://github.com/mlcommons/ck

export CM_HOME="$PWD/ck/cm/cmind"

cm reindex repo
cm test core

#run.sh script
cm run script --tags=run-mlperf,inference,_r4.1-dev,_all-modes,_performance-only,_short  \
   --division=open \
   --category=edge \
   --device=cpu \
   --model=resnet \
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
