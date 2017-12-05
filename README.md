# SLR Alphabet Recognizer

This project is a sign language alphabet recognizer using Python, openCV and tensorflow for training InceptionV3 model, a convolutional neural network model for classification.

The framework used for the CNN implementation can be found here:

[Simple transfer learning with an Inception V3 architecture model](https://github.com/xuetsing/image-classification-tensorflow) by xuetsing

The project contains the dataset (1Go). If you are only interested in code, you better copy/paste the few files than cloning the entire project.

You can [find the demo here](https://youtu.be/kBw-xGEIYhY)

[![Demo](http://img.youtube.com/vi/kBw-xGEIYhY/0.jpg)](http://www.youtube.com/watch?v=kBw-xGEIYhY)

## Requirements

This project uses python 3.5 and the PIP following packages:
* opencv
* tensorflow
* matplotlib
* numpy

See requirements.txt and Dockerfile for versions and required APT packages

### Using Docker
```
docker build -t hands-classifier .
docker run -it hands-classifier bash
```
### Install using PIP

Enable virtual env.

```
$ virtualenv -p /usr/bin/python3 env

$ source env/bin/activate
```

Install dependencies

```
$ pip install -r requirements.txt
```

### Setup opencv

Please follow the instructions for install opencv from sources. 

After the installation of opencv make a symlink in:

```
$ cd env/lib/python3.5/site-packages/
$ ln -s /usr/local/lib/python3.5/site-packages/cv2.cpython-35m-x86_64-linux-gnu.so cv2.so
```

## Training

To train the model, use the following command (see framework github link for more command options):
```
python train.py \
  --bottleneck_dir=trainedset/bottlenecks \
  --how_many_training_steps=2000 \
  --model_dir=inception \
  --summaries_dir=trainedset/training_summaries/basic \
  --output_graph=trainedset/trained_graph.pb \
  --output_labels=trainedset/trained_labels.txt \
  --image_dir=./dataset
```
If you're using the provided dataset, it may take up to three hours.
  
## Classifying
  
To test classification, use the following command:
```
python3 classify.py path/to/image.jpg
```

## Using webcam (demo)

To use webcam, use the following command:
```
$ python classify_webcam.py
```
Your hand must be inside the rectangle. Keep position to write word, see demo for deletions.
