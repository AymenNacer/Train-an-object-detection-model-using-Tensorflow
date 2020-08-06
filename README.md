# Train an object detection model using Tensorflow
in this repo i trained a model to detect face masks using Google Colab.

![aaaaaa](https://user-images.githubusercontent.com/60849096/89512719-49d9aa00-d7dc-11ea-9fd2-7f7ee5ec49b7.png)


# SETUP
Note: you can skip SETUP step if would like to use the same dataset, download the output folder from : https://drive.google.com/drive/folders/1csS0kivfrfndQoEVTo2gCrqR4s19_Vq_?usp=sharing
* First you need to setup your dataset and perform the annotations to the data using labelling.exe application, my data is already setup and available at mask_dataset
* Download the repo from https://github.com/tensorflow/models and rename it to models, then create tensorflow1 directory(you can change the name but make sure you change it for later intructions) in the C drive and move models inside tensorflow1 
* Choose the model you are going to use based on speed and accuracy you can check models at https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/tf1_detection_zoo.md

* I chose ssd_mobilenet_v1_coco
 * download the model and move it to mask_dataset folder 
 * download ssd_mobilenet_v1_pets.config from sample configs in the same page and edit it based on your dataset and paths then move it to mask_dataset -> training
 * what you need to change	
    * num_classes based on your dataset
    * fine tune checkpoint in line 158  
    * in line 172, 174 change input_path and label_map_path
    * in 183, 185  change input_path and label_map_path
* Copy all folder in mask_dataset except .idea to your models-> object_detection folder
* In training folder, Create object-detection.pbtxt file and write in the format, based on your classes and name you want to appear once it detects the object

	    
     
		 item {
		  id: 1
		  name: 'nine'
		}

		item {
		  id: 2
		  name: 'ten'
		}

    
    

* copy the files from legacy folder to object detection folder
* Copy object-detection.pbtxt from training folder to data folder
* Download anaconda and run 
    * Create a new anaconda environment: conda create -n tf python=3.7
    * Then type: conda activate ‘name of new env’
    * to upgrade pip : python -m pip install --upgrade pip setuptools    
    * Run this command to download needed packages : pip install TensorFlow==1.15 lxml pillow matplotlib jupyter contextlib2 cython tf_slim   

* Next go to https://github.com/protocolbuffers/protobuf/releases/tag/v3.4.0 and  download protoc-3.4.0-win32.zip
    * Extract the zip and open the bin folder. Move protoc.exe into the ‘research’ folder of the cloned repository 

    * upload the models folder to Google Drive and put it in a new tensorflow folder.
# Train on Google Colab
* run code written one by one and make sure to change runtime type to GPU
* at the end a zip file will be generated download it and copy new graph and paste it in the object detection folder
* Copy python scripts model_webcam and model_image, then change the scripts according to your data such as number of classes and name of model.

i used and modified some of the files in Bengemon825/TF_Object_Detection2020 repository 

