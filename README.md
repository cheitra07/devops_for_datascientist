# devops_for_datascientist
basic devops knowledge required for devops and mlops


### 🔐 1. **IAM (Identity and Access Management)**

> Used to create permissions for users, apps, and CI/CD pipelines.

#### ✅ What to do:

* **Create IAM users/groups**

  1. Go to IAM Console → Users → Add user
  2. Enable "Programmatic access" and/or "Console access"
  3. Assign the user to a group with predefined policies (like `AdministratorAccess` or `PowerUserAccess`)
* **Create custom policies**

  1. IAM → Policies → Create Policy → JSON
  2. Define access (e.g., allow access to S3, deny EC2 terminate)
  3. Attach policy to user/role/group

---

### ☁️ 2. **EC2 (Virtual Machines) + VPC (Networking)**

> Needed to deploy servers and configure secure networking.

#### ✅ What to do:

* **Launch EC2 instance**

  1. Go to EC2 → Launch Instance
  2. Choose OS (Amazon Linux/Ubuntu)
  3. Select instance type (e.g., t2.micro for free)
  4. Create/select key pair
  5. Configure security group → allow SSH (port 22) and HTTP/HTTPS if needed
* **Create VPC**

  1. Go to VPC Console → Create VPC
  2. Define CIDR block (e.g., 10.0.0.0/16)
  3. Create subnets, internet gateway, route table
  4. Attach subnet to EC2 instance

---

### 📦 3. **S3 (Storage)**

> Used to store build artifacts, logs, and backups.

#### ✅ What to do:

* **Create S3 bucket**

  1. Go to S3 → Create Bucket
  2. Choose a unique name, region
  3. Disable public access unless needed
* **Upload/Download files**

  1. Use console or AWS CLI:

     ```bash
     aws s3 cp myfile.txt s3://my-bucket-name/
     aws s3 cp s3://my-bucket-name/myfile.txt .
     ```
* **Configure versioning & lifecycle rules**

  1. Go to bucket → Properties → Enable versioning
  2. Add lifecycle rule to delete old versions or move to Glacier

---

### 🔔 4. **Monitoring (CloudWatch)**

> Track server health, logs, pipeline failures, etc.

#### ✅ What to do:

* **Enable CloudWatch logs**

  1. EC2: Install CloudWatch Agent to push logs
  2. Lambda: Logs automatically go to CloudWatch
* **Create Alarms**

  1. Go to CloudWatch → Alarms → Create
  2. Choose metric (e.g., CPU > 80%)
  3. Set notification via SNS (email or Slack)

---

### 💸 5. **Cost Optimization & Resource Management**

> Avoid surprises in billing.

#### ✅ What to do:

* **Use resource tagging**

  1. Add tags while creating EC2, S3, Lambda, etc. (e.g., `Project=DevOps`, `Owner=Cheitra`)
  2. Use Cost Explorer to filter costs by tag
* **Create budget alerts**

  1. Go to Billing → Budgets
  2. Set monthly budget (e.g., ₹500)
  3. Set email alert if usage exceeds threshold
* **Terminate unused resources**

  1. Regularly check EC2, EBS, S3 buckets
  2. Stop/terminate old instances or delete unattached EBS volumes

---

### Summary Table

| Skill Area   | Key Tools/Actions                            |
| ------------ | -------------------------------------------- |
| IAM          | Users, Roles, Policies, Least Privilege      |
| EC2/VPC      | Launch servers, configure network & firewall |
| S3           | Buckets, versioning, lifecycle, CLI upload   |
| CloudWatch   | Logs, metrics, alarms                        |
| Billing/Tags | Budgets, tags, cost explorer, cleanup        |


