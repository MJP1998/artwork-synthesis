# Realistic Artwork Synthesis

I conducted this project with Valentin Braux-Guillin under the supervision of Professor Maks Ovsjanikov.

The goal was to propose an implementation of ArtGAN, the conditional categorical Generative Adversarial Network (GAN) introduced in the research paper of Tan, Chan, Aguirre and Tanaka. It is an extension of the original GANs to synthetically generate more complex images of artwork with abstract characteristics. 

## Model 

We implemented the model from [arxiv](https://arxiv.org/abs/1702.03410).

The generator is made of 2 parts : zNet and the decoder :

<img width="660" alt="Generateur" src="https://user-images.githubusercontent.com/64918024/133895768-1017e296-69a9-450e-9fba-ffa03dc88e18.png">

The discriminator is also separated between the encoder and clsNet :

<img width="660" alt="Discriminateur" src="https://user-images.githubusercontent.com/64918024/133895788-b91cd39c-37a3-4584-a85c-54fb063272dd.png">

We trained it on the dataset WikiArt, using the losses described in the paper : the classical loss used for GANs and the custom one between encoder and decoder shown below. 

![artgan_model](https://user-images.githubusercontent.com/64918024/133896268-f31d23bb-b5e4-4c48-9a5d-88112680768d.jpg)


We differentiated the artworks in 3 ways to imitate human learning :

* by styles (80,000 images, 27 classes)
* by genres (60,000 images, 10 classes)
* by artist (20,000 images, 23 classes)


## Results

Some results of the model, trained on images classified by genres are shown below.

![results](https://user-images.githubusercontent.com/64918024/133896228-7de6e8c2-c35f-4adc-a2a5-2dd68d4c68b7.png)

When estimating the results, we obtained a log likelihood of 1041 ± 17 a lower score than the one in the paper.
The results were estimated using parzen windows estimation. 

To further improve it, we propose to add some dropout layers to avoid overfitting on some classes. Maybe further diminishing the learning rate could also help improving the model.



