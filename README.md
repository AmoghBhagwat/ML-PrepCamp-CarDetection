# ML-PrepCamp-CarDetection
Submission for ML preparation camp assignment to try various models for object detection on a car camera dataset.

## Object Detection
### YOLO
I have used yolov5 for the main task because it provided the functionality to freeze layers of the model and finetune it for the specific dataset, whereas yolov8 does not recommend to do so - "The reason why freezing layers may not lead to faster training speed in YOLOv8 could be due to the nature of the model architecture. YOLOv8 consists of multiple components, including backbone layers, neck layers, and detection heads. Freezing layers in one component may not necessarily speed up the training process since the model still needs to compute forward and backward passes through the unfrozen layers."
The code and final weights are provided in the zip file. The best model can be found [here](https://iitk-my.sharepoint.com/:u:/g/personal/bhagwata22_iitk_ac_in/EdX2JIdBWZBIu8PadgJvxNgBTDHtmMzy7LwTECvKwmuAIg?e=Y35Eij), with mAP_50 0.6 and mAP_95 0.3.

### Detectron2, Swin, DeTR
All the code can be found [here](https://colab.research.google.com/drive/1sex9STWvqv1hBeJGI0slh6G01__fgETO?usp=sharing).

### Custom RCNN
I have implemented the code for generating region proposals and trained a CNN for classfying the region proposals. Due to time constraints, I could not integrate all the code together but it can be done so easily. Code can be found [here](https://colab.research.google.com/drive/1j7neHjlulyfK1yb_YQIhRKEvVfuPiP_I?usp=sharing)

## Instance Segmentation
### Yolov5
Kaggle notebook can be found [here](https://www.kaggle.com/code/amoametan/car-dataset-segmentation), which gives mAP of around 75% (the kaggle outputs got deleted while exporting so cannot provide exact metrics)

### Detectron2
Can be found in the previous detectron2 colab file, snd the weights are here: [detectron object detection](https://iitk-my.sharepoint.com/:u:/g/personal/bhagwata22_iitk_ac_in/EThbQHhbi8JDlLThyPnzUOsB473-RAM61cEr4XR6flD7Hw?e=YNNOLH), [detecton segmentation](https://iitk-my.sharepoint.com/:u:/g/personal/bhagwata22_iitk_ac_in/EcIQ8NoMB1VLqouKrO1LvtoBtsHcYrISG_ODpvEhZFBv9Q?e=bJ7vta)

## Comparison of parameters
I tried with 3 different batch sizes of 16, 32 and 48. As the batch size was increased, the training time decreased marginally, but the mAP values improved by a significant margin (0.44, 0.53, 0.61). The only downside of higher batch sizes is that it takes up more GPU memory.

Hyperparameter tuning - I first used the basic `hyp.scratch.yaml` to train the dataset on pretrained model by freezing its backbone layers, and then `hyp.VOC.yaml` (which is used for finetuning) to further finetune the model. I also modified the value of `fl_gamma` (focal loss) to penalize the wrong predictions on the minority class more heavily due to the skewed nature of the dataset.
