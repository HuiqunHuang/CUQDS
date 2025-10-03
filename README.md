


# BCCD Cell Segmentation

## Summary \n

### In this project, I ustilize the UNI foundation model as backbone for binary class fine-grained cell segmentation. More specifically, I integrate UNI2-h as a pretrained image encoder that is connected to a Resnet-based decoder network via skip connections. This architecture allows us to leverage the strength of the pretrained foundation model UNI2-h to extract valuable features of the input for instance segmentation without losing fine-grained information. In addition, the Resnet-based decoder's skip connection design combats the vanishing gradient problem and enables training of much deeper, more expressive decoders — leading to better learned representations for fine-grained segmentation tasks like cells. \n


## Problem Formulation \n

### Given a batch of images which follow the size of (B, 3, 224, 224), the proposed model outputs the corresponding segmentation results which follow the shape of (B, 1, 224, 224). B is the batch size, 3 is the input image channel, 1 is the output image channel, and 224 is the image size which selected based on the parameter setting of UNI2-h. \n


## Model Design \n

### Encoder \n

### Decoder \n

### Loss Function \ n

### Given that this project is designed to test on the single class BCCD dataset, I propose to use the Binary Cross Entropy Loss With Sigmoid Function (BCEWithLogitsLoss) for model optimization. \n



## Data Preprocessing\n

### ss \n



## Training Procedure and Hyperparameters Used \n

### In this project, I split the original BCCD tarining dataset as 80% as training data and 20% as validation data. The original testing data remains as the test set. The model is optimized using AdamW, running 30 epochs in total using batch size of 50. Learning rate is set as -0.0003. The host machine is a server with IntelCore i9-10900X processors and four NVIDIA Quadro RTX 6000 GPUs. \n



## Experiment Results \n

### s \n




## Visualization \n

### To illustrate the model performance on BCCD dataset, I \n




## Challenges & Improvements \n

### In this project, I only use the pretrained UNI2-h foundation model as encoder to extract the cell image features due to time limitation. UNI2-h foundation model is not specified for the cell segmentation tasik. Fine-tunning the UNI2-h model on the cell segmentation task will significantly improve the model performance. In addition, due to time limitation and the first priority is to improve model performance on the BCCD dataset, the proposed model works merely on binary class segmentation task. To make the model work also on multi-class segmentation problem, I will add another classfication head in the decoder and change the loss funtion based on multi-class cross encropy. 

