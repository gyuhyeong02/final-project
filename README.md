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


### 3. Classification with KNeighborsClassifier

I chose ***KNeighborsClassifier*** to classify above training dataset.

> ***KNeighborsClassifier*** is the classifier algorithm that classifying the test data by calulating the closest k training data and labeling with the most frequent label among them.

Then, I used ***GridSearchCV*** to find out the best parameters as follow:


    parameters = {'n_neighbors' : [3, 5, 7], 'weights' : ('uniform', 'distance'), 'p' : [1, 2]}


After I got the best parameters form ***GridSearchCV***, I classified the training dataset with them:


* To use train data more, I defined the test size with 0.1
    
    
      X_train, X_test, y_train, y_test = sklearn.model_selection.train_test_split(X, y, test_size=0.1, random_state=42)
    
* Standardize with StandardScaler
    
      scaler = sklearn.preprocessing.StandardScaler()
      X_train_scaled = scaler.fit_transform(X_train)
      X_test_scaled = scaler.transform(X_test)
    
* Training

      rf = sklearn.neighbors.KNeighborsClassifier( n_neighbors = 3, p = 1, weights = 'distance', n_jobs = -1)
      rf.fit(X_train_scaled, y_train)
    
* Check Accuracy
      
      y_pred = rf.predict(X_test_scaled)
      print('Accuracy: %.2f' % sklearn.metrics.accuracy_score(y_test, y_pred))

  Accuracy was 0.87


### 4. [Explanation of parameters](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsClassifier.html#sklearn.neighbors.KNeighborsClassifier.kneighbors)


* **n_neighbors** : *int, default=5*

  I modified it with 3 that means it will see the closest 3 training data for each test data.
  
  
* **weights** : *{‘uniform’, ‘distance’}, callable or None, default=’uniform’*
   
  Since there are 4 labels, 'distance' would be better for multiclass classifying.
  
  When you use 'distance', closer neighbors of a query point will have a greater influence than neighbors which are further away.

* **p** : *int, default=2*

   Since I modified the value of 'p' with 1, it uses the 'manhattan distance'.
   
   When you use 'manhattan distance', the distance between two points is the sum of the absolute differences of their Cartesian coordinates.

* **n_jobs** : *int, default=None*

  'n_jobs = -1' means using all processors 
