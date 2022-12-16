# Final-Project
Classification of brain tumor



### Install
You need scikit-learn and scikit-image 

* Install the latest version of scikit-learn


      $ pip install scikit-learn --user

* Install the latest version of scikit-image


      $ pip install scikit-image --user



### Training dataset

Brain tumors are classified as : Benign Tumor, Malignant Tumor, Pituitary Tumor, etc.

***Training*** folder consists of 4 folders which contain MRI images of their cases :

> glioma_tumor
> 
> meningioma_tumor
> 
> no_tumor
> 
> pituitary_tumor


### KNeighborsClassifier

I chose ***KNeighborsClassifier*** to classify above training dataset.

> ***KNeighborsClassifier*** is the classifier algorithm that classifying the test data by calulating the closest k training data and labeling with the most frequent label among them.

Then, I used ***GridSearchCV*** to find out the best parameters as follow:


    parameters = {'n_neighbors' : [3, 5, 7], 'weights' : ('uniform', 'distance'), 'p' : [1, 2]}


After I got the best parameters form ***GridSearchCV***, I classified the training dataset with:


    KNeighborsClassifier( n_neighbors = 3, weights = 'distance', p = 1, n_jobs = -1)



### Explanation of parameters

* **n_neighbors** : int, default=5
  
  The number of neighbors to be calulated. (Also means 'K' at the KNeighborsClassifier)
  
 * **weights** : {‘uniform’, ‘distance’}, callable or None, default=’uniform’
   
   Weight function used in prediction.
   
   ‘uniform’ : uniform weights. All points in each neighborhood are weighted equally.
   
   distance’ : weight points by the inverse of their distance. in this case, closer neighbors of a query point will have a greater influence than neighbors which are further away.
   
