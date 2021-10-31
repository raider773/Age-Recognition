# Age-Recognition
Predicting age form single images without facial landmarks. 

Paper used: Deep expectation of real and apparent age from a single image
without facial landmarks from Rasmus Rothe · Radu Timofte · Luc Van Gool







The idea behind the paper is to solve the problem CNN have with outliers in regression problems. The proposed model changes from regression to classification.
Basically you categorize the ages in bins (The amount of bins is treated as a hyperparameter) in either uniform or weighted distributions. The paper shows that few bins and
a weighted distribution gives good results, so thats a good starting point. We use transfer learning, using the vgg16 model trained with imagNet dataset. The output is
a softmax, with X neurons, where X is the amount of bins. We multiply the softmax distribution with a vector of means for each bin. This makes means with higher probability to have more weight than the others. Finally we sum the distribution multiplication with the means vector, and the sum is the predicted age for that picture.The paper also gives some tips as for training the model. Reducing learning rate every 10 epochs by a factor of 10, or some values to try with weight decay.

![image](https://user-images.githubusercontent.com/70241561/139592716-4d0bbd5b-c9ca-4df2-a189-e9d3e195f59f.png)\
![image](https://user-images.githubusercontent.com/70241561/139592723-6366188e-0e9f-4487-a077-cd227030da9e.png)\
![image](https://user-images.githubusercontent.com/70241561/139592728-199218ee-4e24-4ca3-a4f6-eb0844511bcf.png)\
Output explanation within the paper
\
\

![image](https://user-images.githubusercontent.com/70241561/139592776-27562a68-01bc-406c-b1e5-34a1175aca5a.png)\
Comparation of MAE values with uniform or balanced bins distribution, as well as the output of neurons.(the amount of bins)
\
\

![image](https://user-images.githubusercontent.com/70241561/139592841-830daf39-d917-4ff1-b910-6bc15fd784e7.png)\
Data Sample
\
\


![image](https://user-images.githubusercontent.com/70241561/139592853-05a457c6-80dc-4d54-9bf9-77ff1c26cbf7.png)\
![image](https://user-images.githubusercontent.com/70241561/139592863-c1cf9e31-59e8-41b2-b27e-17d984c4fe2c.png)\
implementation of the Model

\
\

![image](https://user-images.githubusercontent.com/70241561/139592889-3413f504-e3c8-4747-8348-bd9ce9f0154f.png)\
Losses and Scores

\
\


![image](https://user-images.githubusercontent.com/70241561/139592907-4b0db7c0-a68f-43c7-96eb-f9bac1fdf22e.png)\
![image](https://user-images.githubusercontent.com/70241561/139592935-b96217f6-73bd-498a-b398-4c992dd02ac3.png)\

Implementation of the learning rate decay for every 10 epochs by a factor of 10


