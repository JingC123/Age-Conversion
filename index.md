## Implementing CycleGAN for Age Conversion
### Video
<video src="demo.mov" width="320" height="200" controls preload></video>
### Abstract

In this project, our goal is to learn an unpaired image-to-image translation and predict what people look like decades later or before. Our model contains two mappings F: A->B and G: B->A. Given an image from domain A, we introduce a forward cycle consistency loss: A ≈ G(F(A)) and the other way around. 

### Problem statement

In this project, we try to simulate the function of one fashionable app: FaceApp, people put their original selfie and change their age to predict their previous or future apparence. GANs were mostly implemented to achieve this purpose in the past, and can only speculate in one direction, from young to old or from old to young, so we use the GAN-based architecture: CycleGAN to realize the function that can predict in two directions, from young to old and old to young.

### Related work

**Cycle-Consistent Adversarial networks (CycleGANs)**: CycleGANs are neural networks that involve the automatic training of image-to-image translation models without paired input/output. The models are trained using a collection of images from the source and target domain that don’t need to be one-to-one correspondence any way.

**Generative adversarial networks (GANs)**: GANs are neural networks that are trained in an adversarial manner to solve image-to-image translation problems, such as style transfer, since they depend on the unconstrained input set and output set rather than specific corresponding input/output pairs. A GAN has two parts in it: generator that generates images and discriminator that classify the real and fake images and the generator learns to deceive the discriminator and makes the discriminator unable to learn to classify properly.
  <div align=center><img width="650" src="/Age-Conversion/imgs/gan.png"/></div>

**Dataset**: We use the dataset in Kaggle: [facial age](https://www.kaggle.com/frabbisw/facial-age) (An image dataset consisting human faces with ages), images of 20 - 30 year old faces are taken as dataset A and 70 - 80 year sold faces as dataset B, at the same time, the images of the A and B datasets are not in a one-to-one correspondence. 80% of each dataset is a training set and the remainder is a testing set.

### Methodology

We implemented a CycleGAN program in Jupyter Notebook, and then trained and tested our model in Google Colab. In our model, we used two generators and two discriminators. One generator transforms data from A to B. Then discriminator B compares the generated data with sample data to get GAN loss and identity loss. The generated B is then used to generate A by the other generator. The generated A is also evaluated by a discriminator. A cycle consistency loss is also recorded in the cycle process. The model is trained in this cycle process of generating and discriminating A and B.
  <div align=center><img width="650" src="/Age-Conversion/imgs/cycle_gan.png"/></div>

### Experiments/evaluation

We do two experiments, one is reverting from young to old, and the other is reverting from old to young. We evaluate the results with identity loss, Gan loss, cycle consistency loss and then add them together.

### Results

We trained the model and got the generator loss near 3, the generator identity loss near 0.5, the cycle loss near 1, and discriminator loss near 0.2. The GAN loss is increasing during the training, while the discriminator loss shows a linear reduction and all other losses shows an exponential reduction.
We used the trained model to generate several testing pictures. Some of them showed good results of age shifting, which is described in the examples section.


<p align="center">
  <img width="400" src="/Age-Conversion/imgs/loss_G.png"/>
  <img width="400" src="/Age-Conversion/imgs/loss_G_identity.png"/>
</p>
  
<p align="center">
  <img width="400" src="/Age-Conversion/imgs/loss_G_GAN.png"/>
  <img width="400" src="/Age-Conversion/imgs/loss_G_cycle.png"/>
</p>
  
<p align="center">
  <img width="400" src="/Age-Conversion/imgs/loss_D.png"/>
</p>

### Examples

From old to young:
<p align="center">
  <img width="200" src="/Age-Conversion/imgs/o2y_1o.png"/>
  <img width="200" src="/Age-Conversion/imgs/o2y_1y.png"/>
</p>

<p align="center">
  <img width="200" src="/Age-Conversion/imgs/o2y_2o.png"/>
  <img width="200" src="/Age-Conversion/imgs/o2y_2y.png"/>
</p>

In the “youngify” process, we noticed that wrinkles are lightened and the skin looks better. In many cases, whitened hairs are also turned back to darker colors.

From young to old:
<p align="center">
  <img width="200" height="200" src="/Age-Conversion/imgs/y2o_1y.png"/>
  <img width="200" height="200" src="/Age-Conversion/imgs/y2o_1o.png"/>
</p>

<p align="center">
  <img width="200" height="200" src="/Age-Conversion/imgs/y2o_2y.png"/>
  <img width="200" height="200" src="/Age-Conversion/imgs/y2o_2o.png"/>
</p>

The “oldify” process is like a reverse to the previous. Wrinkles are added to the face. Hairs are whitened. The skin also looks a little more pale. We even noticed that the teeth in the pictures are also turned into a more aged condition.

### Codes

[https://github.com/JingC123/Age-Conversion/blob/main/model.ipynb](https://github.com/JingC123/Age-Conversion/blob/main/model.ipynb)

### References
[A clean and readable Pytorch implementation of CycleGAN](https://github.com/aitorzip/PyTorch-CycleGAN)

[Torch implementation for learning an image-to-image translation without input-output pairs](https://github.com/junyanz/CycleGAN/)

[Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networks](https://arxiv.org/pdf/1703.10593.pdf)

[Understanding and Implementing CycleGAN in TensorFlow](https://hardikbansal.github.io/CycleGANBlog/)

[An introduction to Generative Adversarial Networks (with code in TensorFlow)](https://aylien.com/blog/introduction-generative-adversarial-networks-code-tensorflow)

[A Gentle Introduction to CycleGAN for Image](https://machinelearningmastery.com/what-is-cyclegan/)

[Translationmachinelearningmastery.com › what-is-cyclegan](https://machinelearningmastery.com/what-is-cyclegan/)

[Understanding Generative Adversarial Networks](https://naokishibuya.medium.com/understanding-generative-adversarial-networks-4dafc963f2ef#:~:text=A%20GAN%20can%20be%20trained,digit%20images%20from%20MNIST%20database.&text=A%20GAN%20has%20two%20parts,classifies%20real%20and%20fake%20images)
