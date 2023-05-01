# Thyroid Disease Detection

Thyroid disease is a very common problem in India, more than one crore people are suffering with the disease every year. Thyroid disorder can speed up or slow down the metabolism of the body.

The main objective of this project is to predict if a person is having compensated hypothyroid, primary hypothyroid, secondary hypothyroid or negative (no thyroid) with the help of Machine Learning. Classification algorithms such as Random Forest, XGBoost and KNN Model have been trained on the thyroid dataset, UCI Machine Learning repository. After hyperparameter tuning XGBoost model has performed well with better accuracy, precision and recall. Application has deployed on Heroku with the help of flask framework.

# Demo

https://user-images.githubusercontent.com/100748938/235404067-17b499dc-2894-48db-91c8-feca774abef8.mp4




# Technical Aspects

- Python 3.7 and more
- Important Libraries: sklearn, pandas, numpy, matplotlib & seaborn
- Front-end: HTML, CSS 
- Back-end: Flask framework
- IDE: Jupyter Notebook, Pycharm & VSCode
- Database: Cassandra 
- Deployment: Locally

# How to run this app 

Code is written in Python 3.7 and more. If you don't have python installed on your system, click here https://www.python.org/downloads/ to install.

- Create virtual environment - conda create -p venv python==3.7 -y 
- Activate the environment - conda activate venv
- Install the packages - pip install -r requirements.txt
- Run the app - python run app.py

# Workflow

## Data Collection

Thyroid Disease Data Set from UCI Machine Learning Repository.

Link:https://archive.ics.uci.edu/ml/datasets/thyroid+disease

## Data Pre-processing

- Missing values handling by Simple imputation (KNN Imputer)
- Outliers detection and removal by boxplot and percentile methods
- Categorical features handling by ordinal encoding and label encoding
- Feature scaling done by Standard Scalar method
- Imbalanced dataset handled by SMOTE
- Drop unnecessary columns

## Model Creation and Evaluation

- Various classification algorithms like Random Forest, XGBoost, KNN etc tested.
- Random Forest, XGBoost and KNN were all performed well. XGBoost was chosen for the final model training and testing.
- Hyper parameter tuning was performed using RandomizedSearchCV
- Model performance evaluated based on accuracy, confusion matrix, classification report.


## Database Connection
Cassandra database used for this project.

## Model Deployment
The final model is deployed on Heroku using Flask framework.

### Batch File Prediction User Interface
#### User need to upload CSV file and click custome file predict button for prediction to start.
![wireframe_tdd_2](https://user-images.githubusercontent.com/100748938/235405880-bcb1e01b-8b95-466d-9b8d-47f44b9017ac.PNG)

#### User can download their result by clicking download button below.
![wireframe_tdd_3](https://user-images.githubusercontent.com/72372136/134201925-476df9d9-7f2f-4d5b-b927-46897f5c492c.JPG)

#### Downloaded CSV file will contain index numer with type of thyroid disease patient is suffering from.
![wireframe_tdd_4](https://user-images.githubusercontent.com/72372136/134202106-fb8e0274-ac88-4f9b-b77e-4e834d642a24.JPG)

#### User can also download sample csv file for reference.
![wireframe_tdd_5](https://user-images.githubusercontent.com/72372136/134202214-b4d2fa52-fa25-47d9-9a89-034515e94051.JPG)

#### Data in Cassandra Database.
![DataInCassandraDB](https://user-images.githubusercontent.com/72372136/134202316-ef62ddc2-25f9-451e-bd34-be6c3accce4b.JPG)


## Project Documents

- HLD: https://github.com/imkushwaha/Thyroid-Disease-Detection/blob/main/Docs/TDD_HLD_V1.0.pdf

- LLD: https://github.com/imkushwaha/Thyroid-Disease-Detection/blob/main/Docs/TDD_LLD_V1.0.pdf

- Architecture: https://github.com/imkushwaha/Thyroid-Disease-Detection/blob/main/Docs/TDD_Architecture_V1.0.pdf

- Wireframe: https://github.com/imkushwaha/Thyroid-Disease-Detection/blob/main/Docs/TDD_Wireframe_V1.0.pdf

- Detailed Project Report: https://github.com/imkushwaha/Thyroid-Disease-Detection/blob/main/Docs/TDD_DPR.pdf


# Author

Vikram Jha: https://www.linkedin.com/in/vikram-jha-471bb2246/


## Wafer Fault Detection

#### Problem Statement:
    
    Wafer (In electronics), also called a slice or substrate, is a thin slice of semiconductor,
    such as a crystalline silicon (c-Si), used for fabricationof integrated circuits and in photovoltaics,
    to manufacture solar cells.
    
    The inputs of various sensors for different wafers have been provided.
    The goal is to build a machine learning model which predicts whether a wafer needs to be replaced or not
    (i.e whether it is working or not) nased on the inputs from various sensors.
    There are two classes: +1 and -1.
    +1: Means that the wafer is in a working condition and it doesn't need to be replaced.
    -1: Means that the wafer is faulty and it needa to be replaced.
    
#### Data Description
    
    The client will send data in multiple sets of files in batches at a given location.
    Data will contain Wafer names and 590 columns of different sensor values for each wafer.
    The last column will have the "Good/Bad" value for each wafer.
    
    Apart from training files, we laso require a "schema" file from the client, which contain all the
    relevant information about the training files such as:
    
    Name of the files, Length of Date value in FileName, Length of Time value in FileName, NUmber of Columnns, 
    Name of Columns, and their dataype.
    
#### Data Validation
    
    In This step, we perform different sets of validation on the given set of training files.
    
    Name Validation: We validate the name of the files based on the given name in the schema file. We have 
    created a regex patterg as per the name given in the schema fileto use for validation. After validating 
    the pattern in the name, we check for the length of the date in the file name as well as the length of time 
    in the file name. If all the values are as per requirements, we move such files to "Good_Data_Folder" else
    we move such files to "Bad_Data_Folder."
    
    Number of Columns: We validate the number of columns present in the files, and if it doesn't match with the
    value given in the schema file, then the file id moves to "Bad_Data_Folder."
    
    Name of Columns: The name of the columns is validated and should be the same as given in the schema file. 
    If not, then the file is moved to "Bad_Data_Folder".
    
    The datatype of columns: The datatype of columns is given in the schema file. This is validated when we insert
    the files into Database. If the datatype is wrong, then the file is moved to "Bad_Data_Folder."
    
    Null values in columns: If any of the columns in a file have all the values as NULL or missing, we discard such
    a file and move it to "Bad_Data_Folder".
    
#### Data Insertion in Database
     
     Database Creation and Connection: Create a database with the given name passed. If the database is already created,
     open the connection to the database.
     
     Table creation in the database: Table with name - "Good_Data", is created in the database for inserting the files 
     in the "Good_Data_Folder" based on given column names and datatype in the schema file. If the table is already
     present, then the new table is not created and new files are inserted in the already present table as we want 
     training to be done on new as well as old training files.
     
     Insertion of file in the table: All the files in the "Good_Data_Folder" are inserted in the above-created table. If
     any file has invalid data type in any of the columns, the file is not loaded in the table and is moved to 
     "Bad_Data_Folder".
     
#### Model Training
    
     Data Export from Db: The data in a stored database is exported as a CSV file to be used for model training.
     
     Data Preprocessing: 
        Check for null values in the columns. If present, impute the null values using the KNN imputer.
        
        Check if any column has zero standard deviation, remove such columns as they don't give any information during 
        model training.
        
     Clustering: KMeans algorithm is used to create clusters in the preprocessed data. The optimum number of clusters 
     is selected


## Create a file "Dockerfile" with below content

```
FROM python:3.7
COPY . /app
WORKDIR /app
RUN pip install -r requirements.txt
ENTRYPOINT [ "python" ]
CMD [ "main.py" ]
```

## Create a "Procfile" with following content
```
web: gunicorn main:app
```

## create a file ".circleci\config.yml" with following content
```
version: 2.1
orbs:
  heroku: circleci/heroku@1.0.1
jobs:
  build-and-test:
    executor: heroku/default
    docker:
      - image: circleci/python:3.6.2-stretch-browsers
        auth:
          username: mydockerhub-user
          password: $DOCKERHUB_PASSWORD  # context / project UI env-var reference
    steps:
      - checkout
      - restore_cache:
          key: deps1-{{ .Branch }}-{{ checksum "requirements.txt" }}
      - run:
          name: Install Python deps in a venv
          command: |
            echo 'export TAG=0.1.${CIRCLE_BUILD_NUM}' >> $BASH_ENV
            echo 'export IMAGE_NAME=python-circleci-docker' >> $BASH_ENV
            python3 -m venv venv
            . venv/bin/activate
            pip install --upgrade pip
            pip install -r requirements.txt
      - save_cache:
          key: deps1-{{ .Branch }}-{{ checksum "requirements.txt" }}
          paths:
            - "venv"
      - run:
          command: |
            . venv/bin/activate
            python -m pytest -v tests/test_script.py
      - store_artifacts:
          path: test-reports/
          destination: tr1
      - store_test_results:
          path: test-reports/
      - setup_remote_docker:
          version: 19.03.13
      - run:
          name: Build and push Docker image
          command: |
            docker build -t $DOCKERHUB_USER/$IMAGE_NAME:$TAG .
            docker login -u $DOCKERHUB_USER -p $DOCKER_HUB_PASSWORD_USER docker.io
            docker push $DOCKERHUB_USER/$IMAGE_NAME:$TAG
  deploy:
    executor: heroku/default
    steps:
      - checkout
      - run:
          name: Storing previous commit
          command: |
            git rev-parse HEAD > ./commit.txt
      - heroku/install
      - setup_remote_docker:
          version: 18.06.0-ce
      - run:
          name: Pushing to heroku registry
          command: |
            heroku container:login
            #heroku ps:scale web=1 -a $HEROKU_APP_NAME
            heroku container:push web -a $HEROKU_APP_NAME
            heroku container:release web -a $HEROKU_APP_NAME

workflows:
  build-test-deploy:
    jobs:
      - build-and-test
      - deploy:
          requires:
            - build-and-test
          filters:
            branches:
              only:
                - main
```
## to create requirements.txt

```buildoutcfg
pip freeze>requirements.txt
```

## initialize git repo

```
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin <github_url>
git push -u origin main
```

## create a account at circle ci

<a href="https://circleci.com/login/">Circle CI</a>

## setup your project 

<a href="https://app.circleci.com/projects/github/Avnish327030/setup/"> Setup project </a>

## Select project setting in CircleCI and below environment variable

```
DOCKERHUB_USER
DOCKER_HUB_PASSWORD_USER
HEROKU_API_KEY
HEROKU_APP_NAME
HEROKU_EMAIL_ADDRESS
DOCKER_IMAGE_NAME=wafercircle3270303
```


## to update the modification

```
git add .
git commit -m "proper message"
git push 
```


## #docker login -u $DOCKERHUB_USER -p $DOCKER_HUB_PASSWORD_USER docker.io

    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
     
    
     
    
