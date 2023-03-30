# Developing a Neural Network Regression Model

## AIM

To develop a neural network regression model for the given dataset.

## THEORY

Neural networks consist of simple input/output units called neurons (inspired by neurons of the human brain). These input/output units are interconnected and each connection has a weight associated with it. Neural networks are flexible and can be used for both classification and regression. In this article, we will see how neural networks can be applied to regression problems.

Regression helps in establishing a relationship between a dependent variable and one or more independent variables. Regression models work well only when the regression equation is a good fit for the data. Most regression models will not fit the data perfectly. Although neural networks are complex and computationally expensive, they are flexible and can dynamically pick the best type of regression, and if that is not enough, hidden layers can be added to improve prediction.

First import the libraries which we will going to use and Import the dataset and check the types of the columns and Now build your training and test set from the dataset Here we are making the neural network 2 hidden layer with activation layer as relu and with their nodes in them. Now we will fit our dataset and then predict the value.
## Neural Network Model
![Uploading 226164790-c96d8074-ba9a-4511-b86a-d69e6b61dc5d.png…]()


## DESIGN STEPS

### STEP 1:

Loading the dataset

### STEP 2:

Split the dataset into training and testing

### STEP 3:

Create MinMaxScalar objects ,fit the model and transform the data.

### STEP 4:

Build the Neural Network Model and compile the model.

### STEP 5:

Train the model with the training data.

### STEP 6:

Plot the performance plot

### STEP 7:

Evaluate the model with the testing data.

## PROGRAM

```
NAME : charumathi R
REG NO : 212222240021
        
### To Read CSV file from Google Drive :

from google.colab import auth
import gspread
from google.auth import default
import pandas as pd

## To train and test 
from sklearn.model_selection import train_test_split

## To scale 
from sklearn.preprocessing import MinMaxScaler

## To create a neural network model
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense

### Authenticate User:

auth.authenticate_user()
creds, _ = default()
gc = gspread.authorize(creds)

### Open the Google Sheet and convert into DataFrame :

worksheet = gc.open('My Dataset').sheet1
rows = worksheet.get_all_values()
df = pd.DataFrame(rows[1:], columns = rows[0])


df = df.astype({'Input':'float'})
df = df.astype({'Output':'float'})

df

x=dataset1[['INPUT']].values
y=dataset1[['OUTPUT']].values

x
y

x_train,x_test,y_train,y_test= train_test_split(x,y,test_size = 0.4, random_state =35)
Scaler = MinMaxScaler()
Scaler.fit(x_train)
X_train1 = Scaler.transform(x_train)
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
ai_brain = Sequential([
    Dense(8,activation='relu'),
    Dense(10,activation='relu'),
    Dense(1)
])
ai_brain.compile(optimizer = 'rmsprop' , loss = 'mse')
ai_brain.fit(X_train1 , y_train,epochs = 2005)

loss_df = pd.DataFrame(ai_brain.history.history)
loss_df.plot()

X_test1 =Scaler.transform(X_test)
ai_brain.evaluate(X_test1,y_test)
X_n1=[[4]]
X_n1_1=Scaler.transform(X_n1)
ai_brain.predict(X_n1_1)
```

## Dataset Information
![226168229-6a5244f9-42f2-4592-acfa-78a9e3bbeec0](https://user-images.githubusercontent.com/120204455/228892430-48547c0d-7632-4d24-91bb-dda1c17f7c4b.png)

## OUTPUT

### Training Loss Vs Iteration Plot
![226168464-67a8912f-4784-42b5-935f-b66be1dd4f05](https://user-images.githubusercontent.com/120204455/228892585-6f4bf91a-b9fe-454a-b820-88fe5bc04d9b.png)

### Test Data Root Mean Squared Error
![226168511-634fcabb-cad9-4161-bb33-b07d9e7eb623](https://user-images.githubusercontent.com/120204455/228892689-2386cd10-23d6-466e-9fe2-52b2c267eb71.png)
![226168536-da17fe3c-fa77-402e-af29-716efc23c3ed](https://user-images.githubusercontent.com/120204455/228892761-2ad2ba61-6b03-4fe7-81d5-d6478a4dcda8.png)

### New Sample Data Prediction
![226168557-30aca09d-4b93-41f4-9d30-083927da89e9](https://user-images.githubusercontent.com/120204455/228892820-a8553822-e6ee-46c7-a8fc-74d7b8930654.png)


## RESULT
Thus a neural network regression model for the given dataset is written and executed successfully

