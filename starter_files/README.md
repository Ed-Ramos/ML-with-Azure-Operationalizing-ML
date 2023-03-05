
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

![Project Architecture.png](..%2Fproject2screenshots%2FProject%20Architecture.png)

NOTE: This project was not too concerned with the accuracy of the model produced by the AutoML run. That was not the
focus of the project.  One way to improve the project would be to try and improve the model accuracy. This can be
done by submitting model using the python SDK. This will allow us to better fine tune some parameters like the 
experiment time out and iteration time out parameters. We could also exclude some models from the run and thus
have AutoML spend more time finding and tuning better models.

## Key Steps
*Below are detailed key steps needed to complete this project along with applicable screenshots*

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

*Consume Endpoint*
- In Azure ML, go to "endpoints" section find previously deployed model
- In "details" tab, find the swagger URI.  Download the swagger.json file and place in same directory as the swagger.sh
and serve.py files. This file has information that the swagger service will transform into a website
- Run the swagger.sh script file.  This will run the swagger service in a docker container
- Run the serve.py script which will serve the contents of the current directory
- Confirm swagger runs on localhost showing the HTTP API methods and responses for the model
![swagger running screenshot.png](..%2Fproject2screenshots%2FDeploy%20Model%2Fswagger%20running%20screenshot.png)
- Go to "Consume" tab, obtain endpoint URL and primary key
- Amend endpoints.py script with above info
- Run endpoints.py file and confirm the script runs against the API and a proper json output from model
![enpoint.py run showing jspn output and model prediction.png](..%2Fproject2screenshots%2FDeploy%20Model%2Fenpoint.py%20run%20showing%20jspn%20output%20and%20model%20prediction.png)

*Pipeline Automation*
- Using the "aml pipeline with automated machine learning step" jupyter notebook, replace the URIs, keys, and experiment
names to my scenario
- Run all the jupyter notebook cells until the "Examine Results" section of notebook. Below is screenshot of notebook
wih stepruns
![jupyter notebook showing StepRun.png](..%2Fproject2screenshots%2FPublish%20an%20ML%20Pipeline%2Fjupyter%20notebook%20showing%20StepRun.png) 
- Confirm pipeline is available in the "pipelines" section of Azure Machine Learning Studio
![pipeline created and completed.png](..%2Fproject2screenshots%2FPublish%20an%20ML%20Pipeline%2Fpipeline%20created%20and%20completed.png)
- Publish the pipeline by using Python SDK via the jupyter notebook code. Alternatively, we can use Azure ML Studio 
by going to the "pipelines" section and clicking th pipeline name. Then Click on the "publish" tab on top part.
- Confirm published pipeline now shows a REST endpoint with status of active
![published pipeline showing rest endpoint as active.png](..%2Fproject2screenshots%2FPublish%20an%20ML%20Pipeline%2Fpublished%20pipeline%20showing%20rest%20endpoint%20as%20active.png)

- Now that we have an active restpoint, we can interact with it.  We can schedule a run for a later time or trigger the
run at this time. Below is the trigger request 
![Pipeline trigger in  jupyter notebook.png](..%2Fproject2screenshots%2FPublish%20an%20ML%20Pipeline%2FPipeline%20trigger%20in%20%20jupyter%20notebook.png)

- Confirm that request was completed in Azure machine Learning Studio
![Pipeline run request completed in Azure ML Studio.png](..%2Fproject2screenshots%2FPublish%20an%20ML%20Pipeline%2FPipeline%20run%20request%20completed%20in%20Azure%20ML%20Studio.png)


## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
