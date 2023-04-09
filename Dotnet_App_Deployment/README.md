## ASP.NET Application deployment with Elastic Beanstalks

There are multiple ways to deploy a .NET application on AWS, depending on your requirements and infrastructure preferences.

Deploying on Elastic Beanstalk: Elastic Beanstalk is a fully-managed service that automates the deployment of your .NET applications. 
You can easily deploy web applications, worker services, and other .NET-based services to Beanstalk. It supports popular .NET frameworks, such as ASP.NET, 
.NET Core, and others. Beanstalk takes care of provisioning, scaling, and managing the underlying infrastructure, so you can focus on your application code.


### Here are the basic steps you can follow to create a ASP.NET application.

1. Create a new .NET project: Open Visual Studio and create a new ASP.NET Web Application project. Choose the Empty template and select the .NET Framework version you want to use.

2. Add a web page: Right-click on the project in the Solution Explorer and select Add -> New Item. Choose the HTML Page template and give it a name, such as index.html. In the file, add the HTML and CSS code for your website. You can also use JavaScript if needed.

3. Configure the project: Open the project properties and set the Start URL to the name of the HTML page you created (e.g. "index.html"). You may also want to configure other project settings, such as the target framework version and build options.

4. Build and run the project: Press F5 or select the Debug -> Start Debugging menu option to build and run the project. The website should open in your default web browser and display the contents of your HTML page.

### Deployment steps on AWS

1. Starts with adding AWS extension to Microsoft Visual Studio 

![image](https://user-images.githubusercontent.com/62793938/230800296-c1bd6396-3476-4db5-806c-edfcf6286abe.png)

2. Under View select AWS Explorer

![image](https://user-images.githubusercontent.com/62793938/230800400-da2cae7a-6040-4665-a60c-6270efe318bb.png)


