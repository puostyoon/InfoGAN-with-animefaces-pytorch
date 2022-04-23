# InfoGAN-with-animefaces
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
