
# [Design a machine learning operations solution](https://learn.microsoft.com/en-us/training/modules/design-machine-learning-operations-solution/)

# Introduction

**Machine Learning operations** or **MLOps** help you to scale your model from a proof of concept or pilot project to production

A model in production is ready for large-scale deployment and is retrained and redeployed when necessary.

mlops makes your machine learning workloads robust and reproducible.


# Explore an MLOps architecture

after training the model you want to get the model ready for entreprise-scale (prepare the model and operationalize it)->

* Convert the model training to a **robust** and **reproducible** pipeline.
* Test the code and the model in a **development** environment.
* Deploy the model in a **production** environment.
* **Automate** the end-to-end process.


## Set up environments for development and production

an **environment** refers to a collection of resources used to deploy a model

the number of environments depends on your organisation but at least there is the dev and production(prod) environments ,other environments are used like (staging or *pre-production*)

A typical approach is to:

* Experiment with model training in the *development* environment.
* Move the best model to the *staging* or *pre-prod* environment to deploy and test the model.
* Finally release the model to the *production* environment to deploy the model so that end-users can consume it.

### Organize Azure Machine Learning environments

When you implement MLOps, and work with machine learning models at a large scale, it's a best practice to work with separate environments for different stages.

Having separate environments makes it easier to control access to resources (data scientist get acces only to dev environment with non-production data, machine learning engineers works on deploying models in pre-prod and prod and get acces to production data ). Each environment can then be associated with a separate Azure Machine Learning workspace.

role-based access control (RBAC) is what gives you in Azure the ability to give acces to colleagues to subset of resources they need


## Design an MLOps architecture

Bringing a model to production means you need to scale your solution and work together with other teams. Together with other data scientists, data engineers and an infrastructure team, you may decide on using the following approach:

* Store all data in an Azure Blob storage, managed by the data engineer.
* The infrastructure team creates all necessary Azure resources, like the Azure Machine Learning workspace.
* Data scientists focus on what they do best: developing and training the model (inner loop).
* Machine learning engineers deploy the trained models (outer loop).

When you're working with larger teams, you're not expected to be responsible of all parts of the MLOps architecture as a data scientist. To prepare your model for MLOps however, you should think about how to design for monitoring and retraining.


# Design for monitoring

**Monitoring** is beneficial in any MLOps environment. You'll want to monitor the  *model* , the  *data* , and the *infrastructure* to collect metrics that help you decide on any necessary next steps.

## Monitor the model

* During development: you use MLflow to train and track your machine learning models, and there are diffenrent metrics u can use based on the model u are using to evaluate whether the model is performing as expected.
* In production : you can use the trained model to generate predictions on a small subset of new incoming data

Before you can monitor a model, it's important to decide which performance metrics you want to monitor and what the benchmark for each metric should be. When should you be alerted that the model isn't accurate anymore?

## Monitor the data

You typically train a machine learning model using a historical dataset that is representative of the new data that your model receives when deployed. However, over time there may be trends that change the profile of the data, making your model less accurate.(data drift)

## Monitor the infrastructure

you should monitor the infrastructure to minimize cost and optimize performance.(compute may be one of your biggest expenses)

# Design for retraining

Generally, there are two approaches to when you want to retrain a model:

* Based on a  **schedule** : when you know you always need the latest version of the model, you can decide to retrain your model every week, or every month, based on a schedule.
* Based on  **metrics** : if you only want to retrain your model when necessary, you can monitor the model's performance and data drift to decide when you need to retrain the model.

In either case, you need to design for retraining. To easily retrain your model, you should prepare your code for automation.

## Prepare your code

* Ideally, you should train models with **scripts** instead of notebooks
* host the code in a central repository(git to achieve  **source control**)

## Automate your code

When you want to automatically execute your code, you can configure Azure Machine Learning jobs to run scripts. In Azure Machine Learning, you can create and schedule pipelines to run scripts too.

If you want scripts to run based on a trigger or event happening outside of Azure Machine Learning, you may want to trigger the Azure Machine Learning job from another tool.

Two tools that are commonly used in MLOps projects are Azure DevOps and GitHub (Actions). Both tools allow you to create automation pipelines and can trigger Azure Machine Learning pipelines.

when working with tools like Azure DevOps and GitHub, you may prefer to configure the necessary resources and jobs with the Azure Machine Learning CLI extension instead. The Azure CLI is designed for automating tasks and may be easier to use with Azure DevOps and GitHub.(instead of Azure Machine Learning Python SDK)
