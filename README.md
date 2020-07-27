<h1>DevOps-Task6</h1>
<h2>Objective :-</h2>
<h3>Jenkins Job DSL Automation.</h3>

<h3>Steps :-</h3>

1. Create container image that’s has Jenkins installed  using dockerfile  Or You can use the Jenkins Server on RHEL 8/7

2.  When we launch this image, it should automatically starts Jenkins service in the container.

3.  Create a job chain of job1, job2, job3 and  job4 using build pipeline plugin in Jenkins.

4.  Job2 ( Seed Job ) : Pull  the Github repo automatically when some developers push repo to Github.

5. Further on jobs should be pipeline using written code  using Groovy language by the developer.

6. Job1 :  

    1. By looking at the code or program file, Jenkins should automatically start the respective language interpreter installed image container to deploy code on top of Kubernetes ( eg. If code is of  PHP, then Jenkins should start the container that has PHP already installed )
    
    2.  Expose your pod so that testing team could perform the testing on the pod.
    
7.  Job3 : Test your app if it  is working or not. If app is not working , then send email to developer with error messages and redeploy the application after code is being edited by the developer.

<h3>Requirements :-</h3>
 
 1. Knowledge of Docker.
 
 2. Knowledge of Jenkins.
 
 3. Knowledge of Kubernetes.
 
 In this article we will learn how to create a Jobs/Pipeline in Jenkins using DSL.

 This is an update for the article :- https://github.com/gauravsjc02/DevOps-Task2
 
 <h2> Plugins required to perform this task are :- </h2>
 
 1. JOB DSL (For Running DSL Script for Seed Jobs)
 
 2. Github Plugin (FOR SCM)
 
 3. CloudBee Docker Build and Publish Plugin.
 
 4. Email Extension Plugin. 
 
 5. Build Pipeline Plugin.
 
 6.Workspace Cleanup Plugin (TO clean the workspace in case of re-run/rebuild).
 
 
 ![plug](https://github.com/gauravsjc02/DevOps-Task6/blob/master/Task6/plugins.png)
 
 
 On Installation of these plugings Go to -> <b>Manage Jenkins >> Configure Global Security >> Uncheck the Enable Script Check Security for JOB DSL.<b>
  
 ![1](https://github.com/gauravsjc02/DevOps-Task6/blob/master/Task6/uncheck.png)
 
 
 Now, well create the seed job.
 
 SEED JOB : This job generates other jobs and is also attached to a webhook. It will run every time a developer pushes an update. 

 <h3> Generated Jobs </h3>
 
 Job1: Download and interpret the code from Github and build the image using given Dockerfile and push it to Dockerhub.

 Job2: Deploy and expose our webserver on Kubernetes so that testing can be performed accordingly.

 Job3: Send status to the team as per the result of the build and deployment status.
 
 <b> DSL script of seed job :-<b>
  
  ![2](https://github.com/gauravsjc02/DevOps-Task6/blob/master/Task6/processjob.png)
  
  
  ![3](https://github.com/gauravsjc02/DevOps-Task6/blob/master/Task6/seed.png)
  
  
  <h3>Build Pipeline View :-</h3>
  
  ![4](https://github.com/gauravsjc02/DevOps-Task6/blob/master/Task6/build.png)
