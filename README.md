# 🗃️ AWS S3 Lifecycle Manager

This project configures Amazon S3 lifecycle rules to automate **storage cost optimization**. It transitions objects between storage classes (e.g., Standard ➜ Infrequent Access ➜ Glacier), and deletes outdated data based on rules you define.

---

## 📦 Project Goals

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
4. Leave default settings or customize as needed
5. Create the bucket

---

###  Step 2: Add Lifecycle Rules

1. In your bucket, go to the **Management** tab
2. Click **Create lifecycle rule**
3. Name the rule (e.g., `TransitionAndExpire`)
4. Scope: apply to all objects or use a prefix like `logs/`
5. Configure actions:
   - **Transition to Infrequent Access** after 30 days
   - **Transition to Glacier** after 60 days
   - **Expire/delete objects** after 90 days
6. Save rule

---

### 🧪 Optional Automation with Boto3 (Python)

```python
import boto3

s3 = boto3.client('s3')

response = s3.put_bucket_lifecycle_configuration(
    Bucket='my-lifecycle-demo-bucket',
    LifecycleConfiguration={
        'Rules': [
            {
                'ID': 'MoveToGlacierAndExpire',
                'Filter': {'Prefix': ''},
                'Status': 'Enabled',
                'Transitions': [
                    {'Days': 30, 'StorageClass': 'STANDARD_IA'},
                    {'Days': 60, 'StorageClass': 'GLACIER'},
                ],
                'Expiration': {'Days': 90},
                'NoncurrentVersionExpiration': {'NoncurrentDays': 30}
            }
        ]
    }
)
