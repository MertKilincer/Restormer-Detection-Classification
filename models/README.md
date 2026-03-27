# Model Weights

The trained model weights are not stored directly in this GitHub repository because they are large files.

You can download all weights from the following Google Drive folder:

https://drive.google.com/drive/folders/16ue6vpwAWVbvb13ZNynCP_i-uTJ_HwXw?usp=drive_link

The Drive folder includes:
- Fine-tuned Restormer weights
- Pretrained Restormer weights
- CNN weights
- YOLO weights

Weight groups

Fine-Tuned Weights
These weights are used for corruption-specific image restoration:
- blur_curetsd.pth
- exposure_curetsd.pth
- rain_curetsd.pth

Pretrained Weights
These are the pretrained restoration model weights used as initialization before fine-tuning:
- deraining.pth
- motion_deblurring.pth
- single_image_defocus_deblurring.pth
- best_exposure_restorer.pth

CNN Weights
These weights are used for the 14-class traffic sign classification model.
They include the saved best/last checkpoints of the MiniCNN classifier.

YOLO Weights
These weights are used for the YOLOv8 traffic sign detector.
They include the trained detector checkpoints.

How to use
After downloading the files, place them in your preferred local directories and update the paths inside the notebooks if needed.

Notes
This repository contains the notebooks, results, and documentation.
The weights are distributed separately through Google Drive to keep the repository lightweight and easy to clone.
