###### This file contains the steps to run the state-of-the-art algorithms used in the thesis for both detection and classification of retail products. The algorithms were run in the Google Colab Pro environment.
&nbsp; 
# Object Detection

### Yolov5

1. Download the notebook "YOLOv5-SKU100k.ipynb".
2. When creating the "data.yaml" file make sure that the directories for train, test and val correspond to the location where you have downloaded the SKU110K dataset. Additionally, check that the labels are in the format expected by YOLO and the images are 512x512 in size.
3. Train, test and calculate the metrics of the algorithm by executing the cells of the file after the cell that creates the "data.yaml" file.

    > Note: When calling the "compare" function to calculate the metrics, make sure that the directories with which it is called correspond to the desired ones.

### SSD

1. Download the notebook "SSD-SKU110K.ipynb".
2. Be sure to choose the appropriate directories where the annotations in .csv format expected by the SSD algorithm (cell number 6) for the SKU110K dataset are located. For this algorithm make sure not to modify the size of the images because during the execution the algorithm takes care of the resize to 1024x1024.
3. In the functions "convert_tfrecord" and "create_data" make sure that the variable "root" has the directory where the images of the SKU110K dataset are located.
4. Train, test and calculate metrics by executing notebook cells.

    > Note: When calling the "compare" function, make sure that the image and annotation directories correspond to the desired ones. Also make sure that the model with the desired weights is loaded globally in the variable called "model".

### Faster R-CNN
1. Download the notebook "Detectron2.ipynb".
2. Make sure to select the appropriate directories where the annotations in .csv format (same format used in the SSD algorithm) are located in cell 6 and 8 for the SKU110K dataset. Additionally, these annotations and images must be sized for 512x512.
3. Train, test and calculate metrics by executing notebook cells.

    > Note: When calling the "compare" function, make sure that the image and annotation directories correspond to the desired ones. Also make sure that the model with the desired weights is loaded globally in the variable called "predictor".

### EfficientDet
1. Download the notebook "EfficientDet.ipynb".
2. Make sure to use the proper directories in cell 6 for the SKU110K dataset, they use the same SSD .csv format but with the annotations and images in 512x512 size. You can use the same as in the Faster R-CNN algorithm.
3. Train, test and calculate metrics by executing notebook cells.

    > Note: When calling the "compare" function, make sure that the image and annotation directories correspond to the desired ones. Also make sure that the model with the desired weights is loaded globally in the variable called "gtf".


# Image Classification

### Without "Object" class
1. Download the notebook "ImageClassification.ipynb" or "Augmented data ImageClassification.ipynb".
2. Make sure to place the desired directories for the set of images and annotations (.csv) in cell 5. These images should be the images of the shelves with the products under study (not the SKU110K dataset). Additionally, keep in mind that these annotations no longer contain only the class "object" but the rest of the classes which will be studied.
3. The function "make_partitions" is in charge of creating the crops from the complete images of the shelves together with the respective annotations (regardless of "object" class). After finishing the execution it will create the directories with the name of each class and the respective crops inside them. These folders are created in the same place where the notebook is downloaded.
4. Make sure that the variables "train_dir", "val_dir", and "test_dir" contain the desired directories for the train, validation and test datasets respectively. Each of these directories must contain the folders with the class names (as integers) and within these the respective crops.
5. Run all cells to train and test the 4 algorithms. The metrics and confusion matrix are automatically calculated from the directories configured in the previous steps.

### With all classes
1. Download the notebook "Resnet TFAugmentation ImageClassification.ipynb" or "Resnet oversampler ImageClassification.ipynb". In addition to the algorithms, these notebooks contain the procedure to perform augmentation by transformations and Random Oversampling respectively.
2. Make sure to place the desired directories for the set of images and annotations (.csv) in cell 6. These images should be the images of the shelves with the products under study (not the SKU110K dataset). Additionally, keep in mind that these annotations no longer contain only the class "object" but the rest of the classes which will be studied.
3. The function "make_partitions" is in charge of creating the crops from the complete images of the shelves together with the respective annotations (considering class "object"). After finishing the execution it will create the directories with the name of each class and the respective crops inside them. These folders are created in the same place where the notebook is downloaded.
4. Make sure that the variables "train_dir", "val_dir", and "test_dir" contain the desired directories for the train, validation and test datasets respectively. Each of these directories must contain the folders with the class names (as integers) and within these the respective crops.
5. Run all cells to train and test the 4 algorithms. The metrics and confusion matrix are automatically calculated from the directories configured in the previous steps.


# Other Files
### IQA
The notebook "IQA.ipynb" contains the code to run the BRISQUE algorithm on a set of images. Additionally, please note that when running the file "brisquequality&#46;py" it must be the one found in this repository and not the one downloaded from the official repository. 

### Data Augmentation
The notebook "Data augmentation.ipynb" contains the code to perform data augmentation on the complete images of the shelves. Make sure that cell 7 has the desired information for the annotation (.csv) and image directories. 

Modify the variables "suffix" and "save_images_path" to suit the desired suffix for the name of the applied transformation and the directory where you want to save the transformed images.


