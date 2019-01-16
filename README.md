# Classification-Using-Logistic-Regression

The objective of the dataset is to diagnostically predict whether or not a patient has diabetes, based on certain diagnostic measurements included in the dataset.All patients here are females at least 21 years old of Pima Indian heritage.Predictor variables includes the number of pregnancies the patient has had, their BMI, insulin level, age, and so on.

Here, I used **Logistic Regression** for solving this clasification problem and measured its various performance attributes on the given dataset.

## RESULT
Following performance attributres were observed on the dataset by Logistic Regression:
```
Accuracy:  0.8181818181818182
Precision: 0.7567567567567568
Recall:    0.5957446808510638
```



## LOGISTIC REGRESSION
>(1) denotes the positive class (presence of something like malignant cancer cell, diabetes,etc)

>(0) denotes the negative class and absence of things above. 

Here, we have only two classes(0/1). In multiclass problems, we have multiple classes like y=0,1,2,3, etc .

### Problems with using Linear Regression for Classification 
Let's say we want to classify cancer cell as malignant or benign using Linear Regression.

![](images/1.png)
