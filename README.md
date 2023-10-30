# Email Spam Classifier

This project implements an email spam classifier using machine learning techniques. The classifier is trained on a dataset of emails labeled as spam or ham (non-spam). It uses the Logistic Regression algorithm and the TF-IDF (Term Frequency-Inverse Document Frequency) feature extraction technique to classify incoming emails as spam or ham.

## Dataset

The dataset used for training and testing the spam classifier is stored in a CSV file named `mail_data.csv`. The dataset contains two columns: "Message" and "Category". The "Message" column contains the text content of the emails, and the "Category" column contains the corresponding label indicating whether the email is spam or ham.

## Steps Involved

1. Reading and Preparing the Data

![Screenshot (350)](https://github.com/dineshkumar1495/Spam_email_project/assets/94850695/4680f3bc-7996-43de-8e10-793430a84993)


   - The CSV file `mail_data.csv` is read using the `pandas` library to load the dataset into a DataFrame.
   - Any missing values in the DataFrame are replaced with empty strings using the `where` method.
   - The DataFrame is examined using `head`, `info`, and `shape` to get an overview of the data.

2. Data Preprocessing
![Screenshot (351)](https://github.com/dineshkumar1495/Spam_email_project/assets/94850695/c6d39c85-7ad9-4f1c-89dc-cfe80accf5ee)

   - The "Category" column values are converted to numeric representation. "spam" is mapped to 0, and "ham" is mapped to 1.
   - The feature and target variables, X and Y respectively, are extracted from the DataFrame.

3. Train-Test Split

   - The data is split into training and testing sets using the `train_test_split` function from `sklearn.model_selection`.
   - The `test_size` parameter is set to 0.2, indicating that 20% of the data will be used for testing.
   - The `random_state` parameter is set to 3 to ensure reproducibility of the data split.

4. Feature Extraction

![Screenshot (352)](https://github.com/dineshkumar1495/Spam_email_project/assets/94850695/83e1ec2d-ad98-4e1a-8ed7-1446314aa3a4)

   - The TF-IDF vectorizer from `sklearn.feature_extraction.text` is used to convert the text data into numerical features.
   - The vectorizer is instantiated with the following settings:
     - `min_df=1`: Specifies that a term must appear in at least one document to be considered.
     - `stop_words='english'`: Excludes common English words from the vocabulary.
     - `lowercase=True`: Converts all text to lowercase.
   - The vectorizer is fit on the training data using the `fit_transform` method, and the same vocabulary is applied to transform both the training and testing data.

5. Model Training and Evaluation

![image](https://github.com/dineshkumar1495/Spam_email_project/assets/94850695/575ef548-bc01-46f9-83ac-3f6206cc414c)

   - A Logistic Regression model is created using the `LogisticRegression` class from `sklearn.linear_model`.
   - The model is trained on the training data features (`X_train_features`) and the corresponding labels (`Y_train`) using the `fit` method.
   - The accuracy of the model is evaluated on both the training and testing data using the `accuracy_score` function from `sklearn.metrics`.
   - The accuracy score on the training data is printed.
   - The accuracy score on the testing data is printed.

6. Predicting Email Category

![Screenshot (354)](https://github.com/dineshkumar1495/Spam_email_project/assets/94850695/b7e9e005-5586-4087-b1e3-21827cc27ad0)

   - An example email is provided as input text (`input_your_mail`).
   - The input text is transformed into feature representation using the same TF-IDF vectorizer (`input_data_feature`).
   - The trained model predicts the category of the input email using the `predict` method.
   - The predicted category is printed as either "Ham mail" or "Spam mail".

## Dependencies

The following Python libraries are required to run this project:

- `numpy`
- `pandas`
- `scikit-learn`

Make sure to have these libraries installed before running the code.

## Usage

1. Prepare the Dataset:
   -

 Create a CSV file named `mail_data.csv` with columns "Message" and "Category".
   - Populate the file with email data, where each row contains the email message and its corresponding category (spam or ham).

2. Run the Code:
   - Execute the Python script containing the code in your preferred Python environment.

3. Interpret the Results:
   - The accuracy scores on the training and testing data will be displayed.
   - The predicted category of the example email will be printed as either "Ham mail" or "Spam mail".

