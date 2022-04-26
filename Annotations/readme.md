## Validation Set Creation

<div align="justify">
The validation set was set equal to 5% of the total training images. The distributions of validation dataset must have the required similarity with the corresponding ones from the original training set for each variable (xc, yc, aspect_ratio=h/w, area=h・w) in instance level. Because the split of the training dataset to new training and validation sets must be done on image level, we assume that each image contains only one imaginary instance whose geometric properties are derived from the mean values of the variables of all the actual image instances. In combination with the above, in the set of geometric properties of each image are added 2 variables regarding the number of examples it contains, as well as whether it depicts land sections, composing a group of a 6 variables (xc, yc, aspect_ratio, area, number_of_instances, Inshore_label ∈ {0,1}).


### Validation set extraction algorithm:

 * To extract the validation set, the training data is divided into 15 groups based on the given image IDs which contain the same number of images.
 * Then the groups that have each one of the mean values close to the original ones for every variable (xc<sup>mean</sup>, yc<sup>mean</sup>, aspect_ratio<sup>mean</sup>, area<sup>mean</sup>, number_of_instances, Inshore_label) simultaneously, were selected. 
 * Finally, an iterative algorithm samples images from the above groups and tries to create the desired distribution of every variable as a mixture of a distribution that resembles the original distribution and of another distribution that tends to be more random.

</div align="justify">

### Validation Set Distributions:

<div align="center">
  
#### Parameter Distributions - Normal Bounding Boxes
  
#### Parameter Distributions - Rotated Bounding Boxes
  
#### Object Sizes - Normal Bounding Boxes  

#### Object Sizes - Rotated Bounding Boxes
  
#### Spatial Distributions - Normal Bounding Boxes  
  
#### Spatial Distributions - Rotated Bounding Boxes  
  
</div align="center">


## Rotated Bounding Box Estimation

<div align="justify">
Minimum area rectangle estimation algorithm serially selects every image of the dataset and extracts the corresponding ROIs (images) of all instances in the image. Then, the initial pixel outline coordinates are mapped to refer to the new smaller images. The above outlines are used to reconstruct images that contain the segmentation masks of all image's instances. Every segmentation mask is considered as an object and its used for the final estimation of the rotated bounding box properties (xc, yc, w, h, theta). If the final theta angle is in [0<sup>o</sup>,  1<sup>o</sup>], the minimum area rectangle is considered as normal and theta=0<sup>o</sup>, else theta=theta (minimizes IOU → more positive anchors). Finally, the estimated coordinates (x,y) of the new rectangle are then transformed to refer to the original image.
</div align="justify">  

#### Minimum area rectangle estimation algorithm flowchart:

![flowchart](https://user-images.githubusercontent.com/74200033/164459112-c839abf7-840a-4fb7-8d41-1870df7dca12.jpg)
