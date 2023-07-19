## Thyroid Disease Detection

#### Problem Statement:
    
   Thyroid disease is a common cause of medical diagnosis and prediction, with an onset
   that is difficult to forecast in medical research. The thyroid gland is one of our body's
   most vital organs. Thyroid hormone releases are responsible for metabolic regulation.
   Hyperthyroidism and hypothyroidism are one of the two common diseases of the thyroid
   that releases thyroid hormones in regulating the rate of body's metabolism.
   The main goal is to predict the estimated risk on a patient's chance of obtaining thyroid
   disease or not.

## Demo

https://user-images.githubusercontent.com/100748938/235404067-17b499dc-2894-48db-91c8-feca774abef8.mp4




## Technical Aspects

- Python 3.7 and more
- Important Libraries: sklearn, pandas, numpy, matplotlib & seaborn
- Front-end: HTML, CSS 
- Back-end: Flask framework
- IDE: Jupyter Notebook, Pycharm & VSCode
- Database: SQLite
- Deployment: Locally

# How to run this app 

Code is written in Python 3.7 and more. If you don't have python installed on your system, click here https://www.python.org/downloads/ to install.

- Create virtual environment  
```conda create -p venv python==3.7 -y ```

- Activate the environment     
```conda activate venv ```

- Install the packages     
```pip install -r requirements.txt ```

- Run the app     
```python main.py ```


# Workflow

## Data Collection

Thyroid Disease Data Set from UCI Machine Learning Repository.

Link:https://archive.ics.uci.edu/ml/datasets/thyroid+disease

## Data Pre-processing

   - Drop columns not useful for training the model. Such columns were selected while doing the EDA.
   - Replace the invalid values with numpy “nan” so we can use imputer on such values.
   - Encode the categorical values
   - Check for null values in the columns. If present, impute the null values using the KNN imputer.
   - After imputing, handle the imbalanced dataset by using RandomOverSampler

## Model Creation and Evaluation

- Various classification algorithms like Random Forest, XGBoost, KNN etc tested.
- Random Forest, XGBoost and KNN were all performed well. XGBoost, Random Forest was chosen for the final model training and testing.
- Hyper parameter tuning was performed using RandomizedSearchCV
- Model performance evaluated based on accuracy, confusion matrix, classification report.


## Database Connection
SQLite database used for this project.

## Model Deployment
The final model is deployed locally.

## Batch File Prediction User Interface
#### User need to upload CSV file and click Custom File Predict button for prediction to start.
![prediction page](https://user-images.githubusercontent.com/100748938/235406552-a003167a-84c8-4e4c-b7fd-35d70f6b2da4.PNG)


![prediction file result](https://user-images.githubusercontent.com/100748938/235406410-c45f36a9-7e85-4356-97d2-888730d6105d.PNG)

#### Prediction CSV file will contain index numer with type of thyroid disease patient is suffering from.
![prediction output file](https://user-images.githubusercontent.com/100748938/235406465-d4d5db8a-7568-43ee-89f1-78fa49cab3c9.PNG)



## Project Documents

- HLD : https://github.com/vikram0888/Thyroid-detection/files/11405412/High.Level.Design.pdf

- LLD : https://github.com/vikram0888/Thyroid-detection/files/11405419/Low.Level.Design.pdf

- Architecture : https://github.com/vikram0888/Thyroid-detection/files/11405422/Architecture.Document.pdf

- Wireframe : https://github.com/vikram0888/Thyroid-detection/files/11405427/Wireframe.document.pdf

- Detailed Project Report : https://github.com/vikram0888/Thyroid-detection/files/11406226/Detailed.Project.Report.pdf

- Experience Letter : https://github.com/vikram0888/Thyroid-detection/files/12091222/Experience_letter_Thyroid.Disease.Detection.pdf

## initialize git repo

```
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin <github_url>
git push -u origin main
```


## to update the modification

```
git add .
git commit -m "proper message"
git push 
```


# Author

Vikram Jha: https://www.linkedin.com/in/vikram-jha-471bb2246/
