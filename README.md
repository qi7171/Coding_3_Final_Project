# DCGAN Style Transfer
The goal of this project is to train a Deep Convolutional Generative Adversarial Network (DCGAN) to generate portrait paintings. After generating, I apply abstract art style transfer techniques to the generated portraits. 

Colab: https://colab.research.google.com/drive/13pHFgujf8P33GUtKZbDkJ6a_ifJAtpJm?usp=sharing


### Dataset used:
Portrait: https://www.kaggle.com/datasets/deewakarchakraborty/portrait-paintings

abstract art style: https://www.kaggle.com/datasets/greg115/abstract-art

abstract art checkpoints: https://www.kaggle.com/datasets/therealcyberlord/abstract-art-generation-dcgan-checkpoints

### Code References:
DCGAN model: https://www.kaggle.com/code/frabbisw/dcgan-faces

DCGAN model with checkpoints: https://www.kaggle.com/code/qi7171/dcgan-faces/edit

Neural style transfer: https://www.kaggle.com/code/sayakdasgupta/neural-style-transfer-using-vgg19

Debugging and proofreading code: ChatGPT

### What I have done:
Changing new dataset for DCGAN and Neural style transfer model

Done experimentation such as epochs and batch size for the existing code of DCGAN and Neural style transfer model, and found that higher numbers of epochs converge to better solutions and generate higher-quality images.

Combining DCGAN model with neural style transfer model



## Design and development processes

### Dataset Preparation
<img width="1080" alt="Screenshot 2023-06-14 at 12 06 59" src="https://github.com/qi7171/Coding_3_Final_Project/assets/72468017/0f8d9bd9-3b93-436a-b53c-1f2e51c6df0e">
For dataset preparation, exploring different datasets posed challenges, and I encountered failures when attempting to switch datasets, such as the dataset size(small datasets can't train a good model), and dataset compatibility(some datasets are not compatible with the DCGAN code I used). It's crucial to ensure that the chosen dataset is properly formatted and contains a sufficient number of portrait paintings for effective training. I modified the DCGAN code to work with a dataset of portrait paintings from Kaggle instead of the original abstract generation dataset. 

### DCGAN Model Selection
![1](https://github.com/qi7171/Coding_3_Final_Project/assets/72468017/656ec333-490b-4ad6-a8aa-f3bcbe78b13f)

I choose to train my new dataset of portrait paintings using this DCGAN model(https://www.kaggle.com/code/frabbisw/dcgan-faces). However, I have noticed that the generated images have low resolution and poor quality. I believe this issue arises due to compatibility problems between the dataset and the DCGAN model.

To address this, I decided to try an alternative DCGAN model that has been specifically trained on a checkpoints dataset. The results obtained from this model have been satisfactory, demonstrating better effect with abstract art style.

By switching to a DCGAN model trained on a checkpoints dataset, which likely shares similar characteristics with my portrait paintings dataset, I have been able to overcome the compatibility issues and achieve improved results.


### Train DCGAN
![real image](https://github.com/qi7171/Coding_3_Final_Project/assets/72468017/412ca40e-c001-4de6-aace-831597003300)
After making modifications to the DCGAN code, I trained the model using the portrait paintings dataset. ChatGPT helped me analyse the existing code, identify potential errors, and provide suggestions for debugging.

During the training process, I saved the generated fake images from the DCGAN into a folder. This allows me to analyze and evaluate the quality of the generated images later on.


### Style Transfer
![styletransfer](https://github.com/qi7171/Coding_3_Final_Project/assets/72468017/cbfcdec6-e197-4c27-a194-d512387a4f4c)

Once the DCGAN training is complete, I have a collection of generated fake images, I applied neural style transfer using a pre-trained VGG19 model. The style transfer process involves combining the content of the generated images with the abstract art style from the style dataset downloaded from Kaggle.

The final result of applying style transfer to the generated fake images is a set of images that combine the content of the portraits with the abstract art style, creating unique and visually appealing outputs.


## Challenges encountered
DCGAN and style transfer models require substantial computational power and memory. Working with high-resolution images results in longer training times or potential resource limitations. 

I tried modifying the batch size from 32 to 128, which is unlikely to directly influence the image resolution or quality. Then I focused on training for more epochs instead. However, it's worth noting that the choice of batch size can indirectly impact the image resolution or quality through its effects on the training process. For example:

### Epochs=10
![epochs10](https://github.com/qi7171/Coding_3_Final_Project/assets/72468017/f1ae8d58-8b6c-4d75-9c88-e9437e63da03)

### Epochs=50
![real image](https://github.com/qi7171/Coding_3_Final_Project/assets/72468017/9fdf8ed8-e54e-4e6d-9634-110604bc79a4)

### Epochs=150
![epochs150](https://github.com/qi7171/Coding_3_Final_Project/assets/72468017/d13e1137-2e64-4df7-a18c-977490337a73)

The number of epochs can indeed influence the resolution and quality of the images generated by DCGAN and style transfer models. I trained the model with a higher number of epochs allowing it to learn more complex features and patterns from the training data, potentially resulting in higher-resolution outputs. As training progresses, the model refines its representations and generates images with improved details and sharper features. Therefore, running the training for more epochs, such as 150 epochs compared to just 10 epochs, gives the model more opportunities to converge to better solutions and generate higher-quality images.

However, it's worth noting that simply increasing the number of epochs doesn't guarantee better results. Finding the most optimised number of epochs is important.




