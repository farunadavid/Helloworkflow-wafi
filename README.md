This deployment is done using the following stacks

Jenkins ⚡️⚡️⚡️⚡️⚡️
Kubernetes✨
Docker✨
Temporal-server✨
Golang✨
This is how it all begun... We started first with the setup of the temporal server and we use Docker-compose for this setup by editing some files and ensure the server and it's relevant dependencies are set-up 


RUN THE FOLLOWING COMMAND

cd Kubernetes docker-compose up -d

After the server is up and running we setup the cluster that will be deployed using terraform.

We write a terraform configuration file to achieve this deployment.Which is not a subject of this deployment

We Then make sure the application is set-up and we run it using the following command
go run ./worker/main.go

That command starts the worker processes for running thw workflows connected to the application To start up the application and execute the application we look at the below snippet and output go run ./starter/main.go
![workflow1](https://user-images.githubusercontent.com/116575399/216769049-1d9623b4-1470-40be-aa36-bd91c5f0a319.png)


Worker application

Now we have seen the worker started, lets now view the web UI to see the workflow execution

WEB UI
![Screworkflow2](https://user-images.githubusercontent.com/116575399/216771430-ad6a624a-4943-4223-b6d5-4c58951400e3.png)


Now that we have the web UI running completed status on the workflow, lets try to chenge it's input and lets see if we still have a resilient service Code Change Snippet

With that change lets look at the UI for the mode of its operation **Mode of operation

Then lets see what happens after its completed Completed status

Since we see how this server operates lets examine how to work with CI/CD

Deploying a fault tolerant application using CI/CD running with a temporal-server
To deploy Temporal-server on a dashboard in a kubernetes environment run the following commands

cd kubernetes && cd k8s && kubectl apply -f .

And we have the Dashboard present HERE

Temporal UI on Kuberenetes

But lets look at it using the DevOps way

AS DevOps Engineers we use Jenkins to Deploy the workloads
We create a pipeline and then we deploy the workloads by using webhooks that has been proconfigured in the environments
Final Remarks
We see the importance of temporal server in ensuring resiliency and high availability of the instances
Ruuning temporal is very vital for running microservices applications that needs high resiliency

I once deployed a Java Microservice application with temporal and this application was great because temporal leveraged it's ability to send retries even when one services is down to ensure there is high availabilty at all times, without throwing up an error.

This service can be improved by building it's dependence and enusring the instances are made multiple for loadBalancing and redundance

That's the little i can discuss in this documentation. Thanks for making it to the end✊✊✊👊🏼🫰🫰.


