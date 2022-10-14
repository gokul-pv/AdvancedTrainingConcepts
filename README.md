# Advanced Training Concepts
> Class activation maps, Weight Updates, Optimizers & LR Schedulers

The assignment is done using CIFAR-10 dataset. It consists of 60000 32x32 color (3-channel) images in 10 classes, with 6000 images per class. There are 50000 training images and 10000 test images. It has the classes: ‘airplane’, ‘automobile’, ‘bird’, ‘cat’, ‘deer’, ‘dog’, ‘frog’, ‘horse’, ‘ship’, ‘truck’.

<p align="center" style="padding: 10px">
<img alt="Forwarding" src="https://github.com/gokul-pv/AdvancedTrainingConcepts/blob/main/Images/dataset_images.png?raw=true" width =500><br>
<em style="color: grey">Figure 1 : Random images from dataset </em>
 </p> 

## Target
* Apply Transformation using Albumentation Library ( RandomCrop(32, padding=4) and CutOut(16x16))
* Implement GradCam.
* Train ResNet18 on Cifar10 for 20 Epochs

**Code Explanation**

All the python scripts used in the assignment are cloned from repository [MyMainRepo](https://github.com/gokul-pv/MyMainRepo). The repo has the following structure
1. models/restnet.py (contains the Resnet18 model)
2. main.py  (contains training and testing function)
3. utils.py (contains 	image augmentation, gradcam functions ...)


**Albumentation**

The transformation is applied using library albumentations.

<p align="center" style="padding: 10px">
<img alt="Forwarding" src="https://github.com/gokul-pv/AdvancedTrainingConcepts/blob/main/Images/albumentation_transform.png?raw=true" width =500><br>
<em style="color: grey">Figure 2 : transformation applied different times on same image </em>
 </p> 

  



The **summary** of the model is shown below

<p align="center" style="padding: 10px">
<img alt="Forwarding" src="https://github.com/gokul-pv/AdvancedTrainingConcepts/blob/main/Images/model_summary.png?raw=true" width =500><br>
<em style="color: grey">Figure 3 : Model summary </em>
 </p> 



**Result**

The training log for 20 eposchs is shown below

<p align="center" style="padding: 10px">
<img alt="Forwarding" src="https://github.com/gokul-pv/AdvancedTrainingConcepts/blob/main/Images/Log1.png?raw=true" width =500><br>
<em style="color: grey">Figure 4.1 : log1 (epoch 1 to 8) </em>
 </p> 
 
 <p align="center" style="padding: 10px">
<img alt="Forwarding" src="https://github.com/gokul-pv/AdvancedTrainingConcepts/blob/main/Images/log2.png?raw=true" width =500><br>
<em style="color: grey">Figure 4.2 : log2 (epoch 8 to 14) </em>
 </p> 
 

<p align="center" style="padding: 10px">
<img alt="Forwarding" src="https://github.com/gokul-pv/AdvancedTrainingConcepts/blob/main/Images/log3.png?raw=true" width =500><br>
<em style="color: grey">Figure 4.3 : log3 (epoch 14 to 20) </em>
</p> 

  
The test and validation loss and accuracy are shown below

<p align="center" style="padding: 10px">
<img alt="Forwarding" src="https://github.com/gokul-pv/AdvancedTrainingConcepts/blob/main/Images/Loss_plot.png?raw=true" width =500><br>
<em style="color: grey">Figure 5 : Plot for loss and accuracy </em>
 </p> 

<p align="center" style="padding: 10px">
<img alt="Forwarding" src="https://github.com/gokul-pv/AdvancedTrainingConcepts/blob/main/Images/accurarcy_per_class.png?raw=true" width =500><br>
<em style="color: grey">Figure 6 : Accuracy per class</em>
 </p> 


**Misclassified Images during validation**

Misclassified images during validation for all the three models are shown below


<p align="center" style="padding: 10px">
<img alt="Forwarding" src="https://github.com/gokul-pv/AdvancedTrainingConcepts/blob/main/Images/misclassified.png?raw=true" width =500><br>
<em style="color: grey">Figure 7 : Misclassified images </em>
 </p> 


**GradCam output on  misclassified images**
 **Gradient-weighted Class Activation Mapping** (GradCAM) uses the gradients of any target concept (say logits for 'dog' or even a caption), flowing into the final convolution layer to produce a coarse localization map highlighting the important regions in the image for predicting the concept

<p align="center" style="padding: 10px">
<img alt="Forwarding" src="https://github.com/gokul-pv/AdvancedTrainingConcepts/blob/main/Images/gradcam_1.png?raw=true" width =800><br>
<em style="color: grey">Figure 8.1 : Gradcam on misclassified images 1 </em>
 </p> 
<p align="center" style="padding: 10px">
<img alt="Forwarding" src="https://github.com/gokul-pv/AdvancedTrainingConcepts/blob/main/Images/gradcam_2.png?raw=true" width =800><br>
<em style="color: grey">Figure 8.2 : Gradcam on misclassified images 2 </em>
 </p> 



