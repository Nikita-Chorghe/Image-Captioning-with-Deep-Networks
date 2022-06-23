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
1. Name of the Image (Image name)
2. The caption number (comment number)
3. The caption (comment)

## Theoretical and conceptual study of the technique/algorithm you wouldlike to implement

The model developed for the task will have two parts to it:

Image Feature/Object Detector to extract key objects and features from the image 

Natural Language Generator to determine a caption in English language using the image features

The output from the Image Feature/Object Detector will be the input for the Natural Language 
Generator.

Implementing Image Feature/Object Detector: RCNN, Fast RCNN, Faster RCNN, VGG net

We used RNN for the image caption generation. Depending on the result and time permissibility, we further enhanced the RNN to caption video by splitting it into frames and also using self-attention mechanism. The architecture we used is encoder / decoder architecture.

1. A network model that reads the photograph input and encodes the content into a 
fixed-length vector using an internal representation.
2. A network model that reads the encoded photograph and generates the textual description output.

We are considering two methodologies for solving this issue.
a) Inject Model: This model combines the encoded form of the image with each word. Here we treat the image feature vector on par with a word and predict the next word using this feature vector and previous word. In this RNN is primarily responsible for image conditioned caption generation.

b) In this RNN purely handles the text generation part and CNN the image feature generation. 

## CNN Layers and their Logic

We have used the following layers in CNN: 
1. Convolution
2. Maxpool
3. Flatten

## CNN and RNN Execution Flow

a) The input data has 2 parts : captions and the images themselves. The first step involves parsing the caption and converting the image to 3 * 112 * 112 dimensions and storing them together in a dictionary with the key being the image name.

b) We are initially training the CNN using preloaded MNIST data so that the CNN can extract relevant features from images.

c) We are then passing the previously processed 3 * 112 * 112 images through the trained CNN to generate feature vector for RNN to consume.


## USAGE OF THE TRAINED MODEL
 An image is passed as the CNN input and the features are extracted from the image using CNN. These extracted features are passed as input for forward pass of RNN's first LSTM unit and the input of this unit is our keyword startseq. Now the predicted RNN output is then compared with the entire vocabulary. We find the CosineSimilarity of the predicted vector with all the word vectors in vocabulary. The word with max similarity is then picked and printed. Now this becomes the input of the next LSTM and so on. We set a limit at 25 words maximum per sentence if endseq is not encountered before.
 
 ## Result and Analysis
 We have done multiple experiments by changing the size of our dataset. Due to the high complexity of the model architecture, the training time was very high. Our model took over 5 hours to run 10 iterations on dataset of 200 images. Unfortunately as a consequence of high training time, we limited our iteration count to 100. We tried 4 different sizes of dataset. The sizes used are [50, 200, 700, 1000].
 
The results for the images listed [21164875.jpg, 21166859.jpg, 31720680.jpg, 86549526.jpg, 70995350.jpg] are shown:


<img src = "https://github.com/Nikita-Chorghe/Image-Captioning-with-Deep-Networks/blob/master/Images/1.jpg"  width="500" height="600"></img>
<img src = "https://github.com/Nikita-Chorghe/Image-Captioning-with-Deep-Networks/blob/master/Images/2.jpg" ></img>
<img src = "https://github.com/Nikita-Chorghe/Image-Captioning-with-Deep-Networks/blob/master/Images/3.jpg"></img>
<img src = "https://github.com/Nikita-Chorghe/Image-Captioning-with-Deep-Networks/blob/master/Images/4.jpg"></img>
<img src = "https://github.com/Nikita-Chorghe/Image-Captioning-with-Deep-Networks/blob/master/Images/5.jpg"></img>
<img src = "https://github.com/Nikita-Chorghe/Image-Captioning-with-Deep-Networks/blob/master/Images/LSTM.png"></img>
<img src = "https://github.com/Nikita-Chorghe/Image-Captioning-with-Deep-Networks/blob/master/Images/vgg16 arch.png"></img>
<img src = "https://github.com/Nikita-Chorghe/Image-Captioning-with-Deep-Networks/blob/master/Images/word_graph.jpg"></img>

