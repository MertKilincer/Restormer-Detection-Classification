{\rtf1\ansi\ansicpg1254\cocoartf2759
\cocoatextscaling0\cocoaplatform0{\fonttbl\f0\fswiss\fcharset0 Helvetica;}
{\colortbl;\red255\green255\blue255;}
{\*\expandedcolortbl;;}
\paperw11900\paperh16840\margl1440\margr1440\vieww11520\viewh8400\viewkind0
\pard\tx720\tx1440\tx2160\tx2880\tx3600\tx4320\tx5040\tx5760\tx6480\tx7200\tx7920\tx8640\pardirnatural\partightenfactor0

\f0\fs24 \cf0 # Model Weights\
\
The trained model weights are not stored directly in this GitHub repository because they are large files.\
\
You can download all weights from the following Google Drive folder:\
\
https://drive.google.com/drive/folders/16ue6vpwAWVbvb13ZNynCP_i-uTJ_HwXw?usp=drive_link\
\
The Drive folder includes:\
- Fine-tuned Restormer weights\
- Pretrained Restormer weights\
- CNN weights\
- YOLO weights\
\
Weight groups\
\
Fine-Tuned Weights\
These weights are used for corruption-specific image restoration:\
- blur_curetsd.pth\
- exposure_curetsd.pth\
- rain_curetsd.pth\
\
Pretrained Weights\
These are the pretrained restoration model weights used as initialization before fine-tuning:\
- deraining.pth\
- motion_deblurring.pth\
- single_image_defocus_deblurring.pth\
- best_exposure_restorer.pth\
\
CNN Weights\
These weights are used for the 14-class traffic sign classification model.\
They include the saved best/last checkpoints of the MiniCNN classifier.\
\
YOLO Weights\
These weights are used for the YOLOv8 traffic sign detector.\
They include the trained detector checkpoints.\
\
How to use\
After downloading the files, place them in your preferred local directories and update the paths inside the notebooks if needed.\
\
Notes\
This repository contains the notebooks, results, and documentation.\
The weights are distributed separately through Google Drive to keep the repository lightweight and easy to clone.}