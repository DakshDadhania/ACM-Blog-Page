# Mathematics in Machine Learning

# Introduction

Machine Learning is a division of AI that focuses on building applications by processing available data accurately. The primary aim of machine learning is to help computers process calculations without human intervention.

The question that arises here is, so how do we feed the data to the machine? How would the machine now perform operations on this dataset and provide precise results? This is where mathematics comes into play.

To all those who are thinking, “What’s the use of learning the mathematics behind machine learning algorithms? We can easily use the widely available libraries in Python and R to build models!” While that is true, it is vital to note that these libraries and functions themselves work on the basis of mathematical concepts. Without understanding the ‘why’s’ and ‘how’s’ behind the code, one can never truly appreciate the beautiful field of Artificial Intelligence or any computer science domain for that matter.

There are four pillars of mathematical support to ML. Let us now tackle each of these, one by one.

![](https://miro.medium.com/max/1050/1*3kRFSOuCp5aL15vE_rOx7g.png)

# Linear Algebra

Linear algebra can transform datasets into matrices on which several operations can be performed.  **NumPy**  is such a library used in Machine Learning which performs several operations on N-dimensional array.

In machine learning, you fit a model on a dataset. This is the table-like set of numbers where each row represents an observation and each column represents a feature of the observation. For example, below is a snippet of the  [Iris flowers dataset](https://archive.ics.uci.edu/ml/datasets/Iris):

![](https://miro.medium.com/max/1050/1*_JPyqI3BI14oVWxF5DqvZw.png)

Iris flower dataset

This data is in fact a matrix: a key data structure in linear algebra.

Further, when you split the data into inputs and outputs to fit a supervised machine learning model, such as the measurements and the flower species, you have a matrix (X) and a vector (y). The vector is another key data structure in linear algebra.

While working with images or photographs in computer vision applications, each image that you work with is itself a table structure with a width and height and one pixel value in each cell whose value ranges from 0 to 255. In case of black and white images there is one channel and in case of RBG there are three channels. A photo is yet another example of a matrix from linear algebra. Operations on the image, such as cropping, scaling, shearing, and so on are all described using the notation and operations of linear algebra which takes us to the next section of datasets — performing operations on them.

Linear regression is a method from statistics for describing the relationships between variables. It uses a linear algebra notation — **y=Ab**. Where y is the output variable, A is the dataset and b are the model coefficients. There are many ways to describe and solve the linear regression problem, i.e. finding a set of coefficients that when multiplied by each of the input variables and added together results in the best prediction of the output variable. One such method is SVD (**Singular value decomposition)**

SVD deals with decomposing a matrix into a product of 3 matrices as shown:

![](https://miro.medium.com/max/318/1*uOUqVTdZHCk-PH6s73DsvA.jpeg)

If the dimensions of A are m x n:

-   U is an m x m matrix of Left Singular Vectors
-   S is an m x n rectangular diagonal matrix of Singular Values arranged in decreasing order
-   V is an n x n matrix of Right Singular Vector

This decomposition allows us to express our  _original matrix as a linear combination of low-rank matrices_.

![](https://miro.medium.com/max/1050/1*v16suDvxEBIHYZ8m_vmuOA.jpeg)

**Note:**  The rank of a matrix is the maximum number of linearly independent row (or column) vectors in the matrix. A vector  **r**  is said to be linearly independent of vectors  **r1**  and **r2**  if it cannot be expressed as a linear combination of  **r1**  and  **r2**. (i.e. r ≠ ar1 + br2)

Thus, the rank of a matrix can be thought of as a representative of the amount of unique information represented by the matrix. Higher the rank, higher the information.

In a practical application, you will observe that only the first few, say k, singular values are large. The rest of the singular values approach zero. As a result, terms except the first few can be ignored without losing much of the information. See how the matrices are truncated in the figure below:

![](https://miro.medium.com/max/1050/1*vsVAhvV-HLc0TUpnoP_LZA.jpeg)

Once we have established the required SVD jargon, we can use it to find approximate solutions for real-world problems. In this example, I am going to use the  [Boston house-prices dataset](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_boston.html). The house-prices data matrix A contains 506 rows (representing individual houses), and 13 columns (each describing a different characteristic of the houses). Some of these 13 features include:

· Per capita crime rate by town

· The average number of rooms per dwelling

· Weighted distances to five Boston employment centers

We want to predict the median value home price in $1000’s. These measurements are real values ranging from 5 to 50, and they represent the b vector in our system of equations Ax=b.

As usual, the matrix has many more rows than columns. This means that we cannot invert A to find the solution to Ax= b. Also, it drastically reduces the possibilities of finding a solution. Indeed, such a solution would only be possible if b is a linear combination of the columns of A. However, using the SVD, we will be able to derive the pseudo-inverse A+, to find the best approximate solution in terms of least squares — which is the projection of the vector b onto the subspace spanned by the columns of A.

Applications of SVD in Image Processing

_Face Recognition:_

1. Collect a training set of faces as the training set

2. Find the most important features by finding the directions of maximum variance — the eigenvectors or the eigenfaces.

_(Note: If non-zero e is an eigenvector of the 3 by 3 matrix A, then (Ae=λe) for some scalar. This scalar is called an eigenvalue of A. This may be rewritten as Ae=λIe and in turn as (A−λI)e=0 . The value of lambda which satisfies this equation is eigenvalue and the corresponding vector values after substituting it back into the matrix equation are the eigenvectors)_

3. Choose top M eigenfaces corresponding to the highest eigenvalues. These eigenfaces now define a new face space

4. Project all the data in this face space

5. For a new face, project it into the new face space, find the closest face(s) in the space, and classify the face as a known or an unknown face

![](https://miro.medium.com/max/1050/1*kBdOn7TPqG9xjI0bplASqg.jpeg)

Results after using above algorithm for face detection

_Special Clustering:_

[Clustering](https://www.analyticsvidhya.com/blog/2016/11/an-introduction-to-clustering-and-different-methods-of-clustering/?utm_source=blog&utm_medium=5-applications-singular-value-decomposition-svd-data-science)  is the task of grouping similar objects together. It is an unsupervised machine learning technique. Consider the below case:

![](https://miro.medium.com/max/575/1*RdAQFUG-Wwn-BCqL2qQ3XQ.jpeg)

Using SVD, we can obtain the following result.

![](https://miro.medium.com/max/575/1*BnxyDZx0nBWAKqD-xPYodg.jpeg)

These are the basic steps to obtain the above result:

-   Start with the  **Affinity matrix (A)**  or the  **Adjacency matrix**  of the data. This represents how similar one object is to another. In a graph, this would represent if an edge existed between the points or not
-   Find the  **Degree matrix (D)**  of each object. This is a diagonal matrix with entry  **_(i,i)_** equal to the number of objects object  **_i_**  is similar to
-   Find the  **Laplacian (L)**  of the Affinity Matrix:  **L = A — D**
-   Find the highest  **_k_**  eigenvectors of the Laplacian Matrix depending on their eigenvalues
-   Run **_k-means_**  on these eigenvectors to cluster the objects into k classes

# Calculus

In Machine Learning, we try to find the inputs which enable a function to best match the data. The slope or descent describes the rate of change off the output with respect to an input. Determining the influence of each input on the output is also one of the critical tasks. All this requires a solid understanding of Multivariate Calculus.

**Gradient descent algorithm:**

Let’s say you are playing a game where the players are at the top of a mountain, and they are asked to reach the lowest point of the mountain. Additionally, they are blindfolded. So, what approach do you think would make you reach the lake?

The best way is to observe the ground and find where the land descends. From that position, take a step in the descending direction and iterate this process until we reach the lowest point.

Similarly, given a cost function, the goal of the gradient descent algorithm is to minimize the given function (say cost function). To achieve this goal, it performs two steps iteratively:

1.  Compute the gradient  (slope), the first order derivative of the function at that point
2.  Make a step (move) in the direction opposite to the gradient, opposite direction of slope increases from the current point by alpha times the gradient at that point

![](https://miro.medium.com/max/413/1*qDMLaL4wyB47Kb9uZNxSmw.png)

_Alpha is called_ **_Learning rate_** _— a tuning parameter in the optimization process. It decides the length of the steps._

**Back-propagation algorithm :**

The  **Back propagation algorithm in neural network**  computes the gradient of the loss function for a single weight by the chain rule. It efficiently computes one layer at a time, output for every  **neuron**  from the input layer, to the hidden layers, to the output layer.

Let us have an artificial neural network module with n layers. Each layer ‘i’ has a weight of ‘Wi’ and outputs are calculated by matrix multiplications between inputs and weights. So, for instance, if we set up the input to the artificial neural network as ‘X0,’ then we have the output of the first layer as:

![](https://miro.medium.com/max/567/1*GhchKg5Gv1i8Cba0HK9oDQ.png)

Where ‘X0’ is the input to the module, ‘W1’ is the weight for the first layer and ‘F1’ is the activation function for the first layer. So, the output of the nth and last layer of a network can be defined as:

![](https://miro.medium.com/max/455/1*NFp6N33lolAN8NvQoHNRBw.png)

Where ‘X(n-1)’ is the input to the layer ‘n,’ ‘Wn’ is the weight for the layer ’n’ and ‘Fn’ is the activation function for the same layer. Now, let us define a loss function ‘L’ that compares the outputs ‘Xn’ with the ground truth ‘G.’ So, the error ‘E’ can be expressed as E = L(G,Xn). Differentiating with respect to weight ‘Wn,’ we get:

![](https://miro.medium.com/max/1050/1*v57KePOhgDh2sGfWqFU-pg.jpeg)

Using the same logic, we can get the generalized series for the (n-1)th layer as well. It is important to note here that ‘Wn’ does not update as soon as the gradient is calculated, it waits for the gradients of all of the weights to be calculated and then all the weights are updated together. As a result of this, the ‘Wn’ term in the in the (n-1) differential still points to the weights before the update.

# Statistics & Probability

After working on dataset and optimization next step is to analyze the result. This is where statistics — specifically, graphical representations are helpful. It gives an insight into the accuracy of the trained model. While probability in general helps us understand whether the points in our dataset are perfectly fitting, overfitting or underfitting in the model, we will discuss one algorithm in particular.

**Naive Bayes Algorithm:**

The fundamental Naive Bayes assumption is that each feature makes an:

· independent

· equal

Now, before moving to the formula for Naive Bayes, it is important to know about Bayes’ theorem. Bayes’ Theorem finds the probability of an event occurring given the probability of another event that has already occurred. Bayes’ theorem is stated mathematically as the following equation:

![](https://miro.medium.com/max/818/1*mZkrLdUqtYQyzvlTRZohDA.png)

This can be rewritten mathematically for the purpose of calculating desirable classes from a large number of datasets. For instance, if we have a dataset on the predictability of a match happening with a few parameters, it is basically bayes theorem.

![](https://miro.medium.com/max/1050/1*OW89591sTr5Q38LnGG8g-Q.jpeg)

Here x1,x2….xn represent the dependent features and y is class variable. By substituting for  **X ,** expanding using the chain rule and inserting proportionality since denominator is constant, we can obtain a function to predict results.

# Summary

Math and machine learning are inseparable. A true AI scientist always has his math right. Hope this blog gave all of you an insight on the vitality of understanding the nuances math can offer to machine learning and delve deeper into it.

# Bibliography

[cs231n.stanford.edu/slides/2018/cs231n_2018_ds02.pdf](http://cs231n.stanford.edu/slides/2018/cs231n_2018_ds02.pdf)

[LinearAlgebraSVD.pdf (upc.edu)](https://web.mat.upc.edu/toni.susin/files/LinearAlgebraSVD.pdf)

[10 Examples of Linear Algebra in Machine Learning (machinelearningmastery.com)](https://machinelearningmastery.com/examples-of-linear-algebra-in-machine-learning/)

[How to Develop a Naive Bayes Classifier from Scratch in Python (machinelearningmastery.com)](https://machinelearningmastery.com/classification-as-conditional-probability-and-the-naive-bayes-algorithm/)