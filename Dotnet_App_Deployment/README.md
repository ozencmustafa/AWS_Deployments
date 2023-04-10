## ASP.NET Application deployment with Elastic Beanstalks

There are multiple ways to deploy a .NET application on AWS, depending on your requirements and infrastructure preferences.

Deploying on Elastic Beanstalk: Elastic Beanstalk is a fully-managed service that automates the deployment of your .NET applications. 
You can easily deploy web applications, worker services, and other .NET-based services to Beanstalk. It supports popular .NET frameworks, such as ASP.NET, 
.NET Core, and others. Beanstalk takes care of provisioning, scaling, and managing the underlying infrastructure, so you can focus on your application code.


### Here are the basic steps that you can follow to create a ASP.NET application.

1. Create a new .NET project: Open Visual Studio and create a new ASP.NET Web Application project. Choose the Empty template and select the .NET Framework version you want to use.

2. Add a web page: Right-click on the project in the Solution Explorer and select Add -> New Item. Choose the HTML Page template and give it a name, such as index.html. In the file, add the HTML and CSS code for your website. You can also use JavaScript if needed.

3. Configure the project: Open the project properties and set the Start URL to the name of the HTML page you created (e.g. "index.html"). You may also want to configure other project settings, such as the target framework version and build options.

4. Build and run the project: Press F5 or select the Debug -> Start Debugging menu option to build and run the project. The website should open in your default web browser and display the contents of your HTML page.

### Deployment steps for Elastic Beanstalk

1. Starts with adding AWS extension to Microsoft Visual Studio.

![image](https://user-images.githubusercontent.com/62793938/230800296-c1bd6396-3476-4db5-806c-edfcf6286abe.png)

2. Under View select AWS Explorer.

![image](https://user-images.githubusercontent.com/62793938/230800400-da2cae7a-6040-4665-a60c-6270efe318bb.png)

Now We have to integrate our AWS to our Studio Code.

![image](https://user-images.githubusercontent.com/62793938/230800956-2587ed08-06dd-4e18-a14c-837ef43f849c.png)

You create user, user_group and access_key to login to Visual Studio. 
You also add the new user to the new user_group as Beanstalk Admin permission was given to the user_group.
User_group is created with Elastic Beanstalk Admin rights. 
Access_key can be downloaded as a csv file and can be import to VS.

![image](https://user-images.githubusercontent.com/62793938/230801359-4d4ff808-752f-4efe-8399-2b22586a13ea.png)

Now you can access to AWS from your VS IDE.

![image](https://user-images.githubusercontent.com/62793938/230801440-ed3231ee-53c9-4ce7-a2c8-70d211bd1dd4.png)

Now right click on the project folder demo_dotnet and select AWS Elastic Beanstalk 

![image](https://user-images.githubusercontent.com/62793938/230801654-4b123dfd-90e7-4a16-83c2-9a9c95231aed.png)


We click Next.

![image](https://user-images.githubusercontent.com/62793938/230801777-0e05d5ed-1657-4e0d-8ff7-045f442c93f4.png)

We gave a name to Application and Environment and also check the availability of the URL. Than click Next.

![image](https://user-images.githubusercontent.com/62793938/230802360-6badc065-c048-4dab-a8b5-8763ef1f3d76.png)


We select t2.micro as instance type. Unselect Single instance environment.

![image](https://user-images.githubusercontent.com/62793938/230802476-1ba329e3-cf01-4700-9fae-f0e20b12ec52.png)

Then Next-Next-Deploy.







