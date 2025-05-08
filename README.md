# AWS S3 Lifecycle Manager ![AWS](https://img.shields.io/badge/Built%20with-AWS-orange?style=flat&logo=amazonaws)![Project Status](https://img.shields.io/badge/status-finished-green)

This project configures Amazon S3 lifecycle rules to automate **storage cost optimization**. It transitions objects between storage classes (Standard ➜ Infrequent Access ➜ Glacier), and deletes outdated data based on rules you define.

---

## Project Goal

-  Reduce S3 storage costs with lifecycle transitions
-  Automatically delete unnecessary or old files
-  Learn how to configure S3 Lifecycle rules manually or with code
-  Demonstrate real-world AWS automation skills

---

## 🧰 Services Used

| AWS Service     | Purpose                                           |
|-----------------|---------------------------------------------------|
| Amazon S3        | Object storage with lifecycle rule support        |
| S3 Lifecycle     | Automates transitions & deletions                 |
| AWS IAM          | Controls access to manage lifecycle policies      |
| (Optional) CloudFormation or Boto3 | Infrastructure as Code or programmatic setup |

---

## 🛠️ Setup Instructions

###  Step 1: Create an S3 Bucket

1. Go to the [S3 Console](https://s3.console.aws.amazon.com/s3/)
2. Click **Create Bucket**
3. Name your bucket (e.g., `my-lifecycle-demo-bucket`)
   ![image alt](https://github.com/Juniorklb/S3-Lifecycle-Manager/blob/f1d788445f90976cb798cfb5918a8cf7cc5e1073/images/Bucketname.PNG)
5. Leave default settings or customize as needed
6. Create the bucket

#### ⚙️ Option 2: AWS CLI
    aws s3api create-bucket \
      --bucket s3-lifecycle-demo-bucket \
      --region us-east-1 \
      --create-bucket-configuration LocationConstraint=us-east-1
---

###  Step 2: Add Lifecycle Rules (Manually)
#### 1. Go to Your S3 Bucket
-  Open the AWS [S3 Console](https://s3.console.aws.amazon.com/s3/)
-  Click on your bucket ``s3-lifecycle-demo-bucket``
#### 2. Navigate to the “Management” Tab
- In the bucket dashboard, click on “Management”
- Find the section titled Lifecycle rules
- Click “Create lifecycle rule.”
####  Create the Rule
- Rule Name: ``TransitionAndExpireRule``
- Choose Scope:
- Apply to all objects (or add a prefix if needed like ``logs/``)

#### Set Lifecycle Actions
-  Transition actions:
-  Transition to Infrequent Access (IA) after 30 days
-  Transition to Glacier Flexible Retrieval after 60 days
  ![image alt](https://github.com/Juniorklb/S3-Lifecycle-Manager/blob/385a79a4bbafafdd00ae0483b30f36bbfc84de69/images/transactioncurrent.PNG)
-  Expiration actions:
-  Delete objects after 90 days
     - Leave other options as default.
- Save
- Click Create rule at the bottom.
---

### Conclusion
The AWS S3 Lifecycle Manager project demonstrates how to efficiently manage and automate the lifecycle of S3 objects to reduce storage costs and maintain compliance. By leveraging lifecycle policies, we can:

- Seamlessly transition data to cheaper storage classes

- Automatically delete outdated objects

- Optimize storage without manual intervention


## 📚 Author
![AWS](https://img.shields.io/badge/Built%20with-AWS-orange?style=flat&logo=amazonaws) by Junior Kalomba
**🔗 Feel free to contribute or suggest improvements!** 
<p align="right">
  <a href="https://www.linkedin.com/in/junior-kalomba-10002a18a/" target="_blank">
    <img src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="junior-kalomba-10002a18a" height="30" width="40"/>  
