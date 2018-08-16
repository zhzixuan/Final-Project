# Final-Project

## 1. This project is about my final project. I will show some SupportDocs here.

### Code: prototxt files (network structure), scripts when training and testing, scripts when applying in real scenes in life. 

### Result: trained model (caffemodel) with parameters and  saved predicted segmentation (.png). 
I uploaded the required caffemodel to the Baidu web disk, which can be downloaded from here (Link: https://pan.baidu.com/s/1zsG-Mos7nzcg3kL2dF1sig  password: ajqj).

### Demo: the original video and segmented demo video. 
Please download it from https://pan.baidu.com/s/1NbxCDoiXTRO-sKe-bJZUAw (password: rf2m).

## 2. Configuration and Application

### 2.1 configuration

The code is developed or applied under the following configurations.
Hardware: 2-8 GPUs (with at least 12G GPU memories) 
Software: Ubuntu 16.04.3 LTS, CUDA 8.0, caffe, python, and OpenCV
Dataset: ADE20K (download from http://groups.csail.mit.edu/vision/datasets/ADE20K/)

### 2.2 application
When using my script on a new computer, the file_root of all scripts needs to be modified to your real file directory.

### Train:
Before training, please prepare model structure (.prototxt), hyper parameter setting file (solver.prototxt) and model training script (train.sh). These files need to be changed based on the actual condition of the hardware.
Makesure there has the ade_sceneparsing_train_im2cate.txt file with all image names for the training set. You can get it from the dataset classic web site.
You also need the ImageNet-pre-trained model when fine-tuning. You can download the caffemodel from Baidu web disk too (link: https://pan.baidu.com/s/1CNCAEG4iwsXFUq0eoXsiyQ  password:8m8q).
Enter the command in the terminal to train a model: sh train.sh

### Test:
After successfully training out the network model, we need to evaluate the effectiveness of the trained model. Prepare the corresponding deploy.prototxt (network structure when testing) and validation.txt (names of test dataset).
Enter the command in the terminal to evaluate the model on test set: python evaluate_seg.py
It will produce a folder named ‘predict’, which contains the predicted segmentation result. The color.py can colorize the grayscale results.
Enter the command in the terminal, you can see the score of mIOU, pixel accuracy and mean accuracy: python score.py

### Apply on a scene image using our trained model:
Enter the command in the terminal: evaluate_demo.py
If there is only an original video, you need to use save_frame.py to take pictures from the video. Use demolist.py to get the name list. Then use evaluate_demo.py to get predicted segmentation. Use color.py to visualize.

