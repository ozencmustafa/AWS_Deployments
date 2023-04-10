## ASP.NET Application deployment with Elastic Beanstalks

There are multiple ways to deploy a .NET application on AWS, depending on your requirements and infrastructure preferences.

Deploying on Elastic Beanstalk: Elastic Beanstalk is a fully-managed service that automates the deployment of your .NET applications. 
You can easily deploy web applications, worker services, and other .NET-based services to Beanstalk. It supports popular .NET frameworks, such as ASP.NET, 
.NET Core, and others. Beanstalk takes care of provisioning, scaling, and managing the underlying infrastructure, so you can focus on your application code.


### Here are the basic steps that you can follow to create a ASP.NET application.

Create Application.

![image](https://user-images.githubusercontent.com/62793938/230967421-6dc3c000-b0b6-4949-a30f-84766333e216.png)

Application name is typed and Web Server Environment is selected.

![image](https://user-images.githubusercontent.com/62793938/230967810-8faf1a0c-2e21-4216-8588-4a596ce91fd6.png)

Domain can be left empty as AWS can select the available one.

Platform is selected .NET on windows.

![image](https://user-images.githubusercontent.com/62793938/230968352-ce55745d-b350-47b7-ba74-193a10ba4171.png)

We will deploy a sample application. 

![image](https://user-images.githubusercontent.com/62793938/230968511-92124179-c1eb-404c-91c1-ceb131abbe1c.png)

We are going to configure Service Access and we will create a new EC2 key pair.

![image](https://user-images.githubusercontent.com/62793938/230969219-95d2995c-4f91-4101-bd8f-5af3e56b3b34.png)

pem file created.

![image](https://user-images.githubusercontent.com/62793938/230969927-29f291d9-12c3-4d9d-acaf-4b1dc04415f8.png)


We go to IAM and create a service role.

![image](https://user-images.githubusercontent.com/62793938/230975010-eb734089-fcd5-4f8c-a0f6-f3974e977c3d.png)

Details are selected as below.

![image](https://user-images.githubusercontent.com/62793938/230975574-5adf9d5e-f7d9-4b87-9774-59e411a1e912.png)

Selected policy is SSMManagedInstanceCore.

![image](https://user-images.githubusercontent.com/62793938/230975947-ad139c9b-33e4-4ba8-ad94-189cd8b9660f.png)

![image](https://user-images.githubusercontent.com/62793938/230978909-ecbd526e-d980-4fd2-a95d-3e68be4fef5c.png)

Next Step is the define the network.

![image](https://user-images.githubusercontent.com/62793938/230979308-54d18146-97cd-4543-badb-e9f9670d79eb.png)
 
Instance Subnets are also selected, Screenshot should be updated.

Next Step is Configure instance traffic and scaling

![image](https://user-images.githubusercontent.com/62793938/230980171-75474064-e0a5-452c-aadf-39d8ee63b110.png)

![image](https://user-images.githubusercontent.com/62793938/230980259-f884ad44-1307-4e2e-9ed4-1c0046a362f8.png)

Next Next Submit, It will take sometime to create the environment.


















