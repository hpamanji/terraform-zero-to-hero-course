# Set Up Cloud Account Authentication

*Before Terraform can start spinning up resources in AWS, it needs access to your AWS account. That means setting up AWS credentials and making sure everything is properly configured. Let’s break it down step by step.*

## Install AWS CLI

👉 Head over to the [AWS CLI download page](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html) and follow the instructions to install AWS CLI

👉 Follow the installation steps, and once it's done, check if it's working by running:

```cmd
aws --version
```

If you see the version number, you're good to go!

## Create an IAM User

Now, let’s create a secure user for Terraform to interact with AWS. 

Instead of using your root account, we’ll create an IAM (Identity and Access Management) user with limited permissions.

- Log in to AWS Console: Use an admin account to access the AWS IAM Console. 

- Go to IAM → Users → Add User 

- Choose a username.

![Alt text](.pictures/AWS_IAM_User_creation_01.png?raw=true "Intro")

- Assign Permissions:
  For our first configuration, we will create an S3 bucket.
  Let's attach `AmazonS3FullAccess` access policy to our new user.
  Choose `attach policies directly`and search for `AmazonS3FullAccess`. Select the check box against the access policy and click on Next button.
 
  ![Alt text](.pictures/AWS_IAM_User_creation_02.png?raw=true "Intro")

  If you need access to other AWS services, assign relevant permissions.
  Click `Create User` finalize.
  
  ![Alt text](.pictures/AWS_IAM_User_creation_03s.png?raw=true "Intro")

- Create User & Save Credentials: AWS will generate an Access Key ID and Secret Access Key—save these somewhere safe (like a password manager). You’ll need them in the next step!

## Configure AWS CLI Credentials

To set up credentials, use the AWS CLI command 'aws configure'.

```cmd
aws configure
```

You’ll be prompted to enter:

1. AWS Access Key ID
2. AWS Secret Access Key
3. Default region name (e.g., us-east-1)
4. Default output format (leave as None)

```cmd
AWS Access Key ID [****************7WPF]:
AWS Secret Access Key [****************giL/]:
Default region name [us-west-2]:
Default output format [json]:
```
