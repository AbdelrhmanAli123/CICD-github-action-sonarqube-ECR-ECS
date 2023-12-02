# Prerequisites
#####
- Simple knowledge github action
- basic knowledge of ECR and ECS
- basic knowledge of sonar cloud
- aws cli

## project design 
![Screenshot 2023-12-02 215210](https://github.com/AbdelrhmanAli123/CICD-github-action-sonarqube-ECR-ECS/assets/133269614/9b695c2c-6b59-4478-a1a6-613effa426d3)


## Project steps
######

### create workflow
- press on the actions and set up a workflow yourself
- start to write you github action file

### create aws user
- create an aws user with full access to the ECR and ECS
- save the public and secret access keys in the repo secret
- I used full access for the sake of simplicity
- put your AWS account id in the repo secret as well

### create sonar cloud account
- create sonar cloud account and then create a new organization
- create a new project 
- save the key of the organization in the repo secret
- create a new token and save it in the repo secret
- save the key of the project in the repo secret
- save the sonar cloud URL in the repo secret as well, I mean this URL "https://sonarcloud.io"
- note: write the name and key of the organization and project the same for the sake of simplicity
  
### create RDS
- create RDS using the AWS console 
- store the credentials in the repo secret to use them later
- store the name and password and the endpoint in the repo secret


### setup ECR 
- create ECR
- store the endpoint of the repo in the repo secret
- store the name of the repo in the repo secret

### setup ECS
- create ECS cluster
  ![Screenshot 2023-12-01 011355](https://github.com/AbdelrhmanAli123/CICD-github-action-sonarqube-ECR-ECS/assets/133269614/b8822095-a3b8-4651-8e1c-ca6395f43dae)
- create task definition
- app works on port 8080
  ![Screenshot 2023-12-01 011438](https://github.com/AbdelrhmanAli123/CICD-github-action-sonarqube-ECR-ECS/assets/133269614/916b60b1-089b-446e-b9cd-ac478b450cfa)
- modify the task definition to use the ECR repo endpoint
- create ECS service
  ![Screenshot 2023-12-01 011420](https://github.com/AbdelrhmanAli123/CICD-github-action-sonarqube-ECR-ECS/assets/133269614/565ce0ea-d389-4224-96f9-3612678c57d7)
-  modify the ECS service to use the task definition and configure the Application load balancer via ECS service
-  put the health check route /login



### Here are all the secrets that I used 

![Screenshot 2023-12-01 195906](https://github.com/AbdelrhmanAli123/CICD-github-action-sonarqube-ECR-ECS/assets/133269614/0e016004-b412-4801-b485-8393be82f089)


### Change the workflow values with the appropriate values that you stored and then run the workflow 
![Screenshot 2023-12-01 013845](https://github.com/AbdelrhmanAli123/CICD-github-action-sonarqube-ECR-ECS/assets/133269614/f37dcef1-8d74-4eaf-86b0-f314c39edb95)

### Access the application using the load balancer endpoint 
![Screenshot 2023-12-01 011616](https://github.com/AbdelrhmanAli123/CICD-github-action-sonarqube-ECR-ECS/assets/133269614/4835c860-d6e0-464d-b3cb-08c6bb0ead63)

### Finally it works fine :)
