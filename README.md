Project Objectives
    - Use Trello to map out processes
    - Spreadsheets for project planning
    - CI/CD

Steps to achieving task:
- Creating and pairing SSh keys with the Github repo and account
    run <ssh-keygen -t rsa>, copy the path the public key is saved in
        <cat ~/.ssh/id_rsa.pub>
  The generated ssh key should be copied and pasted into the Github account via (GitHub > Settings > SSH and GPG keys > New > Paste > Add) 
- Clone the repo with the SSH link 
  run <git clone <SSH-link> >
    Successful cloning should look as shown in the image below
<img width="1440" alt="Screenshot 2022-08-26 at 22 26 46" src="https://user-images.githubusercontent.com/47278559/187019584-aa92552f-0a16-4b5a-b6d6-5fa17804208a.png">

- After successfully cloning the repo, create a new virtual environment
  To create a new virtualenv; run <python3 -m venv ~/.<new name>> > 
                                    <source ~/.<new name>/bin/activate>

- Next install dependencies by running the Makefile with the command <make all>
<img width="1440" alt="Screenshot 2022-08-26 at 22 43 07" src="https://user-images.githubusercontent.com/47278559/187021746-dd21166d-d21d-403b-b1e0-8088928b4a40.png">

- Create a webapp using the command <az webapp up --name <webapp-name> --resource-group <resource-group-name> --runtime "PYTHON:<version>">
   In my own case, I have used webapp-name == "flaskbri";
                               resource-group-name == "Azuredevops";
                               version == 3.7
   The result can be seen as shown below
<img width="1440" alt="Screenshot 2022-08-27 at 02 09 00" src="https://user-images.githubusercontent.com/47278559/187021941-1fa901ec-c284-4e7f-ae9e-e59b0358e04d.png">

- Configuring the Github Actions
  We start by creating a new workflow in the Github repo. This can be done by clicking on Actions menu and then "Set up a workflow yourself"
    It is noteworthy that a starter code has been provided which includes the script to put in the workflow .yml file and named pythonapp.yml
    After successfully making the file commit the changes and then run the build session and the following result should be achieved. 
Notably, the green tick indicate the integration build successfully and all codes are running fine. However, a slight change is required in the stater script for the pythonapp.yml to build successfully. This involve upgrading the python version in the script to any other version aside version == 3.5
<img width="1440" alt="Screenshot 2022-08-26 at 22 48 43" src="https://user-images.githubusercontent.com/47278559/187022274-54fa822c-2040-4698-9709-34d0507fcde1.png">

- After creating the webapp.
> I have had various issues getting it to work; after various complaints, unanswered questions and enormous debugging, I am hoping I can get a better response to my problems through the submission review. 
> here is my current stand.
  > I have created the webapp as shown above and have managed to start it from the portal below, indicating the app status is running. 
<img width="1440" alt="Screenshot 2022-08-27 at 10 47 52" src="https://user-images.githubusercontent.com/47278559/187022892-12dc166e-77a7-4df9-94b6-17ae5970a49a.png">

 > That been the case, I ran the URL of the webapp <https://flaskbri.azurewebsites.net>, Its surprisingly never working as shown with the error.
<img width="1440" alt="Screenshot 2022-08-27 at 10 50 18" src="https://user-images.githubusercontent.com/47278559/187022974-80a35222-c868-4ab1-9941-ebbf988c9f70.png">
 > I had taken the initiative to diagnose it from the portal and hopefully solve the problems, however, I am not able to. 
INDEED I THOUGHT I WAS RESTRICTED BECAUSE I AM USING A PRIVATE ACCOUNT, AFTER HAVING SO MANY ISSUES TO ACCESS THE LAB, FINALLY WHEN I DID, THE SAME ISSUES OF DIAGNOSIS WAS RAISED, WHICH INDICATED THAT ITS NOT ABOUT THE SUBSCRIPTION OR CREDENTIALS. AND YES, ITS EXACTLY THE SAME PROBLEMS THAT THE DIAGNOSIS RETURNED EVEN AFTER SWITCHING TO THE UDACITY CREDENTIALS.
<img width="1440" alt="Screenshot 2022-08-27 at 10 55 12" src="https://user-images.githubusercontent.com/47278559/187023127-cb07c0e0-7a51-45cf-b93e-dab810ce6cc6.png">
 
 > Out of curiosity, I tried to make predictions and this is the error that was returned. Also I have changed the URL in the make_predict_azure_app.sh.  
<img width="1440" alt="Screenshot 2022-08-27 at 11 32 25" src="https://user-images.githubusercontent.com/47278559/187024368-b6f3e078-94ea-499a-b192-e2c52b4a1a0f.png">


- With this final step to completing this task, I will like to get clarifications on what I could have or that I am doing wrong that gave rise  to this error recurrently. 

Best