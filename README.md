# Final-Project
Classification of brain tumor



### 1. Install
You need scikit-learn and scikit-image 

* Install the latest version of scikit-learn


      $ pip install scikit-learn --user

* Install the latest version of scikit-image


      $ pip install scikit-image --user



### 2. Training dataset

Brain tumors are classified as : Benign Tumor, Malignant Tumor, Pituitary Tumor, etc.

***Training*** folder consists of 4 folders which contain MRI images of their cases :

> glioma_tumor
> 
> meningioma_tumor
> 
> no_tumor
> 
> pituitary_tumor


### 3. KNeighborsClassifier

I chose ***KNeighborsClassifier*** to classify above training dataset.

> ***KNeighborsClassifier*** is the classifier algorithm that classifying the test data by calulating the closest k training data and labeling with the most frequent label among them.

Then, I used ***GridSearchCV*** to find out the best parameters as follow:


    parameters = {'n_neighbors' : [3, 5, 7], 'weights' : ('uniform', 'distance'), 'p' : [1, 2]}


After I got the best parameters form ***GridSearchCV***, I classified the training dataset with:


    KNeighborsClassifier( n_neighbors = 3, weights = 'distance', p = 1, n_jobs = -1)



### 4. [Explanation of parameters](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsClassifier.html#sklearn.neighbors.KNeighborsClassifier.kneighbors)


* **n_neighbors** : int, default=5

  I modified it with 3 that means it will see the closest 3 training data for each test data.
  
  
* **weights** : {‘uniform’, ‘distance’}, callable or None, default=’uniform’
   
  Since there are 4 labels, 'distance' would be better for multiclass classifying.
  

* **p** : int, default=2

   Since I modified the value of 'p' with 1, it uses the 'manhattan distance'.

* **n_jobs** : int, default=None

  'n_jobs = -1' means using all processors 
