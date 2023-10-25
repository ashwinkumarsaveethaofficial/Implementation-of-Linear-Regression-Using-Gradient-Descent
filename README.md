# Implementation-of-Linear-Regression-Using-Gradient-Descent

## AIM:
To write a program to predict the profit of a city using the linear regression model with gradient descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Import the standard python libraries for Gradient design.

2.Introduce the variables needed to execute the function.

3.Use function for the representation of the graph.

4.Using for loop apply the concept using the formulae.

5.Execute the program and plot the graph.

6.Predict and execute the values for the given conditions
## Program:
```
Program to implement the linear regression using gradient descent.
Developed by: S Ashwinkumar
RegisterNumber:  212222040020
/*
Program to implement the linear regression using gradient descent.
Developed by: Thiyagarajan A
RegisterNumber:  212222240110
*/
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

data=pd.read_csv("/content/ex1.txt",header=None)

print("Profit prediction graph:")
plt.scatter(data[0],data[1])
plt.xticks(np.arange(5,30,step=5))
plt.yticks(np.arange(-5,30,step=5))
plt.xlabel("Population of City (10,1000s)")
plt.ylabel("Profit ($10,000)")
plt.title("Profit Prediction")

def computeCost(X,y,theta):
  """
  Take in a numpy array X,y,theta and generate the cost function in a linear regression model
  """
  m=len(y) #length of the training data
  h=X.dot(theta) #hypothesis
  square_err=(h-y)**2

  return 1/(2*m) * np.sum(square_err) #returning
  
  data_n=data.values
m=data_n[:,0].size
X=np.append(np.ones((m,1)),data_n[:,0].reshape(m,1),axis=1)
y=data_n[:,1].reshape(m,1)
theta=np.zeros((2,1))

print("Compute cost value:")
computeCost(X,y,theta) #Call the function

def gradientDescent(X,y,theta,alpha,num_iters):
  """
  Take in numpy array X,y and theta and update theta by taking number with learning rate of alpha

  return theta and the list of the cost of theta during each iteration
  """
  m=len(y)
  J_history=[]

  for i in range(num_iters):
    predictions=X.dot(theta)
    error=np.dot(X.transpose(),(predictions -y))
    descent=alpha * 1/m * error
    theta-=descent
    J_history.append(computeCost(X,y,theta))

  return theta,J_history  
  
theta,J_history = gradientDescent(X,y,theta,0.01,1500)
print("h(x) value:")
print("h(x) ="+str(round(theta[0,0],2))+" + "+str(round(theta[1,0],2))+"x1")

print("Cost function using Gradient Descent graph:")
plt.plot(J_history)
plt.xlabel("Iteration")
plt.ylabel("$J(\Theta)$")
plt.title("Cost function using Gradient Descent")

print("Profit prediction graph:")
plt.scatter(data[0],data[1])
x_value=[x for x in range(25)]
y_value=[y*theta[1]+theta[0] for y in x_value]
plt.plot(x_value,y_value,color="r")
plt.xticks(np.arange(5,30,step=5))
plt.yticks(np.arange(-5,30,step=5))
plt.xlabel("Population of City (10,000s)")
plt.ylabel("profit ($10,000)")
plt.title("Profit Prediction")

def predict(x,theta):
  """
  Take in numpy array of x and theta and return the predicted value of y based on theta
  """

  predictions= np.dot(theta.transpose(),x)

  return predictions[0]
  
predict1=predict(np.array([1,3.5]),theta)*10000
print("Profit for the population 35,000:")
print("For population = 35,000, we predict a profit of $"+str(round(predict1,0)))

predict2=predict(np.array([1,7]),theta)*10000
print("Profit for the population 70,000:")
print("For population = 70,000, we predict a profit of $"+str(round(predict2,0)))



```

## Output:
![image](https://github.com/ashwinkumarsaveethaofficial/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/120731469/9b3ea740-6978-4eb7-aeba-d16cce45ae5e)

### compute cost value
![image](https://github.com/ashwinkumarsaveethaofficial/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/120731469/da02b685-9d34-4e44-b282-b52f22adf481)

### h(x) value:
![image](https://github.com/ashwinkumarsaveethaofficial/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/120731469/bfedb5e3-680b-4459-ae62-f53388d45713)

### cost function using gradient descent graph
![image](https://github.com/ashwinkumarsaveethaofficial/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/120731469/45f3079b-000c-4a10-87f7-5f5b33223684)

### profit prediction graph
![image](https://github.com/ashwinkumarsaveethaofficial/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/120731469/f0daddf4-f504-49f8-8e4b-d2e36a9e6365)

### profit for the population 35000:
![image](https://github.com/ashwinkumarsaveethaofficial/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/120731469/32600920-0381-4e58-a81b-f711fbaa3a36)

### profit for the population 70000:
![image](https://github.com/ashwinkumarsaveethaofficial/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/120731469/78d6b32b-6130-4124-a651-336e809c2fbe)


## Result:
Thus the program to implement the linear regression using gradient descent is written and verified using python programming
