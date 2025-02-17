## Set Up Cloud Account Authentication

*Before Terraform can start spinning up resources in AWS, it needs access to your AWS account. That means setting up AWS credentials and making sure everything is properly configured. Don’t worry—it’s easier than you think! Let’s break it down step by step.*

---
### Install AWS CLI

👉 Head over to the AWS CLI download page and follow the instructions to install AWS CLI

👉 Follow the installation steps, and once it's done, check if it's working by running:

```cmd
aws --version
```

If you see the version number, you're good to go!

### Create an IAM User1

Now, let’s create a secure user for Terraform to interact with AWS. 

Instead of using your root account, we’ll create an IAM (Identity and Access Management) user with limited permissions.

- Log in to AWS Console: Use an admin account to access the AWS IAM Console. 

- Go to IAM → Users → Add User 

- Choose a username & enable Programmatic Access (so Terraform can use an API key).

- Assign Permissions: For basic EC2 management, attach the AmazonEC2FullAccess policy. If you need access to other AWS services, assign relevant permissions. 

- Create User & Save Credentials: AWS will generate an Access Key ID and Secret Access Key—save these somewhere safe (like a password manager). You’ll need them in the next step!

### Configure AWS CLI Credentials

To set up credentials, use the AWS CLI command 'aws configure'. You’ll be prompted to enter:

AWS Access Key ID
AWS Secret Access Key
Default region name (e.g., us-east-1)
Default output format (leave as None)

```cmd
C:\>aws configure
AWS Access Key ID [****************7WPF]:
AWS Secret Access Key [****************giL/]:
Default region name [us-west-2]:
Default output format [json]:
```
