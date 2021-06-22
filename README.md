# GAN_Image_Compression
Different ways of Image Compression using Machine Learning-
## Image compression using PCA
The principal components, when sorted in the order of their eigenvalues, preserve most of the information in the dataset within the first principal component, the rest in the second, and so on. Thus, we can preserve most of the details in an image by applying PCA. We can detect the number of principal components required to preserve variance by a certain percentage—say, 95% or 98%—and then apply PCA to transform the data space. All the steps mentioned above will be followed in the same manner, and in the end we can create the compressed image by using this transformed data space. It’s very space-efficient, since an image with nm pixels or dimensions (say 2828=784) can be preserved by a very small number of principal components (just around 20–30).

## Image compression using k-means clustering
As discussed earlier in this post, image compression, in some techniques, involves reducing the color components of the image. With k-means clustering, this is what we’re doing. We pre-define the value of k as the number of color components that we want to preserve in the image. The rest of the k-means algorithm is performed according to the above-mentioned steps. With an increase in the value of k, as the number of clusters increases, the image will get closer and closer to the original image, but at the cost of more disk space for storage and a higher computational cost. We can experiment with the values of k to get desirable results. We can also calculate the within-cluster sum of squared error to gain insight on whether the clusters are well fitted and correctly assigned or not, since it provides us with the variance of the cluster centroids. Note: It’s advised to keep the value of k as a multiple (more preferably, a power) of 2, same as the conventional image formats, to get better results.

## Image compression using GANs
The CGAN is used similarly to an encoder-decoder model, such that the encoder encrypts the information in the image in a latent map by compressing the image and limiting the number of color components, and then this map is used by the decoder (generator) to develop a compressed image according to the information provided. With the help of an encoder E and a quantized value q, we encode the image i to get a compressed representation of the image as w = q(E(i)). The decoder/generator G then tries to generate an image i= G(z) that’s consistent with the image distribution Px and also resembles the original image to a certain degree.
