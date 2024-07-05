---
layout: post
title: "An Actor-Model Framework For Visual Sensory Encoding (digital twin)"
date: 2024-07-05
categories: literature-reviews
---

**Citation:**
Liu, X., Karsh, B., & Rieke, F. (2022). An Actor-Model Framework For Visual Sensory Encoding. *Journal of Neuroscience*, 42(10), 1234-1245. https://doi.org/10.1523/JNEUROSCI.1234-22.2022

**TLDR**
The issue in neuroengineering is determining artifical inputs for a sensory system that will output the desired perception. Researchers implemented an actor-model framework using two convolutional neural networks (CNNs) to create a digital twin of a mouse retina for improving downsampling. Downsampling is important because sensory systems or prosthetics cannot ingest high resolution images. The actor network downsampling conserves more important vital information than the traditional systems. 


**Methods:**
Step 1: 
- Project high resolution images to mouse retinas and detect neural spides in response to image projection 
- Average the number of spikes
- Combined the recorded response spike vectors across many retinas into a neural response matrix

Step 2: 
- train a CNN to act as a digital twin of the retina, this is called a forward model: 

$$ \mathcal{F} = X \rightarrow \hat{Y} $$

- Send the same high resolution images to the forward model. This creates the prediction matrix $\hat{y}$. 
- Calculate the poisson loss between the ground truth and the prediction.
- Use that to update the forwrd model along with the regularization terms 

$$ \theta^* = argmin_{\theta}[L(\hat{\mathcal{F}}(X), \mathcal{F}, R]) $$

where $\theta^*$ is the optimized parameters of $\hat{\mathcal{F}}$, $l$ is the loss function, and $R$ is the regularization term. 

- Then conduct hyperparameter tuning with random search. 
- Fix weights for the forward model. 

Step 3: 
- Prepend another CNN, the actor network A: $X \rightarrow X_{down}$ where $ X \in \mathbb{R}^{32x32}$, which learns to downsample images.
- Repeat steps from step 2 for training
- As the actor model A is trained, it learns to distill pertinent features to down sample images while generating a neuronal response similar to high resolution images. 

**Architecture specifications:**
- **Data:** Description of the dataset(s) used in the study.
- **Techniques:** Overview of the methodologies and techniques applied.
- **Architecture:** Details on any specific models or architectures used.


