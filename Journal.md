# Project Walk Through

## Create a S3 bucket and Importing the Website

create a bucket

```aws configure
aws s3api create-bucket --bucket my-715013046770-bucket --region us-east-1
```

verify that the bucket has been created
`aws s3api list-buckets`

upload the content of website in the created bucket
cd udacity-starter-website

```
# Put a single file.
aws s3api put-object --bucket my-bucket-202203081 --key index.html --body udacity-starter-website/index.html
# Copy over folders from local to S3
aws s3 cp udacity-starter-website/vendor/ s3://my-715013046770-bucket/vendor/ --recursive
aws s3 cp udacity-starter-website/css/ s3://my-715013046770-bucket/css/ --recursive
aws s3 cp udacity-starter-website/img/ s3://my-715013046770-bucket/img/ --recursive
```

!(s3_bucket)[/images/S3_bucket_screenshot.png]

## Configuring the S3 Bucket

Go to the permission tab in the S3 and allow public access for hosting

edit the bucket policy and input the follow json policy

```
{
  "Version":"2012-10-17",
  "Statement":[
    {
      "Sid":"AddPerm",
      "Effect":"Allow",
      "Principal": "*",
      "Action":["s3:GetObject"],
      "Resource":["arn:aws:s3:::my-715013046770-bucket/*"]
    }
  ]
}
```

in the properties tab, Click on the “Edit” button to see the Edit static website hosting screen.  
enable the Static website hosting

input index.html as the default home page and error page for your website

## Distribute Website via CloudFront

create a cloud front distribution

```aws cloudfront create-distribution --origin-domain-name https://my-715013046770-bucket.s3.amazonaws.com/index.html \
--enable-origin-shield no --compress yes
```

!(Cloud_Front)[/images/CloudFront_screenshot.png]

Note: It may take up to 10 minutes for the CloudFront Distribution to be created.

!(Endpoint)[/images/Endpoint_screenshot.png]

- S3 object URl : https://my-715013046770-bucket.s3.amazonaws.com/index.html

- website-endpoint : http://my-715013046770-bucket.s3-website-us-east-1.amazonaws.com/

- CloudFront domain name : https://d1wciei2gibak2.cloudfront.net/
