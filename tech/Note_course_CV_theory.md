# AWS Course: "Seeing Clearly: Computer Vision Theory"
### Amazon Rekognition
- searchable image library, Image Moderation, Sentiment Analysis, etc.
- best practice: 
  - Image format (PNG or JPEG)
  - Max size (S3: 15 MB, API calls 5 MB base64 encoded)
  - Video format (mp4, mov), Video codec (H264)
  - Max video size (8GB)
  - Image solution (min 80 px)
  - Collections are faces (not cats, cartoons, ...)
  - Max number of faces (20 million)
  - Max matching faces return 4096
  - Keep image to re-index collection for future verions
  - IndexFaces detects largest 100 faces in the input image and adds them to the specified collection
  - SearchFaceByImage detects the largest face in the image, and then searches the specified collection for maching faces
  - Avoid false positive by not indexing blurry or low quality images
 
### AWS DeepLens
- Wireless-enabled camera and development platform integrated with AWS
- Offer the deep learning capability to develop computer vision applications
- Supported deep learning frameworks: MXNet, TensorFlow, Caffe
- 

### localization techniques: tell us local information about an image (what, where, how many)
- object detection
- semantic segmentation (e.g. medical images)
  - with deep learning
  - per-pixel classification
  - different from **Instance Segmentation**
  - Input: image array (H x W x C)
    - height, width, pixel channel (C=1 for greyscale, 3 for RGB)
    - unsigned integer (0-255)
  - Output: Mask array
    - same spatial resolution (H x W)
    - integer values for pixel class or one-hot encoded e.g. (H x W x N) N = # of classes
 - Semantic segmentation architecture
  - encoder to decoder
  -  U-Net, a fully convolutional autoencoder with Skip Connections
 - Loss function
  - classification: categorical cross-entropy (CE)
  - semantic segmentation: average categorical cross-entropy
    - alternatively, dice-coefficient

- Issues in practice
  - FCN models are computationally expensive (difficult to train on high-res images)
    - Down-sampling not ideal (label meaning lost)
    - Solution: train on crops of high-res images (FCN spatially independent)
  - Convolutional only cares about the local information
    - Class imbalance. e.g. weight loss function, spatial imbalance
    - Solution: crop from positive window
    - Every window has a full positive sample
## Amazon Machine Learning Stack
- Application services: Rekognition, Transcribe, Translate, Polly, Comprehend, Lex
- Platform services: Amazon SageMaker
- Frameworks & Interfaces - AWS Deep Learning AMIs: Caffe2, CNTK, Apache MXNet, PyTorch, TensorFlow, Chainer, Keras, Gluon, etc.

## Satellite Image Classification in SageMaker
- Amazon SageMaker: a fully managed service that enables data scientists and developers to quickly and easily build machine-learning based models into production of smart applications.
  - Build: pre-built notebook instances, highly-optimized machine learning algorithms
  - Train: one-click training for ML, DL and custom algorithms, easier training with hyperparameter optimization
  - Deploy: Deployment without engineering effft, fully-managed hosting at scale

### Convolution Fundamentals (interactive illustration: https://www.cs.ryerson.ca/~aharley/vis/)
  - **Filters** detect patterns, edges, shapes, textures, etc. 
    - A filter is a small matrix with a given number of columns and rows and the same depth as the input data
    - low level features: edge detection
    - mid level features: shapes (circles, squares, triangles)
    - High level features: buildings, Roads, Automobiles ....
