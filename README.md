# AWS_Deployments
There are several ways to host a web application on AWS, depending on the specific requirements of the application, the level of control and customization needed, and the budget and resources available. Here are some common options:

### Amazon Elastic Compute Cloud (EC2): 
With EC2, you can provision virtual servers in the cloud and install your own software and applications on them. This gives you full control over the server environment, but requires more management and maintenance compared to other options.

### AWS Elastic Beanstalk: 
Elastic Beanstalk is a platform as a service (PaaS) offering that allows you to deploy web applications and automatically handles the underlying infrastructure, such as load balancing, scaling, and monitoring. This makes it easier to deploy and manage applications, but with less control and customization compared to EC2.

### AWS Lambda: 
Lambda is a serverless computing platform that allows you to run code in response to events without provisioning or managing servers. It's well-suited for applications with sporadic or unpredictable traffic, but has limitations on the type and duration of code that can be run.

### AWS Fargate: 
Fargate is a container platform that allows you to run Docker containers in the cloud without managing the underlying infrastructure. It provides more control and customization than Lambda, but requires more setup and configuration compared to Elastic Beanstalk.

### Amazon Lightsail: 
Lightsail is a simplified cloud hosting service that provides pre-configured virtual private servers (VPS) and applications for common use cases, such as WordPress, Drupal, and Magento. It's designed for users who want a simple and low-cost option without the need for advanced customization or scalability.


One of the most cost-effective ways to host a static website developed with React on AWS is to use Amazon S3 and Amazon CloudFront.

Here's a high-level overview of the steps involved:

```
1. First, build your React application for production using a tool like npm run build or yarn build. This will generate a bundle of optimized static files that can be served to the client.

2. Next, create an S3 bucket and upload the static files to the bucket. Make sure to set the permissions on the bucket to allow public access to the files.

3. Configure the bucket to act as a static website by enabling the Static website hosting feature in the bucket properties. Specify the default index document and error document, if applicable.

4. Create a CloudFront distribution to serve the static files from the S3 bucket. CloudFront is a content delivery network (CDN) that caches content at edge locations around the world, providing low-latency access to users from any location.

5. Finally, configure your domain name to point to the CloudFront distribution. This can be done by creating a CNAME record in your DNS settings that points to the CloudFront distribution domain name.
```
