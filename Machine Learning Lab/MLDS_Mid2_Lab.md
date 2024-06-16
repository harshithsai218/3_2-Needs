# Week 6

Implementing Backpropagation algorithm and test the same using appropriate datasets

The backpropagation algorithm is a supervised learning technique used in artificial neural networks to optimize weights. It involves two main steps: forward propagation and backward propagation. In forward propagation, inputs are passed through the network to generate an output. The output is then compared to the target value, and an error is calculated. During backward propagation, this error is propagated back through the network, adjusting the weights by gradient descent to minimize the error. This process iteratively updates the weights to improve the network's performance. Backpropagation is essential for training deep learning models effectively.


```py
import numpy as np

x = np.array(([2, 9], [1, 5], [3, 6]), dtype=float)
print(x)

y = np.array(([92], [86], [89]), dtype=float)
x = x / np.max(x, axis=0)  # Normalize input data
y = y / 100  # Normalize target data (optional)
print(x)
print(y)


def sigmoid(x):
    return (1 / (1 + np.exp(-x)))

def derivatives_sigmoid(x):
    return x * (1 - x)


epoch = 1000  # Number of training iterations
lr = 0.01  # Learning rate
input_layer_neurons = 2  # Number of input neurons (matches the size of x)
hidden_layer_neurons = 2  # Number of neurons in the hidden layer
output_neurons = 1  # Number of output neurons (matches the size of y)

wh = np.random.uniform(size=(input_layer_neurons, hidden_layer_neurons))
bh = np.random.uniform(size=(1, hidden_layer_neurons))
wout = np.random.uniform(size=(hidden_layer_neurons, output_neurons))
bout = np.random.uniform(size=(1, output_neurons))


for i in range(epoch):
    # Forward Propagation
    hinp1 = np.dot(x, wh)
    hinp = hinp1 + bh
    hlayer_act = sigmoid(hinp)

    outinp1 = np.dot(hlayer_act, wout)
    outinp = outinp1 + bout
    output = sigmoid(outinp)

    EO = (y - output)  # Error (target - predicted)

    # Backward Propagation
    outgrad = derivatives_sigmoid(output)
    d_output = EO * outgrad
    EH = d_output.dot(wout.T)
    hiddengrad = derivatives_sigmoid(hlayer_act)
    d_hiddenlayer=EH*hiddengrad

    # Adjusting weights
    wout+=hlayer_act.T.dot(d_output)*lr
    bout+=np.sum(d_output,axis=0,keepdims=True)*lr
    wh+=x.T.dot(d_hiddenlayer)*lr
    bh+=np.sum(d_hiddenlayer,axis=0,keepdims=True)*lr

print("-----------Epoch-",i+1,"Starts-----------")
print("Input:\n"+str(x))
print("Actual output:\n"+str(y))
#
print("predicted output:\n",output)
print("Error:\n"+str(EO))
print("--------Epoch-",i+1,"Ends------")
#
print("Actual Output"+str(y))
print("Predicted Output"+str(output))
print("Error"+str(EO))

```


# Week 8

Write a program to predict the eligibility of a customer for a loan disbursement.

```py

import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

# Load the datasets
train = pd.read_csv("train.csv")
test = pd.read_csv("test.csv")

# Display the head of the datasets
train.head()
test.head()

# Display the columns of the datasets
print(train.columns)
print(test.columns)

# Display the shapes of the datasets
print(train.shape, test.shape)

# Perform exploratory data analysis
train['Loan_Status'].value_counts().plot.bar()

train['Gender'].value_counts(normalize=True).plot.bar(title='Gender')
train['Married'].value_counts(normalize=True).plot.bar(title='Married')
train['Self_Employed'].value_counts(normalize=True).plot.bar(title='Self_Employed')
train['Credit_History'].value_counts(normalize=True).plot.bar(title='Credit_History')
train['Dependents'].value_counts(normalize=True).plot.bar(title='Dependents')
train['Education'].value_counts(normalize=True).plot.bar(title='Education')
train['Property_Area'].value_counts(normalize=True).plot.bar(title='Property_Area')
train['ApplicantIncome'].value_counts(normalize=True).plot.bar(title='ApplicantIncome')

train['CoapplicantIncome'].plot.box()
train['LoanAmount'].plot.box()

# Plot the correlation 
Gender = pd.crosstab(train['Gender'], train['Loan_Status'])
Gender.div(Gender.sum(1).astype(float), axis=0).plot(kind='bar', stacked=True, figsize=(4, 4))

# Plotting a heatmap
matrix = train.select_dtypes(include=['int', 'float'])
plt.figure(figsize=(12, 8))
sns.heatmap(matrix.corr(), vmax=.8, square=True, cmap="BuPu", annot=True)
plt.show()

# Handle missing values
train.isnull().sum()

# Fill missing values with mode
train['Gender'].fillna(train['Gender'].mode()[0], inplace=True)
print(train['Gender'])

train['Married'].fillna(train['Married'].mode()[0], inplace=True)
print(train['Married'])

train['Self_Employed'].fillna(train['Self_Employed'].mode()[0], inplace=True)
print(train['Self_Employed'])

train['Dependents'].fillna(train['Dependents'].mode()[0], inplace=True)
print(train['Dependents'])

train['Property_Area'].fillna(train['Property_Area'].mode()[0], inplace=True)
print(train['Property_Area'])

train['Education'].fillna(train['Education'].mode()[0], inplace=True)
print(train['Education'])

train['LoanAmount'].fillna(train['LoanAmount'].mode()[0], inplace=True)
print(train['LoanAmount'])
```



# Week 9

Write a program to predict the quality of water

```py

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

data =pd.read_csv('water_dataX.csv',encoding="ISO-8859-1")
data.fillna(0,inplace=True)
data.head()a

data.dtypes

data['Temp']=pd.to_numeric(data['Temp'],errors='coerce')
data['D.O. (mg/l)']=pd.to_numeric(data['D.O. (mg/l)'],errors='coerce')
data['PH']=pd.to_numeric(data['PH'],errors='coerce')
data['B.O.D. (mg/l)']=pd.to_numeric(data['B.O.D. (mg/l)'],errors='coerce')
data['CONDUCTIVITY (µmhos/cm)']=pd.to_numeric(data['CONDUCTIVITY (µmhos/cm)'],errors='coerce')
data['NITRATENAN N+ NITRITENANN (mg/l)']=pd.to_numeric(data['NITRATENAN N+ NITRITENANN (mg/l)'],errors='coerce')
data['TOTAL COLIFORM (MPN/100ml)Mean']=pd.to_numeric(data['TOTAL COLIFORM (MPN/100ml)Mean'],errors='coerce')
data.dtypes

start=2
end=1772
station=data.iloc[start:end ,0]
location=data.iloc[start:end ,1]
state=data.iloc[start:end ,2]
do=data.iloc[start:end ,4].astype(np.float64)
value=0
ph=data.iloc[start:end ,5]
co=data.iloc[start:end ,6].astype(np.float64)

year=data.iloc[start:end ,11]
tc=data.iloc[2:end ,10].astype(np.float64)

bod=data.iloc[start:end ,7].astype(np.float64)
na=data.iloc[start:end ,8].astype(np.float64)
na.dtype

data=pd.concat([station,location,state,do,ph,co,bod,na,tc,year],axis=1)
data.columns=['station','location','state','do','ph','co','bod','na','tc','year']

data['npH']=data.ph.apply(lambda x: (100 if (8.5>=x>=7)
else(80 if (8.6>=x>=8.5) or (6.9>=x>=6.8)
else(60 if (8.8>=x>=8.6) or (6.8>=x>=6.7)
else(40 if (9>=x>=8.8) or (6.7>=x>=6.5)
else 0)))))

data['ndo']=data.do.apply(lambda x: (100 if (x>=6)
else(80 if (6>=x>=5.1)
else(60 if (5>=x>=4.1)
else(40 if (4>=x>=3)
else 0)))))

data['nco']=data.tc.apply(lambda x: (100 if (5>=x>=0)
else(80 if (50>=x>=5)
else(60 if (500>=x>=50)
else(40 if (10000>=x>=500)
else 0)))))

data['nbod']=data.bod.apply(lambda x: (100 if (3>=x>=0)
else(80 if (6>=x>=3)
else(60 if (80>=x>=6)
else(40 if (125>=x>=80)
else 0)))))

data['nec']=data.co.apply(lambda x: (100 if (75>=x>=0)
else(80 if (150>=x>=75)
else(60 if (225>=x>=150)
else(40 if (300>=x>=225)
else 0)))))

data['nna']=data.na.apply(lambda x: (100 if (20>=x>=0)
else(80 if (50>=x>=20)
else(60 if (100>=x>=50)
else(40 if (200>=x>=100)
else 0)))))

data.head()
data.dtypes

data['wph']=data.npH * 0.165
data['wdo']=data.ndo * 0.281
data['wbod']=data.nbod * 0.234
data['wec']=data.nec * 0.009
data['wna']=data.nna * 0.028
data['wco']=data.nco * 0.281
data['wqi']=data.wph+data.wdo+data.wbod+data.wec+data.wna+data.wco
data

ag=data.groupby('year')['wqi'].mean()
ag.head()

data=ag.reset_index(level=0,inplace=False)
data

data=data[np.isfinite(data['wqi'])]
data.head()

cols=['year']
y=data['wqi']
x=data[cols]
plt.scatter(x,y)
plt.show()

data=data.set_index('year')
data.plot(figsize=(15,6))
plt.show()

from sklearn import neighbors,datasets
data=ag.reset_index(level=0,inplace=False)
data

from sklearn import linear_model
from sklearn.model_selection import train_test_split
cols=['year']
y=data['wqi']
x=data[cols]
reg=linear_model.LinearRegression()
x_train,x_test,y_train,y_test=train_test_split(x,y,test_size=0.2,random_state=4)
reg.fit(x_train,y_train)

a=reg.predict(x_test)
a

y_test

from sklearn.metrics import mean_squared_error
print('mse:%.2f'%mean_squared_error(y_test,a))

dt=pd.DataFrame({'Actual':y_test,'Predicted':a})

x=(x-x.mean())/x.std()
x=np.c_[np.ones(x.shape[0]),x]
x

alpha=0.1
iterations=3000
m=y.size
np.random.seed(4)
theta=np.random.rand(2)

def gradient_descent(x,y,theta,iterations,alpha):
    past_costs=[]
    past_thetas=[theta]
    for i in range(iterations):
        prediction=np.dot(x,theta)
        error=prediction-y
        cost=1/(2*m)*np.dot(error.T,error)
        past_costs.append(cost)
        theta=theta-(alpha*(1/m)*np.dot(x.T,error))
        past_thetas.append(theta)
    return past_thetas,past_costs
past_thetas,past_costs=gradient_descent(x,y,theta,iterations,alpha)
theta=past_thetas[-1]

print("Gradient Descent: {:.2f},{:.2f}".format(theta[0],theta[1]))

plt.title('Cost Function J')
plt.xlabel('No of iterations')
plt.ylabel('Cost')
plt.plot(past_costs)
plt.show()

newB=[74.76,2.13]
def rmse(y,y_pred):
  rmse = np.sqrt(sum(y-y_pred))
  return rmse

y_pred=x.dot(newB)
dt=pd.DataFrame({'Actual':y,'predicted':y_pred})
dt=pd.concat([data,dt],axis=1)
dt

from sklearn import metrics
print(np.sqrt(metrics.mean_squared_error(y,y_pred)))

x_axis=dt.year
y_axis=dt.Actual
y1_axis=dt.predicted
plt.scatter(x_axis,y_axis)
plt.plot(x_axis,y1_axis,color='r')
plt.title("linear regression")
plt.show
```


# Week 10

Write a program to predict the winner in IPL matches.

```py
import pandas as pd
import numpy as np
import seaborn as sns
sns.set_style("whitegrid")
import matplotlib.pyplot as plt
import sklearn

data = pd.read_csv("matches.csv")
data.head()

data.describe()

data.isnull().sum()

data = data.iloc[:,:-1]
data.dropna(inplace=True)

data["team1"].unique()

data["team1"] = data["team1"].str.replace('Delhi Daredevils', 'Delhi Capitals')
data["team2"] = data["team2"].str.replace('Delhi Daredevils', 'Delhi Capitals')
data["winner"] = data["winner"].str.replace('Delhi Daredevils', 'Delhi Capitals')
data["team1"] = data["team1"].str.replace('Deccan Chargers', 'Sunrisers Hyderabad')
data["team2"] = data["team2"].str.replace('Deccan Chargers', 'Sunrisers Hyderabad')
data["winner"] = data["winner"].str.replace('Deccan Chargers', 'Sunrisers Hyderabad')

plt.figure(figsize=(10,6))
sns.countplot(y = "winner", data = data, order = data['winner'].value_counts().index, color = "pink")
plt.xlabel('Wins')
plt.ylabel('Team')
plt.title("The number of IPL matches won by each team")

plt.figure(figsize=(10,6))
sns.countplot(y = "venue", data = data, order = data["venue"].value_counts().iloc[:10].index, color = "pink")
plt.xlabel("No of matches", fontsize = 12)
plt.ylabel("Venue", fontsize = 12)
plt.title("Total number of matches played in different stadium")

plt.figure(figsize=(10,6))
sns.countplot(x = "toss_decision", data = data, color = "pink")
plt.xlabel("Toss Decision", fontsize = 12)
plt.ylabel("Count", fontsize = 12)
plt.title("Toss Decision")

x = ["city", "toss_decision", "result", "dl_applied"]
for i in x:
    print("-----------")
    print(data[i].unique())
    print(data[i].value_counts())

data.drop(["id", "season", "city", "date", "player_of_match", "umpire1", "venue", "umpire2"], axis = 1, inplace = True)

x = data.drop(["winner"], axis = 1)
y = data["winner"]

X = pd.get_dummies(x, ["team1", "team2", "toss_winner", "toss_decision", "result"], drop_first=True)

from sklearn.preprocessing import LabelEncoder
le = LabelEncoder()
y = le.fit_transform(y)

from sklearn.model_selection import train_test_split
x_train, x_test, y_train, y_test = train_test_split(X, y, test_size=0.8)

from sklearn.ensemble import RandomForestClassifier
model = RandomForestClassifier()

model.fit(x_train, y_train)

y_pred = model.predict(x_test)

from sklearn.metrics import accuracy_score
ac = accuracy_score(y_pred, y_test)
ac
```
