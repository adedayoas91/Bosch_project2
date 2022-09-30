## Bosch_project2 documentation

[![Python application test with GitHub Actions](https://github.com/adedayoas91/Bosch_project2/actions/workflows/pythonapp.yml/badge.svg)](https://github.com/adedayoas91/Bosch_project2/actions/workflows/pythonapp.yml)

Project architecture is detailed as follows
<img width="894" alt="Screenshot 2022-09-10 at 18 28 44" src="https://user-images.githubusercontent.com/47278559/189492758-a77b511c-6ea9-489d-a508-30a38f94c7d9.png">

Project Objectives
    - Use Trello to map out processes
    - Spreadsheets for project planning
    - CI/CD

Steps to achieving task:
- Creating and pairing SSh keys with the Github repo and account
    run <ssh-keygen -t rsa>, copy the path the public key is saved in
        <cat ~/.ssh/id_rsa.pub>
  The generated ssh key should be copied and pasted into the GitHub account via (GitHub > Settings > SSH and GPG keys > New > Paste > Add) 
- Clone the repo with the SSH link 
  run <git clone <SSH-link> >
    Successful cloning should look as shown in the image below
<img width="1440" alt="Screenshot 2022-08-26 at 22 26 46" src="https://user-images.githubusercontent.com/47278559/187019584-aa92552f-0a16-4b5a-b6d6-5fa17804208a.png">

- After successfully cloning the repo, create a new virtual environment
  To create a new virtualenv; run <python3 -m venv ~/.<new name>> > 
                                    <source ~/.<new name>/bin/activate>

- Next, install dependencies by running the Makefile with the command <make all>
<img width="1440" alt="Screenshot 2022-08-27 at 16 22 59" src="https://user-images.githubusercontent.com/47278559/187035437-b533c639-e113-45dc-b6e3-568153dc9c8e.png">

- Create a web app using the command <az web app up --name <webapp-name> --resource-group <resource-group-name> --runtime "PYTHON:<version>">
   In my own case, I have used web app-name == "bright-services"; "this is to be checked."
                               resource-group-name == "Azuredevops";
                               version == 3.9  #i have used a python 3.9 not 3.7
   The result can be seen as shown below
<img width="1440" alt="Screenshot 2022-08-27 at 02 09 00" src="https://user-images.githubusercontent.com/47278559/187021941-1fa901ec-c284-4e7f-ae9e-e59b0358e04d.png">

- A screenshot of the web app deployment as in the Azure portal can be seen in the attached
<img width="1440" alt="Screenshot 2022-09-10 at 17 20 11" src="https://user-images.githubusercontent.com/47278559/190574286-6b0c7775-c57f-4b95-b814-5a5b501526cf.png">

- Configuring the GitHub Actions
  We start by creating a new workflow in the Github repo. This can be done by clicking on the Actions menu and "Set up a workflow yourself."
    It is noteworthy that a starter code has been provided, which includes the script to put in the workflow .yml file and named pythonapp.yml
    After successfully making the file commit the changes and then run the build session, and the following result should be achieved. 
     - Notably, the green tick indicates the integration build successfully, and all codes are running fine. However, a slight change is required in the stater script for the pythonapp.yml to build successfully. This involves upgrading the python version in the script to any other version aside from version == 3.5
<img width="1440" alt="Screenshot 2022-08-26 at 22 48 43" src="https://user-images.githubusercontent.com/47278559/187022274-54fa822c-2040-4698-9709-34d0507fcde1.png">

- After creating the web app.
  > I have created the web app with the above specifications and checked the URL to see if it's running. Below showed the expected result
<img width="1440" alt="Screenshot 2022-08-27 at 16 36 54" src="https://user-images.githubusercontent.com/47278559/187035831-12f312e4-0afa-490a-af2e-0ae30f8b8375.png">

 > Then proceed to predict by running <./make_predict_azure_app.sh>, and the prediction based on the model used can be shown in the following image
<img width="1440" alt="Screenshot 2022-08-27 at 16 40 00" src="https://user-images.githubusercontent.com/47278559/187035959-5bda29b4-dfe3-4cdc-9be8-1eded3543c6c.png"> # this is a change

> Results from the locust test carried out can be seen in the attached screenshot. 
<img width="1440" alt="Screenshot 2022-09-15 at 20 26 51" src="https://user-images.githubusercontent.com/47278559/190486470-5d0b5b3d-e578-46ae-a3e8-bb249c79cb90.png">


```2022-08-27T15:06:42  Welcome; you are now connected to the log-streaming service.

Starting Log Tail -n 10 of existing logs ----

/home/LogFiles/__lastCheckTime.txt  (https://bright-services.scm.azurewebsites.net/api/vfs/LogFiles/__lastCheckTime.txt)
08/27/2022 14:36:18

/home/LogFiles/kudu/trace/769ceae5243b-5c51755b-6f28-4485-98b4-00f71f667703.txt  (https://bright-services.scm.azurewebsites.net/api/vfs/LogFiles/kudu/trace/769ceae5243b-5c51755b-6f28-4485-98b4-00f71f667703.txt)
2022-08-27T14:30:43  Startup Request, url: /api/zipdeploy?isAsync=true, method: POST, type: request, pid: 65,1,5, SCM_DO_BUILD_DURING_DEPLOYMENT: True, ScmType: None

/home/LogFiles/2022_08_27_10-30-0-12_default_docker.log  (https://bright-services.scm.azurewebsites.net/api/vfs/LogFiles/2022_08_27_10-30-0-12_default_docker.log)
2022-08-27T14:36:47.333267422Z 169.254.130.1 - - [27/Aug/2022:14:36:47 +0000] "GET /favicon.ico HTTP/1.1" 404 207 "https://bright-services.azurewebsites.net/" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/104.0.0.0 Safari/537.36"


2022-08-27T14:39:36.442669515Z /tmp/8da8838bd7c5026/antenv/lib/python3.9/site-packages/sklearn/base.py:329: UserWarning: Trying to unpickle estimator LinearRegression from version 0.24.2 when using version 1.1.2. This might lead to breaking code or invalid results. Use at your own risk. For more info, please refer to the following:
2022-08-27T14:39:36.442721216Z https://scikit-learn.org/stable/model_persistence.html#security-maintainability-limitations
2022-08-27T14:39:36.442730716Z   warnings.warn(
2022-08-27T14:39:36.444341838Z [2022-08-27 14:39:36,443] INFO in app: JSON payload: %s json_payload
2022-08-27T14:39:36.462030982Z [2022-08-27 14:39:36,460] INFO in app: inference payload DataFrame: %s inference_payload
2022-08-27T14:39:36.466075238Z [2022-08-27 14:39:36,460] INFO in app: Scaling Payload: %s payload
2022-08-27T14:39:36.502926347Z 169.254.130.1 - - [27/Aug/2022:14:39:36 +0000] "POST /predict HTTP/1.1" 200 36 "-" "curl/7.84.0"

/home/LogFiles/2022_08_27_10-30-0-12_docker.log  (https://bright-services.scm.azurewebsites.net/api/vfs/LogFiles/2022_08_27_10-30-0-12_docker.log)
2022-08-27T14:36:19.980Z INFO  - Starting container for the site
2022-08-27T14:36:19.982Z INFO  - docker run -d --expose=8000 --name bright-services_0_174c9243 -e WEBSITE_SITE_NAME=bright-services -e WEBSITE_AUTH_ENABLED=False -e WEBSITE_ROLE_INSTANCE_ID=0 -e WEBSITE_HOSTNAME=bright-services.azurewebsites.net -e WEBSITE_INSTANCE_ID=d48e7722c44716b2d3b260fd39937cd26b4df2c1aad200418e83e1648d9c8bd5 -e HTTP_LOGGING_ENABLED=1 -e WEBSITE_USE_DIAGNOSTIC_SERVER=False appsvc/python:3.9_20220315.5  

2022-08-27T14:36:22.788Z INFO  - Initiating warmup request to container bright-services_0_174c9243 for site bright-services
2022-08-27T14:36:46.029Z INFO  - Container bright-services_0_174c9243 for site bright-services initialized successfully and is ready to serve requests.


/home/LogFiles/AppServiceAppLogs_Feature_Installer/startup_0.log  (https://bright-services.scm.azurewebsites.net/api/vfs/LogFiles/AppServiceAppLogs_Feature_Installer/startup_0.log)
2022-08-27 14:36:35,355  [MainThread] [DEBUG] : Initializating AppServiceAppLogging 
2022-08-27 14:36:35,356  [Thread-1  ] [DEBUG] : Did not find any previously bound socket
2022-08-27 14:36:35,362  [MainThread] [DEBUG] : Initialized AppServiceAppLogging
2022-08-27 14:36:43,424  [Thread-3  ] [DEBUG] : Waiting for the logs flag to be set


/home/LogFiles/CodeProfiler/d48e77_debug.log  (https://bright-services.scm.azurewebsites.net/api/vfs/LogFiles/CodeProfiler/d48e77_debug.log)
[2022_08_27_14_36_43] [appsvc_profiler.installer] [INFO] Code Profiler Installer is starting up
[2022_08_27_14_36_43] [appsvc_profiler.installer] [INFO] Cleaning up any existing status file which indicated signal handlers initialized status
[2022_08_27_14_36_43] [appsvc_profiler.installer] [DEBUG] APPSETTING_WEBSITE_ENABLE_DEFAULT_CODE_PROFILER : None
[2022_08_27_14_36_43] [appsvc_profiler.installer] [INFO] Attempting to install the default code profiler.
[2022_08_27_14_36_43] [appsvc_profiler.installer] [DEBUG] viztracer would save traces to /tmp/d48e77_profiler_trace.json
[2022_08_27_14_36_43] [appsvc_profiler.installer] [INFO] Successfully installed code profiler.
[2022_08_27_14_36_43] [appsvc_profiler.installer] [INFO] Signal Handlers SIGUSR for needed code-profiler have been initialized for gunicorn process on instance d48e7722c44716b2d3b260fd39937cd26b4df2c1aad200418e83e1648d9c8bd5
[2022_08_27_14_36_43] [appsvc_profiler.installer] [DEBUG] Code Profiler Installer is exiting as installation is completed


Ending Log Tail of existing logs ---

Starting Live Log Stream ---
2022-08-27T14:36:19.980Z INFO  - Starting container for site

2022-08-27T14:36:19.982Z INFO  - docker run -d --expose=8000 --name bright-services_0_174c9243 -e WEBSITE_SITE_NAME=bright-services -e WEBSITE_AUTH_ENABLED=False -e WEBSITE_ROLE_INSTANCE_ID=0 -e WEBSITE_HOSTNAME=bright-services.azurewebsites.net -e WEBSITE_INSTANCE_ID=d48e7722c44716b2d3b260fd39937cd26b4df2c1aad200418e83e1648d9c8bd5 -e HTTP_LOGGING_ENABLED=1 -e WEBSITE_USE_DIAGNOSTIC_SERVER=False appsvc/python:3.9_20220315.5  



2022-08-27T14:36:22.788Z INFO  - Initiating warmup request to container bright-services_0_174c9243 for site bright-services

2022-08-27T14:36:46.029Z INFO  - Container bright-services_0_174c9243 for site bright-services initialized successfully and is ready to serve requests.
````

-  A snapshot of the log footage as shown in the CLI is shown below
<img width="1440" alt="Screenshot 2022-08-27 at 17 07 32" src="https://user-images.githubusercontent.com/47278559/187036066-acd5f892-f08a-4af1-bccb-b0230cf62dc7.png">


- After committing all changes to Github, I ran the Github actions build, and all build was successful
<img width="1440" alt="Screenshot 2022-08-28 at 15 50 15" src="https://user-images.githubusercontent.com/47278559/187078650-f0fc2a0c-a8bf-4911-8879-d7f10df050f9.png">

- Performance validation of the web app can be performed via a load test using [locust](https://locust.io/). 
To run the locustfile.py, please edit the Host URL to include the web app that has been tested.
A screenshot of the results of the testing is attached below
<img width="1440" alt="Screenshot 2022-09-03 at 19 23 27" src="https://user-images.githubusercontent.com/47278559/188506380-d5272805-fe6b-4e21-9214-15e82ed61a73.png">


- Proceed to Configure the azure pipelines as described in the [documentation](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops)
<img width="1440" alt="Screenshot 2022-09-10 at 17 17 50" src="https://user-images.githubusercontent.com/47278559/190573878-23004a89-0333-46f1-b9e9-a753e542483e.png">


- Also, the GitHub repo passed the build as well as shown in the image below and can be verified via this [link](https://github.com/adedayoas91/Bosch_project2)
![Screenshot (203)](https://user-images.githubusercontent.com/47278559/187691020-1b1324d3-1ecb-4ba3-b780-2a068f58310c.png)

- That ended the task and documentation process, including the Trello board and spreadsheet, and the README was updated.
   - Click [here](https://trello.com/b/VNWPOlIf/boschproject2) to view the workflow Trello
   - Click [here](https://docs.google.com/spreadsheets/d/1FjNlNgm0SfMknYug1v7eJzQ2GBJOGoPPpXxUvH1ZeoQ/edit?usp=sharing) to see the workflow spreadsheet. Likewise, a copy of the spreadsheet can be found in the root folder of the repo.
   - Click [here](https://youtu.be/xvctqRk8luo) to access the video demo required.


# Recommendations for improving the project

- The project is a very well-designed task to understand the CI/CD pipeline workflow with Azure. However, I would like to make a slight suggestion by clarifying the locust file testing and procedures better. It appears to be one very critical aspect of the project. So more emphasis should be made on its use in class and the project descriptions. 
