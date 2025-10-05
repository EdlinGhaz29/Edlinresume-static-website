# Edlin Static Resume Website (AWS S3 + CloudFront)

This Project is a static resume website created to showcase my professional background, certifications and cloud projects.
It demonstrates hands-on experience in deploying and managing static web hosting on AWS, using Amazon S3 for hosting and and Cloudfront for secure, high-performance global delivery.

Architecture Overview

This website follows a serverless architecture that combines AWS S# and Cloudfront to deliver content efficiently across the globe.


        ┌──────────────────────────┐
        
        │        User Browser      │
        
        │ (Accesses website via    │
        
        │  CloudFront URL or DNS)  │
        
        └────────────┬─────────────┘
        
                     │ HTTP Request
                     
                     ▼
                     
        ┌──────────────────────────┐
        
        │     Amazon CloudFront    │
        
        │ (CDN – caches and serves │
        
        │  content from edge locs) │
        
        └────────────┬─────────────┘
        
                     │ Fetches content
                     
                     ▼
        ┌──────────────────────────┐
        
        │       Amazon S3          │
        
        │ (Static Website Hosting  │
        
        │  – HTML, CSS, JS, media) │
        
        └──────────────────────────┘

Component  : Description
1. Amazon S3 : Host Static Website files (HTML, CSS, JS and Media).
2. Amazon Cloudfront: Delivers content globally with low latency and HTTPS support.

Tech Stack

- FrontEnd: HTML, CSS, Vanilla Javascript.
- Hosting: AWS S3 (Static WEbsite hosting).
- CDN: AWS Cloudfront.
- Deployment: Manual upload via AWS Management Console.
- Version Control: Git/GitHub.

Key Features

- Fully responsive static website.
- Secure, fast global delivery through Cloudfront.
- HTTPS enabled by default.
- Optimized for minimal load times.
- Simple manual deployment process using AWS Console.

Deployment Step

1. Create an S3 Bucket.
   - In the AWS Console, open Amazon S3 and create a new bucket, name: edlin-resume-staticwebsite.
   - Enable Static Website Hosting under the Properties Tab.
   - Set index document to index.html.

2. Upload Website files.
   - In the Object tab, click upload and Add file/folder.
   - Select all your website files (HTML,CSS,JS, images). 
   - Click Upload to deploy them to the bucket.

3. Configure Permission.
   - Under Permissions, enable Block all Public Access: OFF.
   - Apply a bucket policy allowing public read access for the website files.
   - Bucket static website endpoint: http://edlin-resume-staticwebsite.s3-website-us-east-1.amazonaws.com

4. Create a Cloudfront distribution.
   - Open Amazon Cloudfront and create Distribution.
   - pointing to your S3 website endpoint.
   - Set your S3 bucket as the Origin.
   - Enable Redirect HTTP to HTTPS for secure(will be charged)
   - Set Default Root object to index.html (since it serve as entry point).
     If not it will return an XML document isting the contents of that directory. 
     This can expose sensitive information about your website's structure and content,
     which is a security risk.
   - Distribution Domain Name: d3d366veqcd1ec.cloudfront.net

5. Update Content.
   When making future update:
   - Re-upload my updated files through the S3 Console.
   - In Cloudfront, click Create Invalidation and enter /* to clear cached content and force refresh.
  
     *This time, deployment is fully manual using AWS Management Console, without CLI or automation pipeline.
      This method is suitable for small static website and only occasionally update.
      If we want to host a bigger static website, better use automation (GitHub Action or CodePipeline)

Learning Objectives

- Configure and host staic website using Amazon S3.
- Integrate Cloudfront for performance.
- Manage manual deployment using the AWS Management Console.
- Understand cache invalidation and static hosting principle.

To view the website locally:
1. Clone the repository:
    ```bash
    git clone https://github.com/EdlinGhaz29/Edlinresume-static-website.git
    ```
2. Open `index.html` in your browser.

Deploying

Deploy to AWS S3 + CloudFront
1. Upload all files in this repo to an AWS S3 bucket.
2. Enable static website hosting on the bucket.
3. Set `index.html` as the root document.
4. Make the files public or set a bucket policy for read access.
5. Create a CloudFront distribution pointing to your S3 website endpoint.



For any questions, reach out via [GitHub Issues](https://github.com/EdlinGhaz29/mulin_static_website/issues) or [connect on GitHub](https://github.com/EdlinGhaz29).

---
