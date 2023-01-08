[![Prerna Mittal](https://miro.medium.com/fit/c/96/96/0*vM5VQyvVUXfS9lHp)

](https://medium.com/@prernaharshi3403?source=post_page-----58ad4877e042--------------------------------)[Prerna Mittal](https://medium.com/@prernaharshi3403?source=post_page-----58ad4877e042--------------------------------)Follow

Mar 24, 2022

·12 min read

Decoding the world of Python libraries
======================================

> **_Introduction_**

Evolution of Artificial Intelligence and Machine Learning in the modern world has led to extensive development in the field of technology enabling categorization of data, fraud detection , recognition of images, or predictions about the future (among other things).

Python libraries play a very vital role in fields of Machine Learning, Data Science, Data Visualization, etc. This is a reusable chunk of code that one can include in one’s programs/ projects. It is a collection of modules that can be installed using a package manager like rubygems or npm. Other than pre-compiled codes, a library may contain documentation, configuration data, message templates, classes, and values, etc. This enables smooth, high-efficiency programming, convenient programming.


Python Libraries

Here’s a list of six widely used and popular libraries for aspiring developers.

*   SciPy
*   PyTorch
*   Pandas
*   NumPy
*   TernsorFlow
*   MatPlotLib

Each section under every library describes its features and applications in addition to basic information and it’s syntax at a glance. We hope you enjoy exploring these with us.

> **_SciPy_**

SciPy is a free and open-source machine learning library used for high level computations by application developers. SciPy has around 19,000 comments on GitHub and an active community of about 600 contributors. It’s extensively used for scientific and technical computations, because it extends NumPy and provides many user-friendly and efficient routines for scientific calculations. However, one can differentiate between the SciPy library and SciPy stack. SciPy library contains modules for optimization, linear algebra, integration, and statistics.

**_Features Of SciPy :_**

*   The main feature of the SciPy library is that it is developed using NumPy. Hence the collection of algorithms and functions built on the NumPy extension of Python.
*   In addition, SciPy provides all the efficient numerical routines like optimization, numerical integration, and many others using its specific submodules.
*   All the functions in all submodules of SciPy are well documented.
*   High-level commands for data manipulation and visualization
*   Multidimensional image processing with the SciPy ndimage submodule
*   Includes built-in functions for solving differential equations

**_Applications of SciPy :_**

*   SciPy is a library that uses NumPy for the purpose of solving mathematical functions. SciPy uses NumPy arrays as the basic data structure, and comes with modules for various commonly used tasks in scientific programming.
*   Tasks including linear algebra, integration (calculus), ordinary differential equation solving and signal processing execute easily by SciPy.
*   Multidimensional image operations can be carried out.
*   Solving differential equations and the Fourier transform can be done.
*   Optimization algorithms can be implemented
*   Linear algebra can be performed

**_Understanding SciPy:_**

*   Obtaining information about any function can be done using **help()**. However this can be performed with or without parameters.

_Code -_

```
from scipy import clusterhelp(cluster) #with parameterhelp() #without parameter
```

To stop execution of this function ‘quit’ and enter can be used.

*   **scipy.io** package provides a number of functions that help you manage files of different formats such as MATLAB files, IDL files, Matrix Market files, etc.

_Code -_

```
import scipy.io as sio
```

*   **info()-** Returns information about the desired function. While **source() returns objects written solely in python.** Useful information cannot be obtained if objects are written in other languages such as java.

_Code -_

```
scipy.info(cluster) scipy.source(cluster)
```

*   Solving exponential and trigonometric functions can be done with SciPy’s special package. Many more operations like integration, double integration etc can also be performed.

_Code -_

```
from scipy import speciala= special.exp10(3)print(a)b= special.exp2(3)print(b)c= special.sindg(90)print(c)d= special.cosdg(45)print(d)
```

_Output -_

```
1000.08.01.00.7071067811865475
```

**_Optimization of functions_**

*   Unconstrained and constrained minimization of multivariate scalar functions i.e _minimize_ (eg. BFGS, Newton Conjugate Gradient, Nelder\_mead simplex, etc)
*   Global optimization routines (eg. differential\_evolution, dual\_annealing, etc)
*   Least-squares minimization and curve fitting (eg. least\_squares, curve\_fit, etc)
*   Scalar univariate functions minimizers and root finders (eg. minimize\_scalar and root\_scalar)
*   Multivariate equation system solvers using algorithms such as hybrid Powell, Levenberg-Marquardt.
*   Rosenbrook function (_rosen_) is a test problem used for gradient-based optimization algorithms. It is defined as follows in SciPy:

_Code -_

```
import numpy as npfrom scipy.optimisze import rozena= 1.2\* np.arrange(5)rozen(a)
```

_Output -_

```
7371.0399999999945
```

Many more operations like correlation, convolution, etc can be carried out with ease and efficiency using SciPy making it a wonderful library for developers.

**Website link:** [https://scipy.org/](https://scipy.org/)

**GitHub link:** [https://github.com/scipy](https://github.com/scipy/scipy)

> **_Pytorch_**

Next in the list of top python libraries for data science is PyTorch, this is a Python-based scientific computing package that uses the power of graphics processing units. Python is a preferred programming language due to its simplicity, productivity and portability. It’s syntax it’s simpler when compared to Java and C++ among others.

PyTorch is one of the most commonly used deep learning research platforms built to provide maximum flexibility and speed.

**_Features Of PyTorch:_**

*   **Hybrid Front-End-** A new hybrid front-end provides ease-of-use and flexibility in eager mode, while seamlessly transitioning to graph mode for speed, optimization, and functionality in C++ runtime environments.
*   **Distributed Training-** Optimize performance in both research and production by taking advantage of native support for asynchronous execution of collective operations and peer-to-peer communication that is accessible from Python and C++.
*   **Python First-** PyTorch is not a Python binding into a monolithic C++ framework. It’s built to be deeply integrated into Python so it can be used with popular libraries and packages such as Cython and Numba.
*   **Libraries And Tools-**An active community of researchers and developers have built a rich ecosystem of tools and libraries for extending PyTorch and supporting development in areas from computer vision to reinforcement learning.

**_Applications of PyTorch:_**

*   PyTorch is famous for providing two of the most high-level features
*   It enables tensor computations with strong GPU acceleration support
*   Helps in building deep neural networks on a tape-based autograd system
*   PyTorch is primarily used for applications such as natural language processing.
*   It is primarily developed by Facebook’s artificial-intelligence research group and Uber’s “Pyro” software for probabilistic programming is built on it.
*   PyTorch is outperforming TensorFlow in multiple ways and it is gaining a lot of attention in recent days.

**_Understanding PyTorch:_**

*   In PyTorch, every method that ends with an underscore (\_) makes changes in-place, meaning, they will modify the underlying variable.
*   Sending tensors( three dimensional arrays) to specified devices including GPU can be done with — **to()**
*   In any case if one desires the code back to CPU due to unavailability of GPU **cuda.is\_available()** can be used to find out if a GPU is available at your disposal. It can also be casted to a lower precision(32 bit float) using **float().** While **type()** reveals its location.
*   Autograd is PyTorch’s automatic differentiation package. Partial derivatives, chain rule everything is taken care of. Manual computation gradients can be avoided with the usage of **zero\_()** and **backward ().**
*   PyTorch can build a dynamic computation graph from every python operation that involves any gradient-computing tensor or it’s dependencies. A tensor is a three dimensional array.
*   **torch.no\_grad()** enables updation of parameters with changing the dynamic computation graph. Regular python operations can now be performed on tensors.
*   PyTorch’s DataLoader can be dictated to use a dataset,the desired mini batch-size or if one would like to shuffle the data. This is like an iterator that can be looped and different mini-batches can be obtained.

_Code (_Creating two tensors of 2 x 3 dimensions each) -

```
import torchx= torch.tensor( \[ \[1,2,3\], \[4,5,6\] \] )y = torch.tensor ( \[ \[7,8,9\], \[10,11,12\] \] )f= 2\*x + yprint(f)
```

_Output:_

```
( \[ \[ 9, 12,15\],\[ 18,21,24\] \] )
```

This was a simple illustration to enable better understanding. In addition to these many more operations can be carried out to develop efficient Deep Learning models using PyTorch.

**Website link:** [https://pypi.org/project/pandas/](https://pypi.org/project/pandas/)

**GitHub link:** [https://github.com/pandas-dev/pandas](https://github.com/pandas-dev/pandas)

> **_Pandas_**

As technology enthusiasts we understand how complicated operations can get. Looking forward to simplified execution of data with minimal commands in addition to Re-indexing, Iteration, Sorting, Aggregations, Concatenations and Visualizations the Pandas machine learning library provides all these tools to enable smooth and efficient programming.

Created by Wes Mckinney, with around 1700 comments on GitHub and an active community of 1200 contributors this enables high productivity, flexibility in addition to offering extremely responsive data structures.

**_Features of Panda:_**

*   Eloquent syntax and rich functionalities that gives one the liberty to manage missing data.
*   It enables creation of your own functions and flexibility to run it across a series of data.
*   High-level abstraction
*   Its high-level data structures and elementary manipulation of simple operations make it a real time- saver.

**_Applications of Panda:_**

*   General data wrangling and data cleaning
*   ETL (extract, transform, load) jobs for data transformation and data storage, as it has excellent support for loading CSV files into its data frame format
*   Used in a variety of academic and commercial areas, including statistics, finance and neuroscience.
*   Time-series-specific functionality, such as date range generation, moving window, linear regression and date shifting.

**_Understanding Pandas:_**

Data scientists are responsible for processing, cleaning, and validation of integrated data.

This can often be a very tiring process. However with Pandas:

```
nba.info ()
```

This produces a list of all columns in the dataset and type of data each column contains. Although one can store arbitrary Python in object data type, we are aware of drawbacks. Strange values in an object column can harm Pandas performance and it’s interoperability with other libraries.

*   Accessing DataFrame elements: The DataFrame consists of a series of objects which can be used to access the elements. The crucial difference is addition of dimension of the DataFrame. Indexing operator for the columns and the access methods .loc and .iloc for rows can be used.
*   For instance-Adjusting the numeric value stored in one column of a data set. Without writing a loop “u-func” can apply changes.

_Code -_

```
dataFrame\[“colName”\] = dataFrame\[“ colName”\] / 2
```

*   Filtration of data can be tedious.

However with Pandas: To find females above the age of 45 following can be implemented with ease.

_Code -_

```
\# Return rows only where the “female” field is True and “age” is > 45adult\_females = dataFrame\[ ( dataFrame\[“female”\] == True) & ( dataFrame\[“age”\] > 45
```

Pandas has various other features among these for creating new series of data to accessing components making it the ultimate hack for aspiring data scientists.

**Library link:** [https://pypi.org/project/pandas/](https://pypi.org/project/pandas/)

**GitHublink:** [https://github.com/pandas-dev/pandas](https://github.com/pandas-dev/pandas)

> **_NumPy_**

NumPy (Numerical Python) is a library for the Python programming language, adding support for large, multi-dimensional arrays and matrices, along with an extensive collection of high-level mathematical functions to operate on these arrays. It has the benefits of smaller memory consumption and faster runtime behavior. It has uses in various other developing fields like machine learning and data science. We can also combine it with other libraries to further enhance its applications.

**_Features of NumPy:_**

*   High-performance N-dimensional array object.
*   It contains tools for integrating code from C/C++ and Fortran.
*   It contains a multidimensional container for generic data.
*   Additional linear algebra, Fourier transform, and random number capabilities.
*   It consists of broadcasting functions. It broadcasts the shape of smaller arrays according to the larger ones.
*   It had data type definition capability to work with various databases.

**_Applications of NumPy:_**

*   Numpy with Pandas is used for faster computations. When we use both the libraries together it is a very helpful resource for scientific computations.
*   NumPy with Pandas is used to generate the graphs of the results. We enhance it further with the use of graphic toolkits like PyQt and wxPython.
*   NumPy with SciPy is used to generate the graphs of the results. We enhance it further with the use of graphic toolkits like PyQt and wxPython.
*   The use of Tkinter along with NumPy is user friendly. We can easily convert the array objects into image objects.

**_Understanding NumPy:_**

*   Shape Manipulations  — Users can change array dimensions at runtime if the output produces the same number of elements. We apply **_np.reshape(…)_**  function on the array. The reshape function is useful for performing various operations. For example, we use it to broadcast two dissimilar arrays.
*   Array Generation — We can generate array data set for implementing various functions. We can also generate a predefined set of numbers for the array elements using the **_np.arrange(…)_**  function. Reshape function is useful to generate a different set of dimensions.
*   Array Dimensions **—** Numpy consists of both one and multidimensional arrays. Some functions have restrictions on multidimensional arrays. It is then necessary to transform those arrays into one-dimensional arrays. We can transform multi-dimensional to single dimension using **_np.ravel(..)_**

_Code- Single Dimensional NumPy Array_

```
import numpy as npa=np.array(\[1,2,3\])print(a) — \[1 2 3\]
```

_Ouput -_

```
\[1 2 3\]
```

_Code- NumPy array occupies less memory as compared to list_

```
import numpy as npimport timeimport sysS= range(1000)print(sys.getsizeof(5)\*len(S))D= np.arange(1000)print(D.size\*D.itemsize)
```

_Output -_

```
140004000
```

The above output shows that the memory allocated by list (denoted by S) is 14000 whereas the memory allocated by the NumPy array is just 4000. From this, you can conclude that there is a major difference between the two and this makes Python NumPy array as the preferred choice over list.

**Library Link**: [https://numpy.org/install/](https://numpy.org/install/)

**GitHub Link**:[https://github.com/numpy/numpy](https://github.com/numpy/numpy)

> **_TensorFlow_**

TensorFlow is a free and open-source software library for machine learning and artificial intelligence. It can be used across a range of tasks but has a particular focus on the training and inference of deep neural networks. TensorFlow can be used in a wide variety of programming languages, most notably Python, as well as Javascript, C++, and Java. This flexibility lends itself to a range of applications in many different sectors.

**_Features of TensorFlow:_**

*   AutoDifferentiation: It is the process of automatically calculating the gradient vector of a model with respect to each of its parameters
*   TensorFlow includes an “eager execution” mode, which means that operations are evaluated immediately as opposed to being added to a computational graph which is executed later.
*   TensorFlow provides an API for distributing computation across multiple devices with various distribution strategies.
*   To train and assess models, TensorFlow provides a set of loss functions. These loss functions compute the “error” or “difference” between a model’s output and the expected output.
*   In order to assess the performance of machine learning models, TensorFlow gives API access to commonly used metrics.
*   TensorFlow offers a set of optimizers for training neural networks, including ADAM, ADAGRAD, and Stochastic Gradient Descent (SGD).

**_Applications of TensorFlow:_**

*   Image recognition: It is used by Mobile companies, social media, and other telecom houses. Image recognition consists of pixel and pattern matching to identify the image and its parts.
*   Voice Recognition: It is done using Automatic speech recognition which is trained using TensorFlow. These systems convert the human voice into text or computer understandable code by digitizing it.
*   Video Detection: Here uses of TensorFlow include self-driving car systems, automation, and many automotive machines.
*   Text-based applications: The text messages, reactions, comments, tweets, stock results etc are a means of data. This processing of data is done using TensorFlow for the analysis purpose and reaching the expected sales.

**_Understanding TensorFlow:_**

The first argument should be tensors, followed by basic Python parameters. The last argument is name with a default value of None. Operations should contain an extensive Python comment with Args and Returns declarations that explain both the type and meaning of each value. Possible shapes, dtypes, or ranks should be specified in the description.

_Code -_

```
\# Import \`tensorflow\`import tensorflow as tf# Initialize two constantsx1 = tf.constant(\[1,2,3,4\])x2 = tf.constant(\[5,6,7,8\])  
\# Multiplyresult = tf.multiply(x1, x2)# Print the resultprint(result)
```

_Output -_

```
Tensor(“Mul:0”, shape=(4,), dtype=int32)
```

**Library Link**: [https://www.tensorflow.org/install](https://www.tensorflow.org/install)

**GitHub Link**: [https://github.com/tensorflow](https://github.com/tensorflow)/

> **_MatPlotLib_**

Matplotlib is a plotting library for the Python programming language and its numerical mathematics extension NumPy. It provides an object-oriented API for embedding plots into applications using general-purpose GUI toolkits. Matplotlib is designed to be as usable as MATLAB, with the ability to use Python, and the advantage of being free and open-source.

**_Features of MatPlotLib :_**

*   Semantic way to generate complex, subplot grids.
*   Setting the aspect ratio of the axes box.
*   Colored labels in legends.
*   Ticks and labels.
*   rcParams can be passed as Decorators.
*   3D plots now support minor ticks

**_Applications of MatPlotLib :_**

*   Create publication quality plots.
*   Make interactive figures that can zoom, pan, update.
*   Customize visual style and layout.
*   Export to many file formats .
*   Embed in JupyterLab and Graphical User Interfaces.
*   Use a rich array of third-party packages built on Matplotlib.

**_Understanding MatPlotLib :_**

*   **_matplotlib.pyplot.figure: Figure_** is the top-level container. It includes everything visualized in a plot including one or more  _Axes_.
*   **_matplotlib.pyplot.axes_**_:_ **_Axes_** contain most of the elements in a plot**:** _Axis, Tick, Line2D, Text,_  etc., and sets the coordinates. It is the area in which data is plotted. Axes include the X-Axis, Y-Axis, and possibly a Z-Axis, as well.

_Code -_

Creating your first plot — The Figure is the first step and the key to unlocking the power of this package. Next, you see that you initialize the axes of the Figure in the code chunk above with fig.add\_axes():

```
\# Import \`pyplot\`  
import matplotlib.pyplot as plt  
\# Initialize a Figure   
fig = plt.figure()  
\# Add Axes to the Figure  
fig.add\_axes(\[0,0,1,1\])
```

_Output -_

```
<matplotlib.axes.\_axes.Axes at 0x7f98466de4a8>
```

**Library Link**: [https://matplotlib.org/stable/users/installing/index.htm](https://matplotlib.org/stable/users/installing/index.htm)l

**GitHub Link**:[https://github.com/matplotlib/matplotlib](https://github.com/matplotlib/matplotlib)

> **_Conclusion_**

In this blog, you learned about the best Python libraries for machine learning. Python libraries and packages are a set of useful modules and functions that minimize the use of code in our daily lives. There are over 137,000 libraries and 198,826 packages for Python, ready to make developer programming easier. These libraries and packages are intended for a variety of modern solutions.

Every library has its own positives and negatives. These aspects should be taken into account before selecting a library for the purpose of machine learning and the model’s accuracy should also be checked after training and testing the models so as to select the best model in the best library to do your task. And may this help you in keeping up with the growing popularity and development of the Python programming language.

> **Authors**

Kashin Mittal & Prerna Mittal
