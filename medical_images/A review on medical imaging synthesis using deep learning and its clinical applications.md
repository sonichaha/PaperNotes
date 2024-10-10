# Structure
- Abstract
- Introduction
- Literature Search
- Deep Learning Methods
- Application Area
- Summary and Outlook

# Abstract
- Topics:
  - review of medical imaging synthesis and its clinical application
- Methodology
  - summerize deep learning‐based methods in inter‐ and intra‐modality image synthesis
  - list and highlight the proposed methods, study designs, and reported performances with related clinical applications

# Introduction
- why studied image synthesis?
  - Its primary purpose is to facilitate the clinical work- flow by bypassing or replacing an imaging procedure when acquisition is infeasible due to constraints on time, labor, or expense.
- how do they review?
  - categorize the recent literature based on their deep learn- ing methods and highlighted their contributions.
  - Clinical applications are surveyed with identification of pertinent limitations and chal- lenges.

# Literature Search
- what is image synthesis
  - Inter‐modality: image synthesis between two different imaging modalities
  - intra‐modality: transform images between two dif- ferent protocols of the same imaging modality, such as between MRI sequences, or the restoration of images from a low‐quality protocol to a high‐quality protocol.

# Deep Learning Methods
- Categories:
  - Auto‐encoder (AE)
    - unsupervised learning
    - Input layer, bottleneck layer, output layer
    - The loss function used during training is typically a reconstruction loss, measuring the difference between the input and the reconstructed output. Common choices include mean squared error (MSE) for continuous data or binary cross-entropy for binary data.
    - During training, the autoencoder learns to minimize the reconstruction loss, forcing the network to capture the most important features of the input data in the bottleneck layer.
    - learns to extract features and compress the images.
  - U‐net
    - a contracting path(encoder): capture contextual information and reduce the spatial resolution of the input
    - a expansive path(decoder): upsample the feature maps to scale the image (interpolating).
    - output the probability of each pixel
  - Generative adversarial network (GAN)
    - Discriminator(AE):
      - The discriminator classifies both real data and fake data from the generator.
      - The discriminator loss penalizes the discriminator for misclassifying a real instance as fake or a fake instance as real.
      - The discriminator updates its weights through backpropagation from the discriminator loss through the discriminator network.
    - Generator(AE or U-net):
      - random input
      - generator network, which transforms the random input into a data instance
      - discriminator network, which classifies the generated data
      - discriminator output
      - generator loss, which penalizes the generator for failing to fool the discriminator