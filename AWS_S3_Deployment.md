## Amazon S3 and Amazon CloudFront.
One of the most cost-effective ways to host a static website developed with React on AWS is to use Amazon S3 and Amazon CloudFront.
CloudFront is caching and improves the performance also one of the advantage of using CloudFront is that allows you to have https.

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

We are going to have a bucket for awssimplify.io and a bucket for www.awsreactozenc.io. Reason to have both is that one of them is going to be the authority so it is going to have all of our contents and the other is goin to be basically for redirect so someone goes to that website its going to redirect us to the other version.

![image](https://user-images.githubusercontent.com/62793938/230744710-a609df89-6800-42f5-83e5-2db34be52beb.png)

Once buckets are generated to click on the www.awsreactozenc.io bucket and click add files and select the individual files from the build directory then upload all individual files and then select add folder and upload the the static folder contents.

![image](https://user-images.githubusercontent.com/62793938/230744902-c1ec533d-cdc1-435f-8f25-93a725d29c7f.png)

Then you go the Bucket and enable public access. See the 3 steps.

![image](https://user-images.githubusercontent.com/62793938/230745136-c5035b5b-9d16-413c-a684-7810acf31292.png)

Next is Bucket Policy.
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
                "arn:aws:s3:::Bucket-Name/*"
            ]
        }
    ]
}
```

3. Configure the bucket to act as a static website by enabling the Static website hosting feature in the bucket properties. Specify the default index document and error document, if applicable.

4. Create a CloudFront distribution to serve the static files from the S3 bucket. CloudFront is a content delivery network (CDN) that caches content at edge locations around the world, providing low-latency access to users from any location.

5. Finally, configure your domain name to point to the CloudFront distribution. This can be done by creating a CNAME record in your DNS settings that points to the CloudFront distribution domain name.

