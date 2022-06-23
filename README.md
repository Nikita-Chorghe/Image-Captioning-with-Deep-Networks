# image-captioning

## NOTE 

    Make sure you are using Python version 3.7 as this program was written in this version

## Installation 

First you have to change directory using the following command
   
     $ cd <path where this code is downloaded>
     $ cd image-captioning

Download the required packages with correct versions as per requirements.txt using the following command
    
    $ pip install -r requirements.txt

## Running the program

This code is best run via terminal

Run the python code using the following command (make sure you are in image-captioning directory path
    
    $ python3 -m src.main


# Image Captioning with Deep Networks

## INTRODUCTION
Image captioning has made tremendous progress recently.It takes an input and gives text describing the content of the photo. It takes photo as input and outputs encoded representation of it that captures crucial features. This uses CNN architecture. Architecture consists of several CNN blocks which extracts various features from the image in different layer and eventually identifies elements in the image. After this sequence decoder outputs a sequence of tokens that describes the photo. It is basically Recurrent Network model consisting of a stack of LSTM layers fed by an Embedding layer. CNN process the image and LSTM operates on the sequence generated. Output of these two is combined in together with multi-model layer. 

## II. INTRODUCTION AND BACKGROUND WORK

A. Neural network models for captioning involve three main elements:

The project has data in two forms. First a text file containing all the captions and second the images to be processes. Each image has 5 captions associated with it. We process the captions by breaking it into words and then remove all the punctuation and hanging words. After this we create word to vectors using a model called Word2Vec in gensim. We feed all our captions into this model and it uses the word corpus to give us the vector form of each word. We then convert our captions into vectors of size (Number of Words in Caption) * 100 where 100 is the size of each word vector. We also process the images to make all the images of the same size and of a fixed dimension which is needed for our CNN's first layer.

Feature Extraction: Feature extraction model which is neural network that takes image as input and extract salient features in the form of a fixed-length vector. Convolution neural network is used to extract feature. CNN is trained directly on the images in data set


Language Model: For image captioning, LSTM based model is used to predict the sequences of words from the feature vectors obtained from the VGG network.

## DATA SET DETAILS 

The first is the images which we will be captioning. We have 31,783 unique images in our dataset.

Secondly we have a .csv file which holds the information about these images which will help us train the model. For each image we have maximum 5 unique captions i.e an image can be captioned as any one of the following.

The .csv file has 3 fields:
1. Name of the Image(Image name)
2. The caption number(comment number)
3. The caption(comment)



<img src = "https://github.com/Nikita-Chorghe/Image-Captioning-with-Deep-Networks/blob/master/Images/1.jpg"></img>
<img src = "https://github.com/Nikita-Chorghe/Image-Captioning-with-Deep-Networks/blob/master/Images/2.jpg"></img>
<img src = "https://github.com/Nikita-Chorghe/Image-Captioning-with-Deep-Networks/blob/master/Images/3.jpg"></img>
<img src = "https://github.com/Nikita-Chorghe/Image-Captioning-with-Deep-Networks/blob/master/Images/4.jpg"></img>
<img src = "https://github.com/Nikita-Chorghe/Image-Captioning-with-Deep-Networks/blob/master/Images/5.jpg"></img>
<img src = "https://github.com/Nikita-Chorghe/Image-Captioning-with-Deep-Networks/blob/master/Images/LSTM.png"></img>
<img src = "https://github.com/Nikita-Chorghe/Image-Captioning-with-Deep-Networks/blob/master/Images/vgg16 arch.png"></img>
<img src = "https://github.com/Nikita-Chorghe/Image-Captioning-with-Deep-Networks/blob/master/Images/word_graph.jpg"></img>

