# Metric Learning for Person Re-identification
Implementation of a Siamese Neural Network (in Tensorflow) that defines a similarity score between a pair of person images.

## Installation

```
pip3 install -r requirements.txt
```

## Preprocess Dataset

Download the MARS dataset from here:
* [MARS](https://drive.google.com/drive/folders/0B6tjyrV1YrHeMVV2UFFXQld6X1E?amp%3Busp=sharing) 

- The link contains both training and test set in a zip format. Extract both and create some directories first:
THE TWO FOLDERS should be named training_dataset and testing_dataset !!

```plain
└── MARS_DATASET_ROOT
       ├── training_dataset    
       |   ├── 0001
       |        ....jpg
       |        ....jpg
       |
       └── testing_dataset     
           ├── 0000 
                ....jpg
                ....jpg

```

Create a training and validation set for your dataset: (This is done by generating a TFRecord file for TensorFlow consumption)

```
python3 create_tf_record.py --tfrecord_filename=mars --dataset_dir=/path/to/MARS_DATASET_ROOT
```

## Training the Siamese Network

Creates a TFRecord file and then train the model on the generated TFRecord file :
```
python3 train_net.py /path/to/train_dataset/
```
Using TensorBoard, you can see the updates (There are also stored in `./train.log/`).

In a terminal (Ubuntu user) run :
```
tensorboard --logdir /path/to/train.log/
```

## Testing the Siamese Network

```
python3 test_net.py /image_1_path /image_2_path
```

This will output a similiraty score between the two images  