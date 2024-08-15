# Bird Classification Project
This project aims to use a Convolutional Neural Network (CNN) to classify 15 bird species chosen from [BIRDS 525 SPECIES-IMAGE CLASSIFICATION](https://www.kaggle.com/datasets/gpiosenka/100-bird-species).  
All images are 224×224×3 color images after cropping, with cropping ensuring that the bird occupies at least 50% of the pixels in the image. Although the training dataset is not perfectly balanced, each species has at least 130 training images. Please note that the test and validation datasets each contain 5 "best" images, so it is normal to achieve better performance in validation and testing compared to training.


## Bird Species Selection
The 15 bird species are selected based on the following criteria:
1. Minimizing interspecies variation
   a. Individuals differ - Jacobin Pigeon
   b. Sexual dimorphism ( Male and female have different color and pattern ) - Ostrich
   (This is specially noted on the data source page that 80% of the images are of the males and 20% of the females.)
   c. Juvenile and adult are different - Canada Goose (Although not included in the dataset)
2. Maximizing intraspecies variation
It was noted that birds can have different postures in the images. In most images, the head is well-shown. Therefore, bill variation among different species was maximized when selecting the 15 species. - American Avocet
3. Reducing the environment noise
The images feature various environments due to the diverse habitats of the birds. Birds that are camouflaged into their environment were avoided. - Tawny FrogMouth

## Preprocessing
All images were rescaled so that each pixel would be in range of [0,1]. Augmentation (rotation, width and height shift, shear, zoom, horizontal flip) was used to avoid overfitting and increase the variation in the training image. 

## Model Creation
The following CNN model with 4 layes was used:
- **First Conv2D layer**
  - filters=32
  - kernel_size=3
  - activation='relu'
- **Second Conv2D layer** 
  - filters=64
  - kernel_size=3
  - activation='relu'
- **Third Conv2D layer**
  - filters=128
  - kernel_size=3
  - activation='relu'
- **Fourth Conv2D layer**
  - filters=256
  - kernel_size=3
  - activation='relu'
 
# INSERT MODEL SUMMARY
- The classification model performed very well, achieving an overall accuracy of 92% across 15 bird species.
- The lowest accuracy of 0.67 in Iwi, and 0.75 in Bald Eagle. Except Iwi and Bald Eagle, all precision and recall of other species exceed 0.80.
- The macro and weighted averages for precision, recall, and F1-score are all close to 0.92-0.94, confirming the model's effectiveness across the different classes.
    
## Evaluation
Model achieved around 92% accuracy on the test dataset after 22 epochs, with precision and recall all greater than 80%. However, with the training data, it only achieved 77% accuracy rate. This is because validation and test images were hand-picked to be the best image. This suggest that the model may peform worse to predict on an unseen image. 
