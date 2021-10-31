# Age-Recognition
Predicting age form single images without facial landmarks. 

Paper used: Deep expectation of real and apparent age from a single image
without facial landmarks from Rasmus Rothe · Radu Timofte · Luc Van Gool







The idea behind the paper is to solve the problem CNN have with outliers in regression problems. The proposed model changes from regression to classification.
Basically you categorize the ages in bins (The amount of bins is treated as a hyperparameter) in either uniform or weighted distributions. The paper shows that few bins and
a weighted distribution gives good results, so thats a good starting point. We use transfer learning, using the vgg16 model trained with imagNet dataset. The output is
a softmax, with X neurons, where X is the amount of bins. We multiply the softmax distribution with a vector of means for each bin. This makes means with higher probability to have more weight than the others. Finally we sum the distribution multiplication with the means vector, and the sum is the predicted age for that picture.

![image](https://user-images.githubusercontent.com/70241561/139592716-4d0bbd5b-c9ca-4df2-a189-e9d3e195f59f.png)
![image](https://user-images.githubusercontent.com/70241561/139592723-6366188e-0e9f-4487-a077-cd227030da9e.png)
![image](https://user-images.githubusercontent.com/70241561/139592728-199218ee-4e24-4ca3-a4f6-eb0844511bcf.png)

Output explanation within the paper\



