##  Age conversion
In this project, we try to simulate the function of one fashionable app: FaceApp, people put their original selfie and change their age to predict their previous or future apparence. We use  CycleGAN to realize the function that can predict in two directions, from young to old and old to young.

### How to use
Run notebook [] on colab.

### Model
Our cycleGAN model contains two mappings F: A->B and G: B->A. Given an image from domain A, we introduce a forward cycle consistency loss: A ≈ G(F(A)) and the other way around.

<div align=center><img src="https://github.com/JingC123/Age-Conversion/blob/main/imgs/cycle_gan.png/" width="600px" /></div>

### Data
We use the dataset in Kaggle: [**facial age**](https://www.kaggle.com/frabbisw/facial-age)(An image dataset consisting human faces with ages), images of 20 - 30 year old faces are taken as dataset A and 70 - 80 year sold faces as dataset B.

<div align=center><img src="https://github.com/JingC123/Age-Conversion/blob/main/imgs/dataset.png/" width="600px" /></div>
  
### Results

add image: ![name](link) or <img src="link">

### Examples

add link:  [name](link)





