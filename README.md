# simple-terraform-project

## Deploying a Static Website on AWS S3 using Terraform

## Step 1: Install Prerequisites

Before creating anything, make sure you have:

## 1. Terraform installed

Download from terraform.io

Verify installation with terraform -v in the terminal

## 2. AWS CLI installed (optional but recommended)

Download from aws.amazon.com/cli

Configure it with your AWS credentials:

```
aws configure
```
Provide Access Key, Secret Key, and Region (e.g., us-east-1)

## 3. AWS Account

Create one if you don’t have it: aws.amazon.com

Ensure your credentials have permission to manage S3 buckets.

## Step 2: Create a Project Directory

## 1. Open your terminal.

## 2. Create a folder for the project, e.g., terraform-website:

```
mkdir terraform-website
cd terraform-website
```

## 3. Inside this folder, create subfolders for your website files:

mkdir assets

## 4. Place your website files inside the folder:

index.html → Homepage

error.html → Custom error page

Images, such as profile.png

## Step 3: Define Terraform Configuration

Terraform uses .tf files to define infrastructure. You will need three main components:

## 3.1 Provider Configuration

Create main.tf and specify AWS provider and region:

This tells Terraform which cloud provider to use and in which region.

## 3.2 Create S3 Bucket

Define an S3 bucket resource.

Assign a unique bucket name (all bucket names must be globally unique in AWS).

## 3.3 Configure Bucket Ownership and Public Access

Ensure the bucket is owned by you and objects uploaded are also owned by you.

Configure public access to allow the website to be accessible publicly.

## 3.4 Upload Website Files

Use S3 object resources in Terraform to upload index.html, error.html, and images.

Assign public-read ACL to make them accessible via URL.

## 3.5 Configure Static Website Hosting

Set the index document (usually index.html) and error document (error.html).

This allows AWS S3 to serve the site as a static website.

## 3.6 Output the Website Endpoint

Terraform can output the public website URL so you can easily access it.

## Step 4: Initialize Terraform

Open terminal in your project folder.

Run:
```
terraform init
```

Downloads required provider plugins (AWS in this case).

## Step 5: Preview Changes

Run:

```
terraform plan
```

Terraform will show all resources it plans to create (buckets, objects, ACLs, etc.)

Check carefully that the bucket name is correct and matches your intention.

## Step 6: Apply Configuration

Run:

```
terraform apply
```

Terraform will ask for confirmation (yes).

Once applied, it will create:

S3 bucket

Public access policies

Website files

Website configuration

Terraform will output the website endpoint URL.

## Step 7: Access the Website

Copy the endpoint URL from Terraform output.

Open it in a browser.

Your static website should now be live!

## Step 8: Manage and Update the Website

Add new files or update existing ones in your project folder.

Run:

```
terraform apply
```

Terraform will update the S3 bucket automatically.

Delete resources (if needed) with:

```
terraform destroy
```
This will remove the S3 bucket and all uploaded objects.