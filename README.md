# Classification-Using-Logistic-Regression

## DATASET
The objective of the dataset is to diagnostically predict whether or not a patient has diabetes, based on certain diagnostic measurements included in the dataset.All patients here are females at least 21 years old of Pima Indian heritage.Predictor variables includes the number of pregnancies the patient has had, their BMI, insulin level, age, and so on.

Here, I used **Logistic Regression** for solving this clasification problem and measured its various performance metrics on the given dataset.

## RESULT
Follwing was the confusion matrix:

<img src="images/24.png"/>
<img src="images/26.png"/>

Following performance metrics were observed on the dataset by Logistic Regression:
```
Accuracy:  0.8181818181818182
Precision: 0.7567567567567568
Recall:    0.5957446808510638
```

>(1) denotes the positive class (presence of something like malignant cancer cell, diabetes,etc)

>(0) denotes the negative class and absence of things above. 

Here, we have only two classes(0=> doesn't have diabetes; 1=> has diabetes). In multiclass problems, we have multiple classes like y=0,1,2,3, etc .

- [Problems with using Linear Regression for Classification](#problems-with-using-linear-regression-for-classification) 
- [Logistic Regression](#logistic-regression)
- [Interpretation of Hypothesis Output](#interpretation-of-hypothesis-output)
- [Decision Boundary](#decision-boundary)
- [Cost Function for Logistic Regression](#cost-function)
- [Simplified Cost function](#simplified-cost-function)
- [Gradient Descent for Logistic Regression](#gradient-descent-for-logistic-regression) 
- [Multiclass Classification](#multiclass-classification)
- [Problem of Overfitting](#the-problem-of-overfitting)

### Problems with using Linear Regression for Classification 
Let's say we want to classify cancer cell as malignant or benign using Linear Regression.

<img src="images/1.png" width="300px"/>

what we can do is **set a threshold value for classification**:
<p float="left">
<img src="images/2.png" width="330px"/>
<img src="images/3.png" width="300px"/>
     </p>
  
But, if there comes a new training example to the far right(_the blue arrow_), the hypothesis function will change giving(_blue line_):

<img src="images/4.png" width="500px"/>

So, if we have the same threshold of 0.5, this will lead to a lot of wrong predictions.

There is also an **another strange thing**(and doesn't make sense) when using Linear Regression for classification problems:

For binary classification we know that y is either zero or one. But if you are using linear regression, the hypothesis can output values that are much larger than one or less than zero, even if all of your training examples have labels y equals zero or one. 

***So we use Logistic Regression Algorithm for Classification***

## LOGISTIC REGRESSION
Logistic regression is a generalized linear model (GLM). We would like our classifier to output values that are between 0 and 1. So we modify the hypothesis function from linear regression as follows:

<p float="left">
<img src="images/5.png"/>
<img src="images/6.png"/ width="700px"/>
 <p>

g(z) is called the **Sigmoid/Logistic Function** and is complex non-linear function. 

And As z goes to minus infinity, g(z) approaches zero. And as g(z) approaches infinity, g(z) approaches one. And so because g(z) upwards values are between zero and one, we also have that h(x) must be between 0 and 1.

### Interpretation of Hypothesis Output
Here, ***h(x) gives the estimated probability that y=1 on input x***

Example, we have a single feature x_1= Tumor Size and by convention x_0 is taken as 1.
<img src="images/7.png" width="330px"/>

So,
  <img src="images/8.png"/>
  
> ***logistic regression is a regression algorithm and it does predict a continuous outcome: the probability of an event. The fact that we use it as a binary classifier is due to the interpretation of the outcome.***

### Decision Boundary
The decision boundary is the line that separates the area where y = 0 and where y = 1. It is created by our hypothesis function.

In order to get our discrete 0 or 1 classification, we can translate the output of the hypothesis function as follows:

  <img src="images/9.png"/>
  
  > ***Whenever the hypothesis outputs that the probability of y being one is greater than or equal to 0.5, so this means that if there is more likely to be y equals 1 than y equals 0, then let's predict y equals 1.***
  
  <img src="images/11.png"/>
  
  <img src="images/10.png"/>

Example,

  <img src="images/12.png" width="500px"/>
  <img src="images/13.png" width="500px"/>

### COST FUNCTION
>***We cannot use the same cost function that we use for linear regression because for parameter theta, the Logistic Function will cause the output to be wavy, causing many local optima,i.e., it will not be a convex function.***

The cost function for logistic regression looks like:
  
  <img src="images/14.png"/>

>***Writing the cost function in this way guarantees that J(θ) is convex for logistic regression.***

>***But why this logarithmic cost function?***
This function comes from The Priciple of Maximum Likelihood Estimation from statistics

<p float="left">
     <img src="images/15.png" width="400px"/>
     <img src="images/16.png" width="400px" height="281px"/>
 </p>

  <img src="images/17.png"/>

### Simplified Cost Function 
The above cost function is simplified as follows:

  <img src="images/18.png" />
  <img src="images/19.png" />
    
A vectorized implementation is: 
     
  <img src="images/20.png" />
      
### Gradient Descent for Logistic Regression 
Using gradient descent minimize the cost function and simultaneously update all values in theta.

  <img src="images/21.png" />
  <img src="images/22.png" />
     
### Multiclass Classification
One-vs-all: y = {0,1...n}, we divide our problem into n+1 (+1 because the index starts at 0) binary classification problems; in each one, we predict the probability that 'y' is a member of one of our classes.

  <img src="images/23.png" />

We are basically choosing one class and then lumping all the others into a single second class. We do this repeatedly, applying binary logistic regression to each case, and then use the hypothesis that returned the highest value as our prediction.

## The Problem of Overfitting
Both Linear regression and Logistic Regression are susceptible to Overfitting(High variance) and Underfitting(High bias).

There are two main options to address the issue of overfitting:

1. Reduce the number of features:
- Manually select which features to keep.
- Use a model selection algorithm (studied later in the course).

2) [Regularization](https://towardsdatascience.com/regularization-in-machine-learning-76441ddcf99a)
- Keep all the features, but reduce the magnitude of parameters theta_j
- Regularization works well when we have a lot of slightly useful features.

