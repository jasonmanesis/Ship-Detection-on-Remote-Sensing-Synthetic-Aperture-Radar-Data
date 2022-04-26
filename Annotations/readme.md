## Validation Set Creation

<div align="justify">
The validation set was set equal to 5% of the total training images. The distributions of validation dataset must have the required similarity with the corresponding ones from the original training set for each variable (xc, yc, aspect_ratio=h/w, area=h・w) in instance level. Because the split of the training dataset to new training and validation sets must be done on image level, we assume that each image contains only one imaginary instance whose geometric properties are derived from the mean values of the variables of all the actual image instances. In combination with the above, in the set of geometric properties of each image are added 2 variables regarding the number of examples it contains, as well as whether it depicts land sections, composing a group of a 6 variables (xc, yc, aspect_ratio, area, number_of_instances, Inshore_label ∈ {0,1}).


### Validation set extraction algorithm.

To extract the validation set, the training data is divided into 15 groups based on the given image IDs which contain the same number of images. Then the groups that have each one of the mean values close to the original ones for every variable (xc<sup>mean</sup>, yc<sup>mean</sup>, aspect_ratio<sup>mean</sup>, area<sup>mean</sup>, number_of_instances, Inshore_label) simultaneously, were selected. Finally, an iterative algorithm samples images from the above groups and tries to create the desired distribution of every variable as a mixture of a distribution that resembles the original distribution and of another distribution that tends to be more random.

</div align="justify">

### Validation Set Distributions:

<div align="center">
  
#### Parameter Distributions - Normal Bounding Boxes
![pie_plots_val_aug_rotated](https://user-images.githubusercontent.com/74200033/165339328-1441e963-ca89-47c4-88a7-14cbfa06f1c9.png)

#### Parameter Distributions - Rotated Bounding Boxes
![val_aug_rotated](https://user-images.githubusercontent.com/74200033/165337119-61e5b2b7-1990-4d12-bbb3-b5088afa52fb.png)
![augval2_r](https://user-images.githubusercontent.com/74200033/165337481-9c99a509-f23b-42bc-93a8-f20a6fad10af.png)
  
#### Object Sizes - Normal Bounding Boxes 
![p6](https://user-images.githubusercontent.com/74200033/165338892-0cfc0216-f070-469a-aaa5-6344bf72f364.png)

#### Object Sizes - Rotated Bounding Boxes
![pie_plots_val_aug_rotated](https://user-images.githubusercontent.com/74200033/165339398-74e270fa-3340-40e2-98a2-8989b228e2ce.png)
  
</div align="center">  

#### Spatial Distributions and object sizes. 

<div align="center">

#### Original Training Set  
![2d_hist_all](https://user-images.githubusercontent.com/74200033/165340114-92183f8b-ef4a-4464-8291-3ec59f226b5b.png)
  
#### New Training Set   
![2d_hist_train](https://user-images.githubusercontent.com/74200033/165340133-c20add48-480a-4cb2-ace6-1ca1e9289ec0.png)
  
#### Validation Set - Normal Bounding Boxes  
![2d_Aug](https://user-images.githubusercontent.com/74200033/165340167-54c26260-fc78-4e2f-888d-eaee5ce044d2.png)
  
#### Validation Set - Rotated Bounding Boxes
![2d_hist_val_aug_rotated](https://user-images.githubusercontent.com/74200033/165340217-ba3286e4-a884-41fc-88ae-4b2d5e627a4f.png)
  
</div align="center">
 
  



## Rotated Bounding Box Estimation

<div align="justify">
Minimum area rectangle estimation algorithm serially selects every image of the dataset and extracts the corresponding ROIs (images) of all instances in the image. Then, the initial pixel outline coordinates are mapped to refer to the new smaller images. The above outlines are used to reconstruct images that contain the segmentation masks of all image's instances. Every segmentation mask is considered as an object and its used for the final estimation of the rotated bounding box properties (xc, yc, w, h, theta). If the final theta angle is in [0<sup>o</sup>,  1<sup>o</sup>], the minimum area rectangle is considered as normal and theta=0<sup>o</sup>, else theta=theta (minimizes IOU → more positive anchors). Finally, the estimated coordinates (x,y) of the new rectangle are then transformed to refer to the original image.
</div align="justify">  

#### Minimum area rectangle estimation algorithm flowchart:

![flowchart](https://user-images.githubusercontent.com/74200033/164459112-c839abf7-840a-4fb7-8d41-1870df7dca12.jpg)
