# Python DataFrame 이진형 컬럼과 범주형 컬럼 분리

**데이터프레임 안에서 이진 열과 범주형 열을 분류함으로써 이후에 모델 학습에 적합한 훈련 데이터를 제공할 수 있습니다.**


각 열의 고유한 값을 이진형과 범주형으로 분류하고 각 특성 값에 대한 범위를 출력하는 코드입니다.
```python
binary_features = []
categorical_features = []

for col in df.columns:
    #'Id' 와'Age' 열은 pass
    if col not in ['Id', 'Age']:
        unique_values_count = df[col].nunique(dropna=False)
        if unique_values_count == 2:
            binary_features.append(col)
        elif unique_values_count > 2:
            categorical_features.append(col)

        unique_values = df[col].unique()
        print(f"{col} : {unique_values}")

print("Binary Columns:", binary_features)
print()
print("Categorical Columns:", categorical_features)
```

**Result**
```
Gender : ['Female' 'Male']
Hormonal Changes : ['Normal' 'Postmenopausal']
Family History : ['Yes' 'No']
Race/Ethnicity : ['Asian' 'Caucasian' 'African American']
Body Weight : ['Underweight' 'Normal']
Calcium Intake : ['Low' 'Adequate']
Vitamin D Intake : ['Sufficient' 'Insufficient']
Physical Activity : ['Sedentary' 'Active']
Smoking : ['Yes' 'No']
Alcohol Consumption : ['Moderate' nan]
Medical Conditions : ['Rheumatoid Arthritis' nan 'Hyperthyroidism']
Medications : ['Corticosteroids' nan]
Prior Fractures : ['Yes' 'No']
Osteoporosis : [1 0]

Binary Columns: ['Gender', 'Hormonal Changes', 'Family History', 'Body Weight', 'Calcium Intake', 'Vitamin D Intake', 'Physical Activity', 'Smoking', 'Alcohol Consumption', 'Medications', 'Prior Fractures', 'Osteoporosis']

Categorical Columns: ['Race/Ethnicity', 'Medical Conditions']
```

pandas DataFrame df의 각 열을 순회하면서, 
각 열의 고유한 값의 개수를 확인합니다. 

그리고 이 개수에 따라 해당 열을 이진(binary) 특성 또는 범주형(categorical) 특성으로 분류합니다.

 'Id’와 ‘Age’ 열은 이진 또는 범주형 데이터를 나타내지 않기 때문에 분류에서 제외됩니다. 

`binary_columns`
-  고유한 값이 2개인 열들의 리스트입니다. 이러한 열은 보통 이진 데이터를 나타냅니다 
- 예: True/False, Yes/No 등

`categorical_columns`
-  고유한 값이 2개 초과인 열들의 리스트입니다. 이러한 열은 보통 범주형 데이터를 나타냅니다 
- 예: 색상, 도시 이름 등


