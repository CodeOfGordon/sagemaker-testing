# Sagemaker

The below demonstrates my quick dive into the sagemaker using the titanic dataset as my example https://www.kaggle.com/competitions/titanic/data.

## Step 1: Permissions
Firstly, I set up sagemaker, and gave it full permission access. This is typically bad practice, as normally I would just give it full read/write access to a specific app (in this case it'd be S3), however I'm just doing a quick dive; hence why I do this.

![1_sagemaker_iam](https://github.com/user-attachments/assets/0c2d88ca-966d-485b-8443-0c88d719f5c7)

## Step 2: S3 Storage
Now, I simply upload the csv files from the titanic dataset, in order for sagemaker to access them.

![2_sagemaker_s3](https://github.com/user-attachments/assets/5095ea35-7240-4b4c-bbb7-3035eaff32de)

## Step 3: Connecting the dots
With the necessary permissions set up and the data readily available, I can now import the dataset I want (in this case, `train.csv`)

![3_sagemaker_datawrangling_import](https://github.com/user-attachments/assets/e3f21738-3b1a-47c1-a78d-e3f75540749f)

Here is an overview of the pipeline.

![3_sagemaker_datawrangling_import_overview](https://github.com/user-attachments/assets/7f8b9fee-a108-4bee-9eef-166f695e0f49)

## Step 4: Connecting to Canvas: The Low-Code Analyzer

We now want to export it to Canvas where it cleans, transforms, and analyze for us.
So we click the + button to add Canvas as an export destination

![4_sagemaker_export_canvas](https://github.com/user-attachments/assets/9a3f1d2f-6e98-46ca-85c1-041ac507866e)

## Step 5: Utilizing Canvas' Predictions

Once this is done, we can go into the "My Models" sidebar and access it, and select which column we want to predict for.
It doesn't show it in the screenshot, but I selected `Survived` as that's the main goal of the classic titanic dataset.

![5_sagemaker_canvas_build_model](https://github.com/user-attachments/assets/c1f61a79-65d3-4c90-891b-04c5755e1dcd)

## Step 6: Results

After some time, Canvas will have created a full report of what columns (features / predictor variables) have how much of an impact in predicting for the column of our choosing (response variable).
Behind the scenes, Sagemaker Canvas is cleaning and transforming the data, before applying multiple different models to see which is best for this use case by applying various (think comparison metrics like AIC or Adjusted $R^2$).
Afterwards, it takes this best model and examines which features impacted the prediction model the most (think model explainability methods like SHAP)

![6_sagemaker_prediction](https://github.com/user-attachments/assets/604c8ec4-cd68-4f10-b7a4-d6b111bc463f)


