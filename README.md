# Ship-Detection-on-Remote-Sensing-Synthetic-Aperture-Radar-Data
****
<div align="full">
The present diploma thesis focuses on the investigation of methods for the effective detection of ships in synthetic aperture radar satellite imagery utilizing deep learning techniques. These methods uses the Faster-RCNN and YOLOv5 network architectures to create three different detectors. More specifically, the first two models created are based on the Faster-RCNN network architecture and utilize a set of normal and rotated bounding boxes for the detection process. The one-stage detection network is based on the architecture of the YOLOv5 model and uses regular bounding boxes to delimit the estimated targets.The produced models are trained and evaluated on the HRSID dataset. The greatest accuracy is found in models that use regular bounding boxes to derive estimates. While, the model with rotated bounding boxes, shows the largest localization errors and is characterized by an increased number of false negative detections.
</div align="full">



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

<span style="color:">text</span>
## Model Performance

<div align="left"> 
  
 ***Mean Average Precision***
  
|          **Metric**        | **Faster - RCNΝ (Normal Bboxes)**     |**Faster - RCNΝ (Rotated Bboxes)** | **YOLOv5** |  **STANet<sup>1</sup>**  |  **DB-YOLO<sup>2</sup>**  |
|:--------------------------:|:-------------------------------------:|:---------------------------------:|:----------:|:------------:|:-------------:|
|AP<sup>0.50:.05:.95</sup> | *68.1*|*42.9*|*71.1*|*69.5*|***72.0***|
|AP<sup>0.50</sup> |*91.4*|*75.3*|***94.2***|*92.4*|***94.4***|
|AP<sup>0.75</sup> |*79.3*|*45.5*|***82.0***|*81.1*|-|
|AP<sup>small</sup> |*69.3*|*41.3*|*62.9*|***70.9***|-|
|AP<sup>medium</sup> |*68.5*|*51.1*|***80.7***|*68.6*|-|
|AP<sup>large</sup> |*44.1*|*20.9*|***55.1***|*37.8*|-|

 ***Mean Average Recall***  
|          **Metric**        | **Faster - RCNΝ (Normal Bboxes)**     |**Faster - RCNΝ (Rotated Bboxes)** | **YOLOv5** |  **STANet<sup>1</sup>**  |  **DB-YOLO<sup>2</sup>**  |
|:--------------------------:|:-------------------------------------:|:---------------------------------:|:----------:|:------------:|:-------------:|
|AR<sup>max=1</sup> |*27.8*|*21.9*|***28.2***|-|-|
|AR<sup>max=10</sup> |*61.6*|*44.9*|***63.5***|-|-|
|AR<sup>max=100</sup> |*74.0*|*48.3*|***75.9***|-|-|
|AR<sup>small</sup> |***73.5***|*46.4*|*69.5*|-|-|
|AR<sup>medium</sup> |*79.1*|*57.9*|***84.5***|-|-|
|AR<sup>large</sup> |*64.3*|*29.7*|***65.1***|-|-|
</div align="left">
  
*<sup>1</sup> SOTA Two Stage Detector (Wang et. al.)* [`See paper`](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=9353475 )    
*<sup>2</sup> SOTA One Stage Detector (Zhu et. al.)* [`See paper`](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8662457/ )

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
                  
  
