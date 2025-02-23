Password Compromise Check Website

Overview

This project involves hosting a website that allows users to check whether their passwords have been compromised in previous data breaches using the Have I Been Pwned API. The website is hosted on AWS S3 as a static website.

Steps to Deploy the Website

Step 1: Create a Bucket

Log in to your AWS Management Console.

Navigate to the S3 service.

Click "Create bucket."

Provide a unique bucket name.

Select the appropriate AWS region.

Click "Create bucket."

Step 2: Enable Static Website Hosting

Open the bucket settings.

Navigate to the "Properties" tab.

Scroll down to the "Static website hosting" section.

Choose "Enable" and specify an index document (e.g., index.html).

Click "Save."

Step 3: Edit Block Public Access Settings

Go to the "Permissions" tab.

Click "Edit" under "Block public access."

Uncheck "Block all public access."

Confirm the changes and save.

Step 4: Add a Bucket Policy to Make Content Publicly Available

Go to the "Permissions" tab.

Click "Bucket Policy."

Add the following policy:

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::your-bucket-name/*"
    }
  ]
}

Replace your-bucket-name with the actual name of your S3 bucket.

Save the policy.

Step 5: Configure an Index Document

In the "Properties" tab under "Static website hosting," set index.html as the index document.

Save the configuration.

Step 6: Configure an Error Document

Set an error document (e.g., error.html) to handle incorrect requests.

Save the configuration.

Step 7: Test Your Website Endpoint

Copy the website endpoint URL from the "Static website hosting" section in the bucket properties.

Open a browser and navigate to the URL.

Verify that your website loads correctly.

Step 8: Clean Up

If you no longer need the website:

Delete all objects in the S3 bucket.

Delete the S3 bucket itself.

Re-enable "Block all public access" for security.

Conclusion

By following these steps, you successfully host a static website on AWS S3 that allows users to check for password breaches using the Have I Been Pwned API. Ensure that user data is handled securely and maintain compliance with best security practices.
