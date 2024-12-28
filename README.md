## Deploying Static Website on AWS using S3 and CloudFront

Hello, In this project, I will share how I successfully deployed a static website on AWS, leveraging the powerful features of Amazon S3 for storage and CloudFront for content delivery.

### Overview

Amazon S3 provides a simple, scalable, and cost-effective storage solution for storing static website files, such as HTML, CSS, JavaScript, images, and other assets. It offers high durability, low latency, and automatic scalability, making it an ideal choice for hosting static websites.

CloudFront, on the other hand, is a global content delivery service that uses a network of edge locations to cache and deliver content to users from the location nearest to them. It helps improve the performance of static websites by reducing latency and providing faster load times for users across the world.

### Project Steps

I followed these steps to deploy my static website on AWS using S3 and CloudFront:

Creating an S3 Bucket: I created an S3 bucket to store my website files, and I uploaded my static website files to the bucket. I configured the bucket to act as a static website by enabling static website hosting, setting the default index document, and defining error document settings.

Configuring Bucket Permissions: I configured the appropriate permissions for the S3 bucket, including setting the bucket policy to allow public read access to the website files, and enabling cross-origin resource sharing (CORS) to allow my website to make requests to other domains.

Creating a CloudFront Distribution: I created a CloudFront distribution to serve my website files from edge locations around the world. I specified the S3 bucket as the origin for the distribution and configured cache behavior settings, such as setting the default TTL (Time-to-Live), enabling automatic compression of objects, and disabling Origin Shield.

Technologies Used
- Amazon S3: AWS service for storage of static website files.
- CloudFront: AWS content delivery service for caching and delivering content from edge locations.
- AWS CLI: AWS Command Line Interface for interacting with AWS services using the command line.

### Conclusion
Deploying my static website on AWS using S3 and CloudFront has been a rewarding experience. The combination of S3's simplicity and scalability with CloudFront's global content delivery capabilities has helped me deliver my website content quickly and reliably to users worldwide.

A walkthrough can be found in the [JOURNAL.md](/Journal.md) file
