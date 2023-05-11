# AWS Immersion Day Lab Guide

Welcome to the AWS Immersion Day hands on lab. In this lab you will learn foundational concepts on how to onboard and discover cloud assets, identify vulnerabilities and misconfigurations in cloud infrastructure, and contextualize cloud applications via compliance and reporting.

## Section 1: Introduction and Access

In this section you will log in to our AWS account with our OTP (One Time Password) provided by Event Engine. Once you are able to log in, you will onboard the account into Prisma Cloud. 

### Subsection 1.1: Logging into AWS (OTP w/ EE)

Paragraph of text explaining this subsection.

1. Numbered list item 1
2. Numbered list item 2
3. Numbered list item 3

### Subsection 1.2: Logging into Prisma Cloud

Paragraph of text explaining this subsection.

1. Numbered list item 1
2. Numbered list item 2
3. Numbered list item 3

### Subsection 1.3: Onboarding AWS Account into Prisma Cloud

Paragraph of text explaining this subsection.

1. Numbered list item 1
2. Numbered list item 2
3. Numbered list item 3

## Section 2: Pre-Deployment (Dev)

Now that our AWS account has been onboarded into Prisma Cloud, you can kick off the CodeBuild project in AWS. 

### Subsection 2.1: Kicking off the build

In this section you will start our CodeBuild project in AWS.

1. Log in to AWS and search for **CodeBuild** in the search bar. Click on the CodeBuild service:
![Alt text for image](/screenshots/231.png "Optional title")
2. Click on the CodeBuild project Name. Note that your project name will be unique and differ from the screenshot:
![Alt text for image](/screenshots/232.png "Optional title")
3. Once you are in the CodeBuild project, click **Start build**:
[Alt text for image](/screenshots/213.png "Optional title")

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

Now that you have discovered vulnerabilities in our CodeBuild project using Prisma Cloud, let's contextualize the data by leveraging different views within Prisma Cloud and generate a report. 

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
