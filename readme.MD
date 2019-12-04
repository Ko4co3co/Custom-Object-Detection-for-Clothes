# Custom Clothes Dataset Object Detection with Tensorflow API
Custom Clothes Dataset Object Detection is using Tensorflow Object Detection API 


## Installation 
-   Setup a Conda environment and install prerequsitie python package
``` 
conda create -n tensorflow
conda activate tensorflow 
conda install tensorflow=1.14 pandas opencv
git clone https://github.com/tensorflow/models
```
- Adapt Protobuf 

``` 
# Ubuntu 18.04 
sudo apt-get install wget
mkdir protoc_3.0 
wget -O https://github.com/google/protobuf/releases/download/v3.0.0/protoc-3.0.0-linux-x86_64.zip
unzip protoc-3.0.0-linux-x86_64.zip.
cd ..
./protoc_3.0/bin/protoc object_detection/protos/*.proto --python_out=.
export PYTHONPATH=$PYTHONPATH:`pwd`:`pwd`/slim
python setup.py build
python setup.py install

python object_detection/builders/model_builder_test.py

```
## How to Using 
1. Custom images and bbox label
2. Make Label CSV File
3. Make TFRecord Format Label File
4. Modify Config File 
5. Train the Model 

### Make TFRecord 
``` 
python ./util/generate_tfrecord.py --csv_input=../label/train_labels.csv --image_dir=../images --output_path=../record/train.record
```
### Using Tensorflow Trainer 
```
# Move TF Model Directory 
cd model/research/object_detection/legacy/train.py --pipeline_config_path=[YOUR_DIR]/config/ssd_mobilenet_v1.config --train_dir=[your output dir] 
```