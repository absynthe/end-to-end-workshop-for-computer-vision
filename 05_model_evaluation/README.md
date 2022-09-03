# Model Evlaution using SageMaker Processing

Amazon SageMaker Processing is a managed solution for various machine learning(ML) processes. These include feature engineering, data validation, model evaluation, model explainability, and many other essential steps performed by engineers and data scientists during their ML workflow.

Your custom processing scripts will be containerized running in infrastructure that is created on demand and terminated automatically. You can choose to use a SageMaker optimized containers for popular data processing or model evaluation frameworks like Scikit learn, PySpark etc. or Bring Your Own Containers (BYOC).

![Process Data](https://docs.aws.amazon.com/sagemaker/latest/dg/images/Processing-1.png)

---

# Introduction

Postprocess and model evaluation are important steps before deployment the model to production. In this module you will use ScriptProcessor from SageMaker Processing to evaluate the model performance after the training.

To setup your ScriptProcessor, we will build a custom container for a model evaluation script which will Load the tensorflow model, load the test dataset and annotation (either from previous module or run the :code[optional-prepare-data-and-model.ipynb] notebook), and then run predicition and generate the confusion matrix.

---
# Prerequisites

Download the notebook into your environment, and you can run it by simply execute each cell in order. To understand what's happening, you'll need:

- Access to the SageMaker default S3 bucket.
- Familiarity with Python and numpy
- Basic familiarity with AWS S3.
- Basic understanding of AWS Sagemaker.
- Basic familiarity with AWS Command Line Interface (CLI) -- ideally, you should have it set up with credentials to access the AWS account you're running this notebook from.
- SageMaker Studio is preferred for the full UI integration

---

### Dataset & Inputs

The dataset we are using is from [Caltech Birds (CUB 200 2011)](http://www.vision.caltech.edu/visipedia/CUB-200-2011.html). If you kept your artifacts from previous labs, then simply update the s3 location below for you Test images and Test data annotation file.  If you do not have them, just run the `optional-prepare-data-and-model.ipynb` notebook to generate the files, and then update the path below.

- S3 path for test image data
- S3 path for test data annotation file
- S3 path for the bird classification model

---
# Review Outputs

At the end of the lab, you will generate a json file containing the performance metrics (accuracy, precision, recall, f1, and confusion matrix) on your test dataset.