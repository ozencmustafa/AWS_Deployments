## React App deployment with Amazon S3 and Amazon CloudFront.

One of the most cost-effective ways to host a static website developed with React on AWS is to use Amazon S3 and Amazon CloudFront.
CloudFront is caching and improves the performance also one of the advantage of using CloudFront is that allows you to have https.

https://www.awsreactozenc.net/ is deployed with Amazon S3 and CloudFront.

![image](https://user-images.githubusercontent.com/62793938/230742100-b7d58ab4-936e-4887-b9bb-2f8cff8b3803.png)


Here's a high-level overview of the steps involved:

1. First, build your React application for production using a tool like npm run build or yarn build. This will generate a bundle of optimized static files that can be served to the client.

![image](https://user-images.githubusercontent.com/62793938/230743714-551b626b-6575-4011-bd30-a86d2cff6704.png)

You can start the react app on your local as below.

![image](https://user-images.githubusercontent.com/62793938/230743908-41718115-b569-4499-bc59-e23d5e190525.png)

We stopped the application with CTL+C as we confirmed that is running then we will bundle all files so that we can deploy on cloud.

![image](https://user-images.githubusercontent.com/62793938/230744086-3e4a0847-d758-4e3b-b748-dba535d2fe38.png)


2. Next, create an S3 bucket and upload the static files to the bucket. Make sure to set the permissions on the bucket to allow public access to the files.

![image](https://user-images.githubusercontent.com/62793938/230744209-9c548d4a-1418-449c-8a13-eb3462824fa9.png)

We are going to have a bucket for awsreactozenc.net and a bucket for www.awsreactozenc.net. Reason to have both is that one of them is going to be the authority so it is going to have all of our contents and the other is goin to be basically for redirect so someone goes to that website its going to redirect us to the other version.

![image](https://user-images.githubusercontent.com/62793938/230744710-a609df89-6800-42f5-83e5-2db34be52beb.png)

Once buckets are generated to click on the www.awsreactozenc.net bucket and click add files and select the individual files from the build directory then upload all individual files and then select add folder and upload the the static folder contents.

![image](https://user-images.githubusercontent.com/62793938/230744902-c1ec533d-cdc1-435f-8f25-93a725d29c7f.png)

Then you go the Bucket and enable public access. See the 3 steps.

![image](https://user-images.githubusercontent.com/62793938/230745136-c5035b5b-9d16-413c-a684-7810acf31292.png)

Next is copy below policy into Bucket Policy. Basically it allow to run getobject from www.awsreactozenc.net. 
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::www.awsreactozenc.net/*"
            ]
        }
    ]
}
```
So far everything is good and we are  publicly accesiable.
![image](https://user-images.githubusercontent.com/62793938/230745403-cb766269-a09e-431f-89a0-d99cec038898.png)

3. Configure the bucket to act as a static website by enabling the Static website hosting feature in the bucket properties. Specify the default index document and error document, if applicable.

Now we need to enable static website hosting on www.awsreactozenc.net. 

On Properties tab we scroll down and enable Static Website hosting.

We select host static web site for www bucket and also give the index.html name in the selection.

![image](https://user-images.githubusercontent.com/62793938/230745591-ac35b8d2-5b7e-4a1d-ba07-59285d0f1072.png)

We also go the non www bucket and go to the properties tab and click edit to Static Website Hosting and configure as redirect.

![image](https://user-images.githubusercontent.com/62793938/230745779-d1e27e46-9ced-4fd3-92eb-e264e5596b98.png)

Since now we are done on S3 and next we go to Route 53 where we need to make some modifications.

First we go to Registered Domains on the left.
![image](https://user-images.githubusercontent.com/62793938/230747414-6ef56b5c-0b3b-45b0-8af7-6109e882e7a7.png)

Then we create two DNS records. 
One for www bucket.

![image](https://user-images.githubusercontent.com/62793938/230747540-6e6d388e-3990-4245-baf1-c2ba58c345fd.png)

One for the non www bucket.

![image](https://user-images.githubusercontent.com/62793938/230747576-a4f7572e-1249-4221-b16f-4b2cb1a2b424.png)

We leave the subdomain empty.

![image](https://user-images.githubusercontent.com/62793938/230747621-fc55dd5f-e629-4b20-950f-f3dfc6cb27d8.png)

Then we click to Create Records!

And www.awsreactozenc.net is accesiable!!

4. Create a CloudFront distribution to serve the static files from the S3 bucket. CloudFront is a content delivery network (CDN) that caches content at edge locations around the world, providing low-latency access to users from any location.

First we go to Certificate Manager Section and request a certificate to make our wibesite secure.

![image](https://user-images.githubusercontent.com/62793938/230747873-e040db76-7a45-4727-8253-5b4970efb7fa.png)

We can valide our certificates through the DNS validity, simply by adding the CNAME into the Route 53. It is very simple as we just click the button saying add to the DNS records.

After adding the CNAME into DNS, it can take a while until that certificates to be successfuly validated.

![image](https://user-images.githubusercontent.com/62793938/230748124-14114504-f90e-4bdc-824d-e735975145cb.png)


Now we search for CloudFront and click CloudFront Distrubution Creation.

![image](https://user-images.githubusercontent.com/62793938/230748234-eb7c004c-6f65-4f0b-8389-10d05786635a.png)

Origin Domain Name should be copied from S3 Bucket -- Properties -- Static Website

![image](https://user-images.githubusercontent.com/62793938/230748309-334b8064-2a56-4b37-a06f-d34e303e19d3.png)

    a. Redirect from HTTP to HTTPS should be selected.

    b. SSL certificates should be selected.

    c. So we do the same for the non www bucket and create a new distrubution.


The Difficulty for me was to select http in Origin domain.

![image](https://user-images.githubusercontent.com/62793938/230791323-5fba32d1-e28e-43d6-b56f-9d3ef34bb715.png)

In Behviour Settings Redirect HTTP to HTTPS is selected.

![image](https://user-images.githubusercontent.com/62793938/230791354-0a913f65-9f03-4952-8c66-7755989097c2.png)

In General Settings Alternate domain name will be created and Custom SSL certificate will be selected.

![image](https://user-images.githubusercontent.com/62793938/230791487-05cd80e7-2b68-4027-a7b7-3dddb9fe70b9.png)

We also create a cloudfront distribution for non-www bucket.

5. Finally, configure your domain name to point to the CloudFront distribution. This can be done by creating a CNAME record in your DNS settings that points to the CloudFront distribution domain name.

And Next step is going to update A records for www and non www buckets in the "Route Traffic to section"  from pointing S3 to CloudFront.

![image](https://user-images.githubusercontent.com/62793938/230749115-86cdfe4e-f9df-4098-930c-5fc665c9e195.png)


You can click Shift_CTL+J to open console and select Networks and reload the website confirm that Server and Via is Cloudfront.


If you change your Website and want to repool all contents from S3 again you can go to Cloudfront and go to distribution settings and select Invalidations.

![image](https://user-images.githubusercontent.com/62793938/230794835-fa172b98-5a67-48c5-8f6a-86cea8267128.png)

We create invalidation by addding all directories and subdirectories and files by adding /**/*

![image](https://user-images.githubusercontent.com/62793938/230794949-0d9d6cec-3d82-48b1-ab6c-56ad39b3fcb7.png)







