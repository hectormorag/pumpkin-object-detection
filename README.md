# Object Detection Using RCNN On Halloween Pumpkins 

On this repository I present the results and source code for a grad school project to detect halloween pumpkins usin RCNN using the pretrained COCO weights. This project implements the code found on the project "Mask R-CNN for Object Detection and Segmentation" to achieve the final goal, training on a set of my own images. The labelling was done using the labelling tool of the VGG Oxford group. This is an example of how the model can be used. 

![This blog post](https://github.com/hectormorag/pumpkin-object-detection/blob/main/samples/balloon/PumpkinVideo.gif) 

![This blog post](https://github.com/hectormorag/pumpkin-object-detection/blob/main/images/screenshot.jpg) 





## Installation
From this repository:
1. Download `mask_rcnn_pumpkin.h5`. Save it in the root directory of the repo (the `mask_rcnn` directory).
2. Download `pumpkin_dataset.zip`. Expand it such that it's in the path `mask_rcnn/datasets/pumpkin/`.

## Apply color splash using the provided weights
Apply splash effect on an image:

```bash
python pumpkin.py splash --weights=/path/to/mask_rcnn/mask_rcnn_pumpkin.h5 --image=<file name or URL>
```

Apply splash effect on a video. Requires OpenCV 3.2+:

```bash
python pumpkin.py splash --weights=/path/to/mask_rcnn/mask_rcnn_pumkin.h5 --video=<file name or URL>
```


## Run Jupyter notebooks
Open the `inspect_pumpkin_data.ipynb` or `inspect_pumpkin_model.ipynb` Jupter notebooks. You can use these notebooks to explore the dataset and run through the detection pipelie step by step.

## Train the Pumpkin model

Train a new model starting from pre-trained COCO weights
```
python pumpkin.py train --dataset=/path/to/pumpkin/dataset --weights=coco
```

Resume training a model that you had trained earlier
```
python pumkin.py train --dataset=/path/to/pumpkin/dataset --weights=last
```

Train a new model starting from ImageNet weights
```
python pumpkin.py train --dataset=/path/to/balloon/dataset --weights=imagenet
```

## Parameters

The code in `pumpkin.py` is set to train for 3K steps (30 epochs of 100 steps each), and using a batch size of 2. 
Update the schedule to fit your needs.

## Evaluation

This section shows the inner process of how the network does the ROI segmentation by showing some examples of the masking done on different regions of pixels inside the images in order to show the performance of our model. 
