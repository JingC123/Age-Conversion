## Implementing CycleGAN for Age Conversion

### Abstract

In this project, our goal is to learn an unpaired image-to-image translation and predict what people look like decades later or before. Our model contains two mappings F: A->B and G: B->A. Given an image from domain A, we introduce a forward cycle consistency loss: A ≈ G(F(A)) and the other way around. 

### Problem statement

In this project, we try to simulate the function of one fashionable app: FaceApp, people put their original selfie and change their age to predict their previous or future apparence. GANs were mostly implemented to achieve this purpose in the past, and can only speculate in one direction, from young to old or from old to young, so we use the GAN-based architecture: CycleGAN to realize the function that can predict in two directions, from young to old and old to young.

### Related work

**Cycle-Consistent Adversarial networks (CycleGANs)**: CycleGANs are neural networks that involve the automatic training of image-to-image translation models without paired input/output. The models are trained using a collection of images from the source and target domain that don’t need to be one-to-one correspondence any way.

**Generative adversarial networks (GANs)**: GANs are neural networks that are trained in an adversarial manner to solve image-to-image translation problems, such as style transfer, since they depend on the unconstrained input set and output set rather than specific corresponding input/output pairs. A GAN has two parts in it: generator that generates images and discriminator that classify the real and fake images and the generator learns to deceive the discriminator and makes the discriminator unable to learn to classify properly.
![Image](https://github.com/JingC123/Age-Conversion/blob/main/imgs/cycle_gan.png?raw=true)

**Dataset**: We use the dataset in Kaggle: facial age (An image dataset consisting human faces with ages), images of 20 - 30 year old faces are taken as dataset A and 70 - 80 year sold faces as dataset B, at the same time, the images of the A and B datasets are not in a one-to-one correspondence. 80% of each dataset is a training set and the remainder is a testing set.
(Link:https://www.kaggle.com/frabbisw/facial-age)
```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/JingC123/Picture-Style-Transfer/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
