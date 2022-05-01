# YoloV5 annotations.

<div align="justify">
Every image in training test and validation sets has a corresponding .txt file with the same name as the image containing the bounding box properties of all the image's instances. Each row of the .txt file has five variables which are the class id and the four bounding box properties (class x_center y_center width height). The classes are zero-indexed and the geometric properties of the bounding boxes are normalized based on image's dimensions in order to be elements of [0, 1]. All the annotational files of every set must be in the same folder namely "labels" and the corresponding images of the set have to be in the same directory but in another file named "images". The overall folder stucture of the datasets must be as is shown below. The folder structure below with all the dataset images and their annotations can be downloaded from [HERE]
    
</div align="justify">

## Yolo dataset folder structure.
```
├───train
│   ├────images
│   │    ├───image_name_1.jpg
│   │    ├───       ⋮ 
│   │    └───image_name_3461.jpg
│   └────labels
│        ├───image_name_1.txt
│        ├───       ⋮
│        └───image_name_3461.txt
├───test
│   ├────images
│   │    ├───image_name_1.jpg
│   │    ├───       ⋮ 
│   │    └───image_name_1961.jpg
│   └────labels
│        ├───image_name_1.txt
│        ├───       ⋮
│        └───image_name_1961.txt
└───val
    ├────images
    │    ├───image_name_1.jpg
    │    ├───       ⋮ 
    │    └───image_name_256.jpg
    └────labels
         ├───image_name_1.txt
         ├───       ⋮ 
         └───image_name_256.txt
```

## Example:
| P0080_600_1400_4800_5600.jpg | P0080_600_1400_4800_5600.txt | 
|:----------------------------:|:----------------------------:|
|<img src="https://user-images.githubusercontent.com/74200033/166140021-69d165ea-8302-4703-9c8e-41c70587d2e2.jpg" width="500"/> |<img src="https://user-images.githubusercontent.com/74200033/166140238-385aa85e-ac03-496f-9f30-98d3c5b0d5f7.png" width="500"/>|

