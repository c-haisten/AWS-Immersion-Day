# AWS Immersion Day Lab Guide

Welcome to the AWS Immersion Day hands on lab. In this lab you will learn foundational concepts on how to onboard and discover cloud assets, identify vulnerabilities and misconfigurations in cloud infrastructure, and contextualize cloud applications via compliance and reporting.

## Section 1: Introduction and Access

In this section you will log in to your AWS account with your OTP (One Time Password) provided by Event Engine. Once you are able to log in, you will then login to Prisma Cloud. 

### Subsection 1.1: Logging into AWS (OTP w/ EE)

1. Each Team will browse to the below URL: 
https://dashboard.eventengine.run/login
2. You will be prompted to enter your Team Hash and click on “Accept Terms & Login”
![Alt text for image](/screenshots/112.png "Optional title")
3. Next you will see your Team Dashboard where you can click on ”AWS Console”.
![Alt text for image](/screenshots/113.png "Optional title")
4. Click on “Open AWS Console”.
![Alt text for image](/screenshots/114.png "Optional title")

### Subsection 1.2: Logging into Prisma Cloud

1. You will login to Prisma Cloud and use the Amazon Web Services (AWS) Account created for you for this lab. Go to the following link and sign in with the provided Prisma Cloud credentials: https://app4.prismacloud.io/auth/signin
![Alt text for image](/screenshots/121.png "Optional title")

## Section 2: Pre-Deployment (Dev)

Now that your AWS account has been onboarded into Prisma Cloud, you can kick off the CodeBuild project in AWS. 

### Subsection 2.1: Kicking off the build

In this section you will start the CodeBuild project in AWS.

1. Log in to AWS and search for **CodeBuild** in the search bar. Click on the CodeBuild service:
![Alt text for image](/screenshots/231.png "Optional title")
2. Click on the CodeBuild project Name. Note that your project name will be unique and differ from the screenshot:
![Alt text for image](/screenshots/232.png "Optional title")
3. Once you are in the CodeBuild project, click **Start build**:
![Alt text for image](/screenshots/213.png "Optional title")

### Subsection 2.2: Identifying Errors and Vulnerabilities in IaC (Infrastructure as Code)

Paragraph of text explaining this subsection.

1. Numbered list item 1
2. Numbered list item 2
3. Numbered list item 3

### Subsection 2.3: Identifying Vulnerabilities in Application Image from CodeBuild Output

In this section you will navigate to the output link from the twistlock scan within AWS CodeBuild. 

1. Log in to AWS and search for **CodeBuild** in the search bar. Click on the CodeBuild service:
![Alt text for image](/screenshots/231.png "Optional title")
2. Click on the CodeBuild project Name. Note that your project name will be unique and differ from the screenshot:
![Alt text for image](/screenshots/232.png "Optional title")
3. Under the **Build history** tab, click on the last build that succeeded:
![Alt text for image](/screenshots/233.png "Optional title")
4. Scroll towards the bottom of the **Build logs** and look for the line **Link to the results in Console**:
![Alt text for image](/screenshots/234.png "Optional title")
5. Open the results in a new tab and click on the image in Prisma Cloud to view vulnerabilities:
![Alt text for image](/screenshots/235.png "Optional title")

## Section 3: Post-Deployment (Ops)

Now that you have discovered vulnerabilities in the CodeBuild project using Prisma Cloud, let's contextualize the data by leveraging different views within Prisma Cloud and generate a report. 

### Subsection 3.1: Create View of AWS Assets

Prisma Cloud offers several ways to view cloud assets. In this section, you will create a view of the AWS assets with Critical and High vulnerabilities. 

1. Log in to Prisma Cloud and click on the **Inventory** button in the menu bar and select **Assets**:
![Alt text for image](/screenshots/311.png "Optional title")
2. On the **Asset Inventory** page, click the **Add View** hyperlink:
![Alt text for image](/screenshots/312.png "Optional title")
3. Name your new view **vuln** and click **Add New View**:
![Alt text for image](/screenshots/313.png "Optional title")
4. Click on the filter icon and add the **Cloud Type** and **Vulnerability Severity** categories:
![Alt text for image](/screenshots/314.png "Optional title")
5. Click the dropdown window for the Vulnerability Severity category and select both **Critical** and **High**. For the Cloud Type category, select **AWS**:
![Alt text for image](/screenshots/315.png "Optional title")
6. Now you have a view of just the AWS assets with the most severe vulnerabilities. As new assets are added to AWS, they will be monitored by Prisma Cloud and populated in your new vuln view if any critical or high severity vulnerabilities are detected. If needed, all data can be downloaded to a CSV file:
![Alt text for image](/screenshots/316.png "Optional title")

### Subsection 3.2: Identify Compliance Violations

In this next section, you will create another view but this time focusing on compliance.

1. Log in to Prisma Cloud and click on the **Compliance** button in the menu bar and select **Overview**:
![Alt text for image](/screenshots/321.png "Optional title")
2. On the **Compliance Overview** page, click the **Add View** hyperlink:
![Alt text for image](/screenshots/322.png "Optional title")
3. Name your new view **comp** and click **Add New View**:
![Alt text for image](/screenshots/323.png "Optional title")
4. Click on the filter icon and add the **Cloud Type** and **Compliance Standard** categories:
![Alt text for image](/screenshots/324.png "Optional title")
5. Click on the dropdown window for the Compliance Standard category and search for and select **SOC2**. For the Cloud Type category, select **AWS**:
![Alt text for image](/screenshots/325.png "Optional title")
6. Now you have a view of all AWS assets with SOC2 violations. As new assets are added to AWS, they will be monitored by Prisma Cloud and populated in your new comp view if any SOC2 policies are triggered. If needed, all data can be downloaded to a CSV file:
![Alt text for image](/screenshots/326.png "Optional title")


### Subsection 3.3: Reporting

In addition to dynamic, feature rich data views, Prisma Cloud has reporting capabilities for all compliance standards. 

1. Log in to Prisma Cloud and click on the **Compliance** button in the menu bar and select **Reports**:
![Alt text for image](/screenshots/331.png "Optional title")
2. Click the **Create Report** button at the top right. In the **Create Compliance Report** window, enter **aws-gdpr** for the Name, select **AWS** for the Cloud Type, select **Most Recent** for the Date and select **GDPR** for the Compliance Standard. Click the **One Time** button and **Save Report**:
![Alt text for image](/screenshots/332.png "Optional title")
3. Once the report is generated, click on the download button under the **Actions** column. 
![Alt text for image](/screenshots/333.png "Optional title")
4. Open the **AWS-GDPR.pdf** to read through an audit-ready report for GDPR policies impacting your AWS assets:
![Alt text for image](/screenshots/334.png "Optional title")

## Section 4: Additional Cloud Security Posture Management (CSPM) Exercises

In this section, you can go through additional CSPM exercises at your leisure. 

### Subsection 4.1: Discover and Resolve SSH Connections Open to the World

SSH connections open to the world are insecure as they can allow attackers to directly interface with your resources through SSH. Through this task, we will locate these open SSH connections within our AWS environment using Prisma Cloud.

1. Using the left menu of our Prisma Cloud Console, click on **Alerts > Overview**.
![Alt text for image](/screenshots/411.png "Optional title")
2. Find the corresponding policy for our AWS environment: **AWS Security Groups allow internet traffic to SSH port (22)**. Click on the number in the Alerts column to view the Violating Resources.
![Alt text for image](/screenshots/412.png "Optional title")
3. After clicking on the above policy, we will provide a view of Prisma Cloud’s recommendation for how to resolve the issue. Clicking the ![Alt text for image](/screenshots/resource_name_aws_launcher.png "Optional title") next to the **Resource Name** will bring you directly to the resource that will need to be modified to resolve this issue.
![Alt text for image](/screenshots/413.png "Optional title")
![Alt text for image](/screenshots/413b.png "Optional title")
4. After selecting the **Resource Name** in the previous Task, you should now be in your AWS environment at the Security Group in question. From here, we can remediate the open SSH connections. Select the Security Group and click the tab at the bottom named **Inbound Rules**.
![Alt text for image](/screenshots/414.png "Optional title")
5. Click the **Edit inbound rules** button to navigate to the rule editor. Select the Delete button for the SSH rule. Then select the Save Rules Button.
![Alt text for image](/screenshots/415.png "Optional title")
6. Confirm that SSH no longer appears in your Security Group.
![Alt text for image](/screenshots/416.png "Optional title")

### Subsection 4.2: Discover and Resolve RDP Connections Open to the World

RDP connections open to the world are insecure as they can allow attackers to directly interface with your Windows resources through RDP. Through this task, we will locate these open RDP connections within our AWS environment using Prisma Cloud.

1. Using the left menu of our Prisma Cloud Console, click on **Alerts > Overview**.
![Alt text for image](/screenshots/421.png "Optional title")
2. Find the corresponding policy for our AWS environment: **AWS Security Groups allow internet traffic to RDP port (3389)**. Click on the number in the Alerts column to view the Violating Resources.
![Alt text for image](/screenshots/422.png "Optional title")
3. After clicking on the above policy, we will provide a view of Prisma Cloud’s recommendation for how to resolve the issue. Clicking the ![Alt text for image](/screenshots/resource_name_aws_launcher.png "Optional title") next to the **Resource Name** will bring you directly to the resource that will need to be modified to resolve this issue.
![Alt text for image](/screenshots/423.png "Optional title")
4. After selecting the **Resource Name** in the previous Task, you should now be in your AWS environment at the Security Group in question. From here, we can remediate the open RDP connections. Click the box next to the **Name** of the Security Group, then click the tab at the bottom named **Inbound Rules**.
![Alt text for image](/screenshots/424.png "Optional title")
5. Select the Edit Inbound Rules button to open the rules editor. Click the drop down menu under the source and modify it to **My IP**.
![Alt text for image](/screenshots/425.png "Optional title")
6. Click **Save Rules**. The rule should now reflect RDP access using only your current public IP address.
![Alt text for image](/screenshots/426.png "Optional title")

### Subsection 4.3: Discover and Resolve RDS Databases Open to the World

RDS databases open to the world are insecure as they can allow attackers to directly interface with your database resources. Through this task, we will locate these open RDS databases within our AWS environment using Prisma Cloud.

1. Using the left menu of our Prisma Cloud Console, click on **Alerts > Overview**.
![Alt text for image](/screenshots/431.png "Optional title")
2. Find the corresponding policy for our AWS environment: **AWS RDS database instance is publicly accessible**. Click on the number in the Alerts column to view the Violating Resources.
![Alt text for image](/screenshots/432.png "Optional title")
3. After clicking on the above policy, we will provide a view of Prisma Cloud’s recommendation for how to resolve the issue. Clicking the ![Alt text for image](/screenshots/resource_name_aws_launcher.png "Optional title") next to the **Resource Name** will bring you directly to the resource that will need to be modified to resolve this issue.
![Alt text for image](/screenshots/433.png "Optional title")
4. After selecting the **Resource Name** in the previous Task, you should now be in your AWS environment at the RDS Database Security Group in question. From here, we can remediate the open RDS Database. Click in the database name to display the database properties.
![Alt text for image](/screenshots/434.png "Optional title")
5. In the Security section, notice that Public Accessibility is set to **Yes**. Click on **Modify**.
![Alt text for image](/screenshots/435.png "Optional title")
6. Scroll to the “Connectivity” section, expand the Additional Configuration section and select the “Not publicly accessible” option, then click the “Continue” button.
![Alt text for image](/screenshots/436.png "Optional title")
7. Scroll to the the **Scheduling of Modifications** section and select **Apply Immediately** (possibly not a good idea in a production setting), then click **Modify DB Instance**.
![Alt text for image](/screenshots/437.png "Optional title")

### Subsection 4.4: Discover Missing MFA for IAM Users

Users configured without MFA present an issue wherein credentials can be compromised. Through this task, we will locate these IAM users without MFA within our AWS environment using Prisma Cloud.

1. Using the left menu of our Prisma Cloud Console, click on **Alerts > Overview**.
![Alt text for image](/screenshots/441.png "Optional title")
2. Find the corresponding policy for our AWS environment: **AWS MFA not enabled for IAM users**. Click on the number in the Alerts column to view the Violating Resources.
![Alt text for image](/screenshots/442.png "Optional title")
3. After clicking on the above policy, we will provide a view of Prisma Cloud’s recommendation for how to resolve the issue. Clicking the ![Alt text for image](/screenshots/resource_name_aws_launcher.png "Optional title") next to the **Resource Name** will bring you directly to the resource that will need to be modified to resolve this issue.
![Alt text for image](/screenshots/443.png "Optional title")
4. After selecting the **Resource Name** in the previous Task, you should now be in your AWS environment at the IAM User in question. From here, we can remediate the missing MFA. Click the **Security Credentials** tab and confirm that a MFA device is not assigned.
![Alt text for image](/screenshots/444.png "Optional title")

### Subsection 4.5: Discover and Resolve Missing KMS Key Rotation

Keys should be rotated regularly to prevent account compromise. This task will find the keys that are not setup for rotation within our AWS environment using Prisma Cloud.

1. Using the left menu of our Prisma Cloud Console, click on **Alerts > Overview**.
![Alt text for image](/screenshots/451.png "Optional title")
2. Find the corresponding policy for our AWS environment: **AWS Customer Master Key (CMK) rotation is not enabled**. Click on the number in the Alerts column to view the Violating Resources.
![Alt text for image](/screenshots/452.png "Optional title")
3. After clicking on the above policy, we will provide a view of Prisma Cloud’s recommendation for how to resolve the issue. Clicking the ![Alt text for image](/screenshots/resource_name_aws_launcher.png "Optional title") next to the **Resource Name** will bring you directly to the resource that will need to be modified to resolve this issue.
![Alt text for image](/screenshots/453.png "Optional title")
4. After selecting the **Resource Name** in the previous Task, you should now be in your AWS environment at the resource in question. From here, we can remediate the missing KMS Key Rotation. Click on the **Key ID** that matches to the one alerted on in Prisma Cloud.
![Alt text for image](/screenshots/454.png "Optional title")
5. Click on the **Key Rotation** tab at the bottom.
![Alt text for image](/screenshots/455.png "Optional title")
6. Check the box next to **Automatically rotate this CMK every year** and click **Save**.
![Alt text for image](/screenshots/456.png "Optional title")

### Subsection 4.6: Discover S3 Buckets with Object Versioning disabled

S3 Object Versioning is an important capability in protecting your data within a bucket. With versioning, you can easily recover from both unintended user actions and application failures, potentially including application compromise or ransomware (especially if combined with **MFA Delete** being enabled, for which there is also a Prisma Cloud policy).

1. Using the left menu of our Prisma Cloud Console, click on **Alerts > Overview**.
![Alt text for image](/screenshots/461.png "Optional title")
2. Find the corresponding policy for our AWS environment: **AWS S3 Object Versioning is disabled**. Click on the number in the Alerts column to view the Violating Resources.
![Alt text for image](/screenshots/462.png "Optional title")
3. After clicking on the above policy, we will provide a view of Prisma Cloud’s recommendation for how to resolve the issue. Clicking the ![Alt text for image](/screenshots/resource_name_aws_launcher.png "Optional title") next to the **Resource Name** will bring you directly to the resource that will need to be modified to resolve this issue.
![Alt text for image](/screenshots/463.png "Optional title")
4. After selecting the **Resource Name** in the previous Task, you should now be in your AWS environment at the resource in question. From here, we can remediate the disabled Object Versioning. Click on the **Properties** tab of the S3 Bucket. Select **Edit** in the Bucket Versioning property box.
![Alt text for image](/screenshots/464.png "Optional title")
5. Select the **Enable Versioning** radio button and click **Save change**.
![Alt text for image](/screenshots/465.png "Optional title")

**Congratulations!** You have successfully completed this hands-on workshop.

This lab focused primarily on the triage capabilities of Prisma Cloud. In your time remaining, we encourage you to explore the other facets of the Product. Specifically with regard to CSPM, we would encourage you to browse through the Inventory and Compliance Tabs.

![Alt text for image](/screenshots/inventory.png "Optional title")

![Alt text for image](/screenshots/compliance.png "Optional title")

## End of Lab - Thank you for attending!


























