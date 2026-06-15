##### **Introduction to computer vision concepts:-**



Computer vision is the set of AI tasks and techniques that let software process visual input from images, video, or live camera streams to extract meaningful information.



**Use cases of the computer vision:-**



1. Image classification — Predict a single label that describes the main subject of an image; requires large labeled training sets; good for single‑item recognition. ex:- identify each item in grocery store during checkout



2\. Object detection — Find multiple objects and their locations in an image; outputs object classes plus bounding boxes for each detected instance. ex:- identify different item when a group of grocery items are placed in front of camera during checkout



3\. Semantic segmentation — Classify each pixel so the model produces precise object shapes and boundaries rather than coarse boxes. example:- identify the shape and size of fruits by pixel and based on that identify the object.



4\. Contextual image analysis (multimodal models) — Models that link image content with text to interpret scenes, describe activities, or suggest tags. 



###### **Images and image processing:-**



1. **Image Representation**

&#x09;a. Pixels and resolution — An image is a 2D array of pixel values; resolution = rows × columns. 

&#x09;b. Grayscale vs color — Grayscale uses a single channel (0–255); typical color images use three channels (Red, Green, Blue), each a same‑sized array. 



**2. Color Channels**

&#x09;a. RGB channels — Each pixel’s final color is the combination of its R, G, B channel values (e.g., purple = R:150, G:0, B:255). 

&#x09;b. Interpretation — Treat channels as stacked 2D arrays; many vision models accept multi‑channel tensors as input. 



**3. Filters and Kernels**

&#x09;a. Filter kernel — A small matrix (e.g., 3×3) of weights used to transform local patches of the image. 

&#x09;b. Common effects — Different kernels produce blurring, sharpening, color inversion, or edge highlighting (example: Laplace filter). 



4\. **Convolution Process**



&#x09;a. How it works — Slide the kernel across the image; for each patch compute the weighted sum of pixel × kernel weight and write the result to the output image. 

&#x09;b. Value range and clipping — Convolution results can fall outside 0–255 and must be adjusted/clipped back into the valid pixel range. 

&#x09;c. Padding and borders — Edges require padding (commonly zeros) because kernels cannot fully overlap border pixels. 





###### **Convolutional neural networks:-**



Convolutional neural networks (CNNs) are a common deep learning architecture for computer vision that use learnable filters to extract numeric feature maps from images and feed those features into a classifier to predict image labels. 



**How a CNN processes images**

1. Input and filters: Images are fed into convolutional layers where small filter kernels slide over the image to produce feature maps that highlight local patterns. 

2\. Downsampling: Pooling or other down‑sampling layers reduce feature map size and emphasize the most important features. 

3\. Flattening and classification: Feature maps are flattened into a vector and passed through fully connected layers; the output layer (often softmax) produces class probabilities. 



**Training process (what to remember)**



1. Initialization: Filter weights start with random values. 

2\. Loss and backpropagation: Predicted probabilities are compared to true labels to compute loss; gradients update both the classifier weights and the convolutional filter weights to reduce loss over many epochs. 

3\. Model saving and inference: After training converges, learned weights are saved and used to predict labels for new images. 



###### **Vision transformers and multimodal models:-**



Transformers, originally developed for language, encode tokens as vector embeddings using attention; the same approach can be applied to images by encoding image patches as tokens. This enables vision transformers (ViT) and, when combined with language encoders, multimodal models that link visual features and text. 



1. **How transformers encode semantics**



&#x09;a. Token embeddings — Transformers convert discrete tokens into high‑dimensional vectors that capture contextual meaning via attention. 

&#x09;b. Attention mechanism — Attention weights model relationships between tokens so semantically related tokens have similar vector directions. 



2\. **Vision transformers (ViT)**



&#x09;a. Patch tokens — Images are split into patches; each patch is flattened and projected into an embedding vector that the transformer processes like a token. 

&#x09;b. Visual embeddings — Embeddings capture visual attributes such as color, shape, texture, and contextual co‑occurrence (for example, hat features often co‑occur with head features). 



3\. **Multimodal models**



&#x09;a. Combining encoders — A language encoder and a vision encoder produce separate embedding spaces that can be aligned. Cross‑model attention creates a unified representation linking visual features to language. 

&#x09;b. Capabilities — The unified embedding space lets the model generate rich image descriptions, match images to text, and reason about visual–textual relationships without explicit symbolic understanding. 



###### **Image generation:-**



Modern image generation uses multimodal models that map natural language prompts to visual features, then synthesize images that match those features. 



**How generation works**



Iterative denoising — Many models use diffusion: start from random pixels and iteratively remove noise while steering the image toward features implied by the prompt. After each iteration the model evaluates how well the current image matches the prompt and refines it. 



**Key model concepts**



&#x09;a. Prompt → visual features: The prompt is used to identify a set of visual attributes that the model should combine. 

&#x09;b. Evaluation loop: At each denoising step the model compares the intermediate image to the prompt and adjusts generation accordingly. 



**Video generation differences**



Temporal and physical consistency — Video synthesis extends the same feature‑matching idea but must also enforce temporal coherence and plausible physical behavior (for example, consistent object motion and contact with the ground).

