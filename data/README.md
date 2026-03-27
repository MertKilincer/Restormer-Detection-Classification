{\rtf1\ansi\ansicpg1254\cocoartf2759
\cocoatextscaling0\cocoaplatform0{\fonttbl\f0\fswiss\fcharset0 Helvetica;}
{\colortbl;\red255\green255\blue255;}
{\*\expandedcolortbl;;}
\paperw11900\paperh16840\margl1440\margr1440\vieww11520\viewh8400\viewkind0
\pard\tx720\tx1440\tx2160\tx2880\tx3600\tx4320\tx5040\tx5760\tx6480\tx7200\tx7920\tx8640\pardirnatural\partightenfactor0

\f0\fs24 \cf0 # Data Folder\
\
This folder is used to document the dataset structure and the preprocessing logic used in this project.\
\
The full dataset is not included in this repository because of its size.\
\
Dataset source\
We use the CURE-TSD dataset and convert the original videos into frame-based image data.\
\
Frame-based structure used in the project\
subset/\
  classification_labels.csv\
  frames/\
    train/\
    test/\
  labels/\
    train/\
    test/\
\
What is stored in the original project\
- classification_labels.csv\
- extracted video frames\
- annotation text files\
- subset-based train/test organization\
\
Frame naming format\
Example:\
01_01_02_01_282.jpg\
\
Meaning:\
- sequenceType: 01 = Real, 02 = Unreal\
- sequenceNumber: 01\'9649\
- challengeType: corruption type\
- challengeLevel: severity level\
\
Annotation format\
Each image has a matching .txt file with this format:\
\
<cls> <x1> <y1> <x2> <y2> <x3> <y3> <x4> <y4>\
\
The first value is the sign class.\
The remaining values are the four-corner coordinates of the traffic sign.\
\
Classes\
1 speed_limit\
2 goods_vehicles\
3 no_overtaking\
4 no_stopping\
5 no_parking\
6 stop\
7 bicycle\
8 hump\
9 no_left\
10 no_right\
11 priority_to\
12 no_entry\
13 yield\
14 parking\
\
Included in this repository\
This repository may include only small sample metadata or example annotations for documentation purposes.\
\
Not included in this repository\
- Full extracted frame dataset\
- Full label dataset\
- Large raw or processed data folders\
\
Data preparation notebook\
The dataset preparation process is documented in:\
notebooks/data_preparation/Cure_TSD_Subset.ipynb}