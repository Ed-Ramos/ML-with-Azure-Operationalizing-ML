*NOTE:* This file is a template that you can use to create the README for your project. The *TODO* comments below will highlight the information you should be sure to include.


# Operationalizing Machine Learning

*This project is a natural next step to the first project that was completed for this course.  In that first project, we learned
how to create a machine learning model using Azure Machine Learning Studio and via the Azure Python SDK. 
In this project we explore three main areas:
1) **Deploying a Model**
 - This includes creating cluster configurations and compute targets. Also how to get the model into production
 - Setting proper authentication with automation
 - Turning on Application Insights to obtain meaningful model logs information
2) **Consuming Endpoints**
 - Consume endpoints to interact with a deployed model in Azure ML studio
 - Using Swagger to ease documentation efforts of the HTTP API
 - Initiate an HTTP request to the endpoint and obtain a proper response
3) **Pipeline Automation**
 - How to publish and consume pipelines


## Architectural Diagram
*TODO*: Provide an architectual diagram of the project and give an introduction of each step. An architectural diagram is an image that helps visualize the flow of operations from start to finish. In this case, it has to be related to the completed project, with its various stages that are critical to the overall flow. For example, one stage for managing models could be "using Automated ML to determine the best model". 

![Project Architecture.png](Project%20Architecture.png)

## Key Steps
*TODO*: 
* Write a short discription of the key steps. Remember to include all the screenshots required to demonstrate key steps. 
**Deploy model in Azure ML Studio**

*Configure new AutoML Run*
 - Create new AutoML run
 - Upload Bankmarketing data file to datastore and confirm it shows as available
![bankmarketing dataset.png](..%2Fproject2screenshots%2FDeploy%20Model%2Fbankmarketing%20dataset.png)
 - create and configure new compute cluster
 - Use cluster to run AutoML experiment
 - Confirm Experiment is shown as completed
![new automl run showing complete.png](..%2Fproject2screenshots%2FDeploy%20Model%2Fnew%20automl%20run%20showing%20complete.png)

*Deploy an Azure ML Model*
- Go to AutoML section and find ML experiment with complete status
- Go to model tab and select model
- Click on "Deploy". A) fill out form B) use Azure Container Instance (ACI) C) Enable Authentication
- After successful deployment, verify "deployed status" shows healthy
![deployed model with healthy state.png](..%2Fproject2screenshots%2FDeploy%20Model%2Fdeployed%20model%20with%20healthy%20state.png)
- Download config file and place in current directory
- amend logs.py script and enable logging by running script
![deployment logs after running logs.py script.png](..%2Fproject2screenshots%2FDeploy%20Model%2Fdeployment%20logs%20after%20running%20logs.py%20script.png)
- Confirm endpoints section in Azure ML studio shows that "Application Insights enabled" says True
![deployed model shows Application Insights enabled as True.png](..%2Fproject2screenshots%2FDeploy%20Model%2Fdeployed%20model%20shows%20Application%20Insights%20enabled%20as%20True.png)


## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
