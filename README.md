# Implementation-of-Linear-Regression-Using-Gradient-Descent

## AIM:
To write a program to predict the profit of a city using the linear regression model with gradient descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Initialize Parameters – Set initial values for slope m and intercept 𝑏 and choose a learning rate 𝛼
2.Compute Cost Function – Calculate the Mean Squared Error (MSE) to measure model performance.
3.pdate Parameters Using Gradient Descent – Compute gradients and update m and b using the learning rate.
4.Repeat Until Convergence – Iterate until the cost function stabilizes or a maximum number of iterations is reached 

## Program:
/*
Program to implement the linear regression using gradient descent.
Developed by: NITHISH S
RegisterNumber:  212224240105
*/
import numpy as np
import pandas as pd 
from sklearn.preprocessing import StandardScaler

def linear_regression(X1, y, learning_rate=0.1, num_iters=1000):
    X=np.c_[np.ones(len(X1)),X1]
    
    theta=np.zeros(X.shape[1]).reshape(-1,1)
    
    for _ in range(num_iters):
        predictions=(X).dot(theta).reshape(-1,1)
        
        errors=(predictions-y).reshape(-1,1)

        theta -=learning_rate*(1/len(X1))*X.T.dot(errors)
    return theta

data=pd.read_csv("/content/50_Startups.csv")
data.head()
X=(data.iloc[1:,:-2].values)
X1=X.astype(float)

scaler=StandardScaler()
y=(data.iloc[1:,-1].values).reshape(-1,1)
X1_Scaled=scaler.fit_transform(X1)
Y1_Scaled=scaler.fit_transform(y)
print(X)
print(X1_Scaled)
theta=linear_regression(X1_Scaled, Y1_Scaled)
new_data= np.array([165349.2 , 136897.8 , 471784.1]).reshape(-1,1)
new_scaled=scaler.fit_transform(new_data)
prediction=np.dot(np.append(1, new_scaled), theta)
prediction= prediction.reshape(-1,1)
pre = scaler.inverse_transform(prediction)
print(prediction)
print(f"Predicted value: {pre}")

## Output:
![image](https://github.com/user-attachments/assets/599f5870-75af-431d-b84f-7aba3eb781c3)
![image](https://github.com/user-attachments/assets/9c2fc717-af3a-42c2-9880-9ed28c989ea2)
![image](https://github.com/user-attachments/assets/3a79db65-a07a-449d-9000-eb75be942004)
![image](https://github.com/user-attachments/assets/b07e1fec-c0e9-4704-8dd2-b685daf9b788)
![image](https://github.com/user-attachments/assets/f684ddcc-13d4-401d-9d23-65917c9aae4e)
![image](https://github.com/user-attachments/assets/4267c257-bbe8-4919-a8eb-197509e5d845)

Result:
Thus the program to implement the linear regression using gradient descent is written and verified using python programming



