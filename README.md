## EXNO-3-Feature Encoding and Transformation

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
 import pandas as pd
 df=pd.read_csv("Encoding Data.csv")
 df
![Screenshot 2025-04-22 141957](https://github.com/user-attachments/assets/40e3b0e2-43b1-49ac-8999-8369e2645517)

 from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
 pm=['Hot','Warm','Cold']
 e1=OrdinalEncoder(categories=[pm])
 e1.fit_transform(df[["ord_2"]])
 ![Screenshot 2025-04-22 142015](https://github.com/user-attachments/assets/2d3915e5-d6be-416d-9bae-1efc1b7067a4)

 
  df['bo2']=e1.fit_transform(df[["ord_2"]])
  df
 ![Screenshot 2025-04-22 142027](https://github.com/user-attachments/assets/a5d69eae-5ed6-48dd-a04b-9250cb889409)

  le=LabelEncoder()
 dfc=df.copy()
 dfc['ord_2']=le.fit_transform(dfc['ord_2'])
 dfc
![Screenshot 2025-04-22 142036](https://github.com/user-attachments/assets/b38545fa-e209-45ac-b1dc-d5aa9b525870)

 from sklearn.preprocessing import OneHotEncoder
 ohe=OneHotEncoder(sparse=False)
 df2=df.copy()
 enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]))
 df2=pd.concat([df2,enc],axis=1)
 df2
 
![Screenshot 2025-04-22 142046](https://github.com/user-attachments/assets/7fe67eaf-e5bb-443e-b94f-03b68352390c)

 pd.get_dummies(df2,columns=["nom_0"])
![Screenshot 2025-04-22 142057](https://github.com/user-attachments/assets/a86ca928-8d76-4e61-9184-f39e261212f0)

 pip install--upgrade category_encoders
![Screenshot 2025-04-22 142106](https://github.com/user-attachments/assets/14a7b155-454e-4a54-8487-7991a44726d6)

 from category_encoders import BinaryEncoder
 df=pd.read_csv("data.csv")
 df
![Screenshot 2025-04-22 142152](https://github.com/user-attachments/assets/b87445f0-d121-49da-97b1-76c1a03f4b22)

 be=BinaryEncoder()
 nd=be.fit_transform(df['Ord_2'])
 df
![Screenshot 2025-04-22 142159](https://github.com/user-attachments/assets/01263345-6902-4889-889a-57bb55c17ae8)

 dfb=pd.concat([df,nd],axis=1)
 dfb
![Screenshot 2025-04-22 142207](https://github.com/user-attachments/assets/36f54255-315d-489e-bc7d-7d592ea76fa5)

 from category_encoders import TargetEncoder
 te=TargetEncoder()
 CC=df.copy()
 new=te.fit_transform(X=CC["City"],y=CC["Target"])
 CC=pd.concat([CC,new],axis=1)
 CC
![Screenshot 2025-04-22 142214](https://github.com/user-attachments/assets/5d79af1f-dec4-45af-8d92-5cd4e6ecfb48)

 import pandas as pd
 from scipy import stats
 import numpy as np
 df=pd.read_csv("Data_to_Transform.csv")
 df
![Screenshot 2025-04-22 142223](https://github.com/user-attachments/assets/4e3787a7-04c9-4484-a2f5-7672dc5b5471)

 df.skew()
![Screenshot 2025-04-22 142232](https://github.com/user-attachments/assets/ca882fc7-0317-4a79-bf29-742c9b2fe5e2)

np.log(df["Highly Positive Skew"])
![Screenshot 2025-04-22 142239](https://github.com/user-attachments/assets/9c995ab1-1858-4a27-b1f7-015f811c20bc)

 np.reciprocal(df["Moderate Positive Skew"])
![Screenshot 2025-04-22 142256](https://github.com/user-attachments/assets/1a314223-a5f2-43a3-ae58-4ec11d84b271)

 np.sqrt(df["Highly Positive Skew"])
![Screenshot 2025-04-22 142305](https://github.com/user-attachments/assets/0e821529-6f72-4420-b42d-0bf99652bae6)

 np.square(df["Highly Positive Skew"])
![Screenshot 2025-04-22 142319](https://github.com/user-attachments/assets/c22d3fbb-a862-413a-9f13-58b6ee54f94c)

df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
 df
![Screenshot 2025-04-22 142331](https://github.com/user-attachments/assets/d9f62ecd-88b4-4b50-b031-1ff78ce4379f)

 df.skew()
![Screenshot 2025-04-22 142339](https://github.com/user-attachments/assets/97af8841-93e9-476b-8b82-c566c4a31897)

 df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"
 df.skew()

![Screenshot 2025-04-22 142346](https://github.com/user-attachments/assets/32e10a6c-750f-41c1-a69b-e30f7f7f6bd3)

from sklearn.preprocessing import QuantileTransformer
 qt=QuantileTransformer(output_distribution='normal')
 df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]])
 df
![Screenshot 2025-04-22 142421](https://github.com/user-attachments/assets/1c99fa07-e6d6-4982-9c30-eee5aa903027)

 import seaborn as sns
 import statsmodels.api as sm
 import matplotlib.pyplot as plt
 sm.qqplot(df["Moderate Negative Skew"],line='45')
 plt.show()
![Screenshot 2025-04-22 142434](https://github.com/user-attachments/assets/12477759-9746-4ee8-9ec9-ba9562148382)

 sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
 plt.show()
![Screenshot 2025-04-22 142442](https://github.com/user-attachments/assets/bbf8500f-bb5b-4e68-a3d3-0c939cae75cb)

 from sklearn.preprocessing import QuantileTransformer
 qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
 df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
 sm.qqplot(df["Moderate Negative Skew"],line='45')
 plt.show()
![Screenshot 2025-04-22 142514](https://github.com/user-attachments/assets/b6518278-01e9-461f-9bfa-2cfb16ddf8ab)

 df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
 sm.qqplot(df["Highly Negative Skew"],line='45')
 plt.show()
![Screenshot 2025-04-22 142522](https://github.com/user-attachments/assets/0cede0ed-af3c-4124-b493-f6cf0353d083)

 dt=pd.read_csv("titanic_dataset.csv")
 dt
 from sklearn.preprocessing import QuantileTransformer
 qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
 dt["Age_1"]=qt.fit_transform(dt[["Age"]])
 sm.qqplot(dt['Age'],line='45') 
plt.show()
![Screenshot 2025-04-22 142529](https://github.com/user-attachments/assets/079862fa-721b-44df-ab9a-717e4ab24cb6)

 sm.qqplot(df["Highly Negative Skew_1"],line='45')
 plt.show()
![Screenshot 2025-04-22 142536](https://github.com/user-attachments/assets/e68c5738-ed0a-4e3d-a037-2a8d3f0bb74e)



# RESULT:
 Thus the given data, Feature Encoding, Transformation process and save the data to a file
 was performed successfully.

       
