# ML-PrepCamp-CarDetection
Submission for ML preparation camp assignment to try various models for object detection on a car camera dataset.

## Object Detection
### YOLO
I have used yolov5 for the main task because it provided the functionality to freeze layers of the model and finetune it for the specific dataset, whereas yolov8 does not recommend to do so - "The reason why freezing layers may not lead to faster training speed in YOLOv8 could be due to the nature of the model architecture. YOLOv8 consists of multiple components, including backbone layers, neck layers, and detection heads. Freezing layers in one component may not necessarily speed up the training process since the model still needs to compute forward and backward passes through the unfrozen layers."
The code and final weights are provided in the zip file. The best model is in `\yolov5\runs\train\exp8\weights\best.pt`, with mAP_50 0.6 and mAP_95 0.3.

### Detectron2, Swin, DeTR
All the code can be found [here](https://colab.research.google.com/drive/1sex9STWvqv1hBeJGI0slh6G01__fgETO?usp=sharing).

### Custom RCNN
I have implemented the code for generating region proposals and trained a CNN for classfying the region proposals. Due to time constraints, I could integrate all the code together but it can be done so easily. Code can be found [here](https://colab.research.google.com/drive/1j7neHjlulyfK1yb_YQIhRKEvVfuPiP_I?usp=sharing)

## Instance Segmentation
### Yolov5
Kaggle notebook can be found [here](https://www.kaggle.com/code/amoametan/car-dataset-segmentation), and the weights which give the best accuracy [here](https://iitk-my.sharepoint.com/:u:/g/personal/bhagwata22_iitk_ac_in/EcIQ8NoMB1VLqouKrO1LvtoBtsHcYrISG_ODpvEhZFBv9Q?e=bJ7vta), which gives mAP of around 75% (the kaggle outputs got deleted while exporting so cannot provide exact metrics)

### Detectron2
Can be found in the previous detectron2 colab file


