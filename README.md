# Image-Captioning

## Objective

The basic principle of our image-to-text model is as pictured in the diagram below, where an Encoder network encodes the input image as a feature vector by providing the outputs of the last fully-connected layer of a pre-trained CNN (we use [ResNet-152](https://arxiv.org/abs/1512.03385)). This pretrained network has been trained on the complete ImageNet dataset and is thus able to recognise common objects. 

These features are then fed into a Decoder network along with the reference captions. As the image feature dimensions are large and sparse, the Decoder network includes a linear layer which downsizes them, followed by a batch normalisation layer to speed up training. Those resulting features, as well as the reference text captions, are passed into a recurrent network (we will use an RNN). 

The reference captions used to compute loss are represented as numerical vectors via an embedding layer whose weights are learned during training.



The Encoder-Decoder network could be coupled and trained end-to-end, without saving features to disk; however, this requires iterating through the entire image training set during training. We can make the training more efficient by decoupling the networks.


<img width="947" alt="encoder_decoder_diagram(2)" src="https://user-images.githubusercontent.com/54632431/145692637-5a592a03-19d3-4230-af72-709b299aa321.png">


## Output





## Setup and resources 

Having a GPU will speed up the image feature extraction process.

This repo will use the [Flickr8k image caption dataset](http://www.jair.org/papers/paper3994.html) for image caption generation. The dataset consists of 8000 images, each of which has five different descriptions of the salient entities and activities.
