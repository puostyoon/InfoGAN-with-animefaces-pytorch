# InfoGAN-with-animefaces-pytorch
InfoGAN using animeface dataset

InfoGAN (https://arxiv.org/abs/1606.03657) is able to learn disentangled representations in a completely unsupervised manner.
This infoGAN is trained by animeface dataset from (https://www.kaggle.com/datasets/soumikrakshit/anime-faces)

There are three versions.

version1: infoGAN using 1 discrete latent variables and 2 continuous latent variables.

version2: infoGAN using 10 discrete latent variables, and 2 continuous latent variables.

version3: infoGAN using 10 discrete latent variables, and 20 continuous latent variables. 


Each discrete latent variable is a categorical distribution with 10-dimension. (i.e an example of discrete latent variable is [0, 0, 0, 0, 1, 0, 0, 0, 0, 0] )

One discrete latent variable was unable to catch character identity(who the character is). It seems that because there are too many variants(different hair color, different eye sizes, different drawing styles, and so on) in anime-face dataset, a discrete latent code was not enough to catch the character identity of the datasets, and therefore the model is trained to ignore latent variables.

Therefore, I used 10 discrete latent variables, and by varying all of 10 discrete latent variable concurrently, the model successfully cached character identity.
Similarly, two continuous latent codes were not enough to catch continous variation of data. In this case, using 20 continuous latent codes were also not enough to catch continuous variation. Fixing all 20 continuous latent codes made same results as the result made by varying all 20 continous latent codes, which means continuous variation was only decided by noise variable z.

# Usage
make 'checkpoint' directory where your code(.ipynb) exists
make 'data/anime' directory where your code(.ipynb) exists, and in the directory, make your own folder and place anime face data in that folder you made.
In the code, you can see Config block. All hyperparameters including 'num_epochs' is tuned by me to perform at best. Try with your own hyperparameters, but remember that too many epochs will lead the model to cause 'mode collapse' which is a prevailing problem in GANs.
In the second block of the code, you shold set root directory.
Then, run your code until last block.
In the last block of the code, you shold set directory to load your parameters saved during train.
Then, run your final block, which generates images.

# Result
result of version 1

![화면 캡처 2022-04-23 114937](https://user-images.githubusercontent.com/104057435/164870670-1a40b981-9741-4232-8b0a-e0cc5f84e2d7.png)

result of version 2

![Epoch_230 Anime](https://user-images.githubusercontent.com/104057435/164868815-323d793b-295b-4719-9143-0970c2bcf40f.png)

result of version 3

![Epoch_360 Anime](https://user-images.githubusercontent.com/104057435/164868699-03903a9f-6549-4305-85ee-f83714ff9289.png)

# Reference
1. Xi Chen, Yan Duan, Rein Houthooft, John Schulman, Ilya Sutskever, Pieter Abbeel. InfoGAN: Interpretable Representation Learning by Information Maximizing Generative Adversarial Nets. https://arxiv.org/abs/1606.03657
2. pianomania/infoGAN-pytorch https://github.com/pianomania/infoGAN-pytorch
3. Natsu6767/InfoGAN-PyTorch https://github.com/Natsu6767/InfoGAN-PyTorch
4. DCGAN pytorch tutorial https://pytorch.org/tutorials/beginner/dcgan_faces_tutorial.html
 
