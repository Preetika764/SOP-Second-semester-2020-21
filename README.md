# SOP-Second-semester-2020-21

Done as part of my SOP for second semester 2020-21

INTRODUCTION

Adversarial examples are inputs designed to fool machine learning models. They result in 
incorrect output from the neural network. These examples pose security threats for 
applications.
Adversarial training is the process of explicitly training a model on adversarial examples, 
in order to make it more robust to attack or to reduce its test error on clean inputs. 
In white box attacks, the attacker has access to the model’s parameters, while in black 
box attacks, the attacker has no access to these parameters. For the latter, the attacker 
uses a different model or no model at all to generate adversarial images with the hope that 
these will transfer to the target model. 
There are two kinds of attacks -
1. Non-targeted attacks - Enforce the model to misclassify the adversarial image
2. Targeted attacks - The attacker pretends to get the image classified as a specific 
   target class, which is different from the true class.
   
There were two parts in this project-

1. Generating adversarial images using different attack methods

   An inceptionv3 model, pretrained on the ImageNet dataset has been used. An image is 
   fed and is classified as an Egyptian cat by the model. The probability(confidence) of 
   classification for this label is .701695. To this image, noise is added, generating 
   adversarial images by different attack methods.
      a. Fast Gradient Sign method - The value of epsilon is chosen as 0.02. The sign of the gradient of the loss function is calculated with respect to the input                                        image. The input image is modified according to the formula to generate the adversarial image. This is then fed to the model                                        and is classified. Different values of epsilon are used to see how the classification and confidence varies as we increase the 
                                     perturbations.
                                     
      b. One step target class method - The leopard class in the ImageNet Dataset is chosen as the target class. Different values of epsilon - 0.002, 0.01, 0.15,                                           0.5 are chosen.
      
      c. Basic Iterative method - The number of iterations chosen is 5 and in each iteration, we add some perturbation to the image. This generates the final                                         adversarial image. 
      
      d. Iterative Target Class Method - The target class is ostrich. The value of epsilon chosen is 0.25 and the number of iterations is 5. 

2. Quantifying how similar two images are 

   This takes two images and calculates how similar they are based on the Euclidean 
   distance between feature vectors. A ResNet model, pretrained on the ImageNet dataset is 
   used. For each input image, the predict() function returns probability for each outcome 
   class as a value between 0 and 1. This is the feature vector. All possible combinations of 
   pairs of images are taken and the Euclidean distance is calculated for the two feature 
   vectors. For each image, the more similar it is to any particular image, the less the value 
   of Euclidean distance should be. For each test image, it returns the image it is most 
   similar to and the Euclidean distances with all other images.
