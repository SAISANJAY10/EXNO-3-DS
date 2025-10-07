## EXNO-3-DS
## NAME: Sai Sanjay R
## REG.NO:212223040178
# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
```
import pandas as pd
df=pd.read_csv("Encoding Data.csv")
df
```
<img width="358" height="456" alt="image" src="https://github.com/user-attachments/assets/b7fea0bc-4cbe-4c27-9d33-93a7b186c936" />

```
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["ord_2"]])
```
<img width="382" height="231" alt="image" src="https://github.com/user-attachments/assets/a50fe7a5-dfe2-401b-88b0-fbb90f4daed9" />

```
df['bo2']=e1.fit_transform(df[["ord_2"]])
df
```
<img width="400" height="438" alt="image" src="https://github.com/user-attachments/assets/54bfdfe6-4205-4f04-b2d9-dd9e327be68c" />

```
le=LabelEncoder()
dfc=df.copy()
dfc['ord_2']=le.fit_transform(dfc['ord_2'])
dfc
```
<img width="405" height="448" alt="image" src="https://github.com/user-attachments/assets/d2c5008e-ff41-441b-b866-ba42e4eac3c6" />

```
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder()
df2=data.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]].values).toarray())
df2=pd.concat([df2,enc],axis=1)
df2
```
<img width="533" height="443" alt="image" src="https://github.com/user-attachments/assets/d257fc43-3b32-4479-9f25-bc56a321d859" />

```
pd.get_dummies(df2,columns=["nom_0"])
```
<img width="797" height="440" alt="image" src="https://github.com/user-attachments/assets/5ec4e611-8bf0-46f2-b4f1-2f6a9f0a5014" />

```
pip install --upgrade category_encoders
```
<img width="531" height="53" alt="image" src="https://github.com/user-attachments/assets/87742034-004e-4229-b4ab-8f7136264706" />

```
from category_encoders import BinaryEncoder
df=pd.read_csv("data.csv")
df
```
<img width="652" height="448" alt="image" src="https://github.com/user-attachments/assets/fdf6499c-6dd0-4bcf-b923-98e979b9961b" />

```
be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])
df
```
<img width="637" height="453" alt="image" src="https://github.com/user-attachments/assets/859365fa-819d-4d31-9a43-4e3435962ce1" />

```
dfb=pd.concat([df,nd],axis=1)
dfb
```
<img width="835" height="457" alt="image" src="https://github.com/user-attachments/assets/3383aef2-3677-482b-baa5-87bc596a6711" />

```
from category_encoders import TargetEncoder
te=TargetEncoder()
CC=df.copy()
new=te.fit_transform(X=CC["City"],y=CC["Target"])
CC=pd.concat([CC,new],axis=1)
CC
```
<img width="675" height="432" alt="image" src="https://github.com/user-attachments/assets/c44f7b78-4086-4f0c-9182-b54fd97ec84d" />

```
import pandas as pd
from scipy import stats
import numpy as np
df=pd.read_csv("Data_to_Transform.csv")
df
```
<img width="1002" height="502" alt="image" src="https://github.com/user-attachments/assets/5f047869-b428-4df8-b492-48a3e5afc6a2" />

```
df.skew()
```
<img width="455" height="258" alt="image" src="https://github.com/user-attachments/assets/f29dfc55-dee1-4302-8b37-6b0d0ee4bbab" />

```
np.log(df["Highly Positive Skew"])
```
<img width="493" height="567" alt="image" src="https://github.com/user-attachments/assets/f54ae917-2a68-42cc-94ac-7a2d853bbbcb" />

```
np.reciprocal(df["Moderate Positive Skew"])
```
<img width="503" height="563" alt="image" src="https://github.com/user-attachments/assets/64d6ab56-ed2b-4dc2-9597-707bcc21c7f4" />

```
np.sqrt(df["Highly Positive Skew"])
```
<img width="687" height="562" alt="image" src="https://github.com/user-attachments/assets/73cf4237-89cf-4112-87bc-94ee12e31bb6" />

```
np.square(df["Highly Positive Skew"])
```
<img width="386" height="565" alt="image" src="https://github.com/user-attachments/assets/2307250d-8f07-4e9a-9797-cede555d5061" />

```
df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
df
```
<img width="1347" height="521" alt="image" src="https://github.com/user-attachments/assets/4c9fac91-29a4-4cc1-b128-6830e18b35f1" />

```
df.skew()
```
<img width="412" height="287" alt="image" src="https://github.com/user-attachments/assets/454647f1-4285-4dde-a87e-0962e0b9dc34" />

```
df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
df.skew()
```
<img width="425" height="328" alt="image" src="https://github.com/user-attachments/assets/01c023ff-29c0-44bb-8647-87d8f60171e0" />

```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal')
df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]])
df
```
<img width="1412" height="558" alt="image" src="https://github.com/user-attachments/assets/7ec8d225-8bcb-49dd-b67f-819103c8e4fd" />

```
import seaborn as sns
import statsmodels.api as sm
import matplotlib.pyplot as plt
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```
<img width="836" height="550" alt="image" src="https://github.com/user-attachments/assets/554ba968-e687-449d-b9f8-b8933884a4df" />

```
sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
plt.show()
```
<img width="846" height="548" alt="image" src="https://github.com/user-attachments/assets/c663fa18-0413-4228-a29d-0665912c2451" />

```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```
<img width="826" height="570" alt="image" src="https://github.com/user-attachments/assets/5439b544-6f04-494d-b6b5-5e6b1a7d37e4" />

```
df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
sm.qqplot(df["Highly Negative Skew"],line='45')
plt.show()
```
<img width="776" height="542" alt="image" src="https://github.com/user-attachments/assets/8b34b964-09fd-44fb-8f87-db9aaeb995c4" />

```
dt=pd.read_csv("titanic_dataset.csv")
dt
```
<img width="1418" height="557" alt="image" src="https://github.com/user-attachments/assets/737e8672-27ca-4609-955e-8e62545bf913" />

```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
dt["Age_1"]=qt.fit_transform(dt[["Age"]])
sm.qqplot(dt['Age'],line='45')
plt.show()
```
<img width="802" height="552" alt="image" src="https://github.com/user-attachments/assets/2213b6a2-b352-434b-b198-20681c5493a8" />

```
sm.qqplot(df["Highly Negative Skew_1"],line='45')
plt.show()
```
<img width="922" height="540" alt="image" src="https://github.com/user-attachments/assets/9c0d376f-c318-45f8-9fc9-ad693f5d6a9b" />



# RESULT:
 Thus the given data, Feature Encoding, Transformation process and save the data to a file
 was performed successfully.

       
