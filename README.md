# Ship-Detection-on-Remote-Sensing-Synthetic-Aperture-Radar-Data
Convolutional neural network model based on the architecture of the **Faster-RCNN** for wildfire smoke detection. For this project we used a pretrained model on ImageNet dataset, from detectron2's [Model Zoo](https://detectron2.readthedocs.io/en/latest/modules/model_zoo.html), and fine-tuned it for the task of wildfire smoke detection from optical image data.

## HRSID (High-Resolution SAR Images Dataset) Properties.
<div align="left">
 
* The specific dataset contains 116 co-polarized and 20 cross-polarized SAR imageries.
* The original imageries for constructing HRSID are 99 Sentinel-1B imageries, 36 TerraSAR-X and 1 TanDEM-X imageries.
* The above 136 panoramic SAR imageries cropped to 5604 high-resolution SAR images.
* These 5604 images have dimensions of 800 × 800 pixels, resolution of 96 dpi, and there are in .jpeg format.
* The colour depth of the images is 8 bits (one channel). 
* The extracted 5604 high-resolution SAR images contain 16951 ship instances.
* The spatial resolutions of SAR images are 0.5, 1 and 3 meters per pixel.
* The annotations of each instance are the corresponding bounding box and the ship’s outline. 
* The annotations of each SAR image constitute a .json file in MS COCO dataset format.
* Paper Link: https://ieeexplore.ieee.org/abstract/document/9127939
* Dataset Link: https://github.com/chaozhong2010/HRSID 
</div align="left">

## Proposed architectures of Faster-RCNN. 
The model architecture is based on the general architecture of the **Faster-RCNN**, which includes the main modules of **Feature Pyramid Network**, **Region Proposal Network** as well as the model of **Fast-RCNN**. For the bottom-up pathway of the FPN network the architecture of the **ResNet50** was used.

<img src="https://miro.medium.com/max/2000/1*Wvn0WG4XZ0w9Ed2fFYPrXw.jpeg">

_Image source: https://miro.medium.com/max/2000/1*Wvn0WG4XZ0w9Ed2fFYPrXw.jpeg_


## Model Performance

<div align="left"> 
  
 **Mean Average Precision** 
  
|          **Metric**        | **Faster - RCNΝ (Normal Bboxes)**     |**Faster - RCNΝ (Rotated Bboxes)** | **YOLOv5** |  **STANet<sup>1</sup>**  |  **DB-YOLO<sup>2</sup>**  |
|:--------------------------:|:-------------------------------------:|:---------------------------------:|:----------:|:------------:|:-------------:|
|AP<sup>0.50:.05:.95</sup> | 68.1|42.9|71.1|69.5|72.0|
|AP<sup>0.50</sup> |  91.4|75.3|94.2|92.4|94.4|
|AP<sup>0.75</sup> | 79.3|45.5|82.0|81.1|-|
|AP<sup>small</sup> |91.4|75.3|94.2|92.4|-|
|AP<sup>medium</sup> |91.4|75.3|94.2|92.4|-|
|AP<sup>large</sup> |91.4|75.3|94.2|92.4|-|

 **Mean Average Recall**  
|          **Metric**        | **Faster - RCNΝ (Normal Bboxes)**     |**Faster - RCNΝ (Rotated Bboxes)** | **YOLOv5** |  **STANet<sup>1</sup>**  |  **DB-YOLO<sup>2</sup>**  |
|:--------------------------:|:-------------------------------------:|:---------------------------------:|:----------:|:------------:|:-------------:|
|AR<sup>max=1</sup> |  91.4|75.3|94.2|92.4|-|
|AR<sup>max=10</sup> |91.4|75.3|94.2|92.4|-|
|AR<sup>max=100</sup> |91.4|75.3|94.2|92.4|-|
|AR<sup>small</sup> |91.4|75.3|94.2|92.4|-|
|AR<sup>medium</sup> |91.4|75.3|94.2|92.4|-|
|AR<sup>large</sup> |91.4|75.3|94.2|92.4|-|
</div align="left">
  
**<sup>1</sup> SOTA Two Stage Detector (Wang et. al.)**       
**<sup>2</sup> SOTA One Stage Detector(Zhu et. al.)**


## Results

https://user-images.githubusercontent.com/74200033/130357982-c47f46ed-af8a-48c1-abeb-d4761eb707c6.mp4

**Original video at:** https://www.youtube.com/watch?v=q07TBd5o1HQ&t=35s

https://user-images.githubusercontent.com/74200033/130357983-04dbce41-5e87-456c-ad55-a9769d1ec1d5.mp4

**Original video at:** https://www.youtube.com/watch?v=5cEr5ZXGUYA    


## Requirements

    torch == 1.9.0+cu102                           numpy == 1.19.5                           json == 2.0.9
    torchvision == 0.10.0+cu102                    yaml == 5.1                               fiftyone == 0.12.0
    pyyaml == 5.1                                  pandas == 1.3.2                           IPython == 5.5.0
    detectron2 == 0.5                              cv2 == 4.1.2
                  
  
