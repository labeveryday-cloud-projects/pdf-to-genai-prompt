# PDF-to-Prompt

## Description
PDF-to-Prompt is a Python script that downloads PDF files from specified URLs, extracts the text content from the PDFs, and sends the combined text as a prompt to the Claude. The script utilizes the `pdfminer.six` library for PDF text extraction and the `boto3` library to interact with the Claude through the Bedrock Runtime client.

## Prerequisites
Before running the script, ensure that you have the following prerequisites:

1. AWS CLI: The AWS Command Line Interface (CLI) must be installed and configured on your local machine. You can download and install the AWS CLI from the official AWS documentation: [Installing the AWS CLI](https://aws.amazon.com/cli/)

2. AWS Credentials: Configure your AWS credentials by running aws configure and providing your AWS Access Key ID, Secret Access Key, and preferred AWS Region. Alternatively, you can use other authentication methods like AWS IAM roles or environment variables. For more information, refer to the [AWS CLI Configuration and Credential File Settings documentation](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html).

3. AWS IAM Permissions: Ensure that you have the necessary permissions to create and manage the required AWS resources (Lambda, SNS, EventBridge, IAM roles, etc.) in your AWS account. You can either have administrative privileges or use an IAM role with the appropriate permissions. See [Policies and permissions in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html)

## Purpose
The primary purpose of this script is to automate the process of extracting text content from multiple PDF files and using that content as a prompt for the Anthropic Claude 3 LLM. This can be useful in various scenarios, such as:

- Analyzing and summarizing large collections of PDF documents
- Generating responses or insights based on the content of technical documentation or research papers
- Combining information from multiple sources into a single prompt for further processing or analysis

## Value
The PDF-to-Prompt script provides value by streamlining the process of converting PDF files into a format that can be easily consumed by the Claude. It eliminates the need for manual text extraction and formatting, saving time and effort. Additionally, the script can handle multiple PDF files simultaneously, making it a convenient tool for working with large document collections.

## How It Works
1. The user provides a string URL or a list of PDF URLs as input.
2. The `download_pdf()` function downloads the PDF files from the specified URLs and extracts the text content using the `pdfminer.six` library.
3. The extracted text content from all the PDF files is combined into a single string.
4. The `send_prompt()` function constructs a prompt configuration based on the combined text content and sends it to the Amazon Bedrock API using the Bedrock Runtime client.
5. The Amazon Bedrock API processes the prompt and generates a response, which is returned by the `send_prompt()` function.
6. The script prints the response from the Claude 3 Sonnet LLM in Amazon Bedrock.

## Deployment
To deploy and run the PDF-to-Prompt script, follow these steps:

1. [Clone the repository](https://github.com/labeveryday-cloud-projects/pdf-to-genai-prompt.git) and cd into the repo's directory.

```bash
git clone https://github.com/labeveryday-cloud-projects/pdf-to-genai-prompt.git && cd pdf-to-genai-prompt
```

2. Install the required dependencies using pip:

```bash
pip install -r requirements.txt
```

3. Set up your AWS credentials and configuration for the Bedrock Runtime client.
4. Modify the `pdf_urls` list in the `__main__` section with the URLs of the PDF files you want to process.

```python
pdf_urls = [
        "https://d1.awsstatic.com/training-and-certification/docs-data-engineer-associate/AWS-Certified-Data-Engineer-Associate_Exam-Guide.pdf",
        "https://d1.awsstatic.com/training-and-certification/docs-sysops-associate/AWS-Certified-SysOps-Administrator-Associate_Exam-Guide.pdf",
        "https://d1.awsstatic.com/training-and-certification/docs-sa-assoc/AWS-Certified-Solutions-Architect-Associate_Exam-Guide.pdf",
        "https://d1.awsstatic.com/training-and-certification/docs-dev-associate/AWS-Certified-Developer-Associate_Exam-Guide.pdf"
    ]
```

5. Run the script: `python main.py`.
6. The script will download the PDF files, extract the text content, send the prompt to the Claude, and print the response:

```bash
Based on the certification exam guide descriptions, here are some areas that overlap between the 4 certifications:

1. AWS Service Knowledge:
   - Services like AWS Lambda, API Gateway, CloudFormation, CloudWatch, IAM, KMS, VPC, S3, EBS, etc. are covered in multiple certification exams.

2. Security and Compliance:
    - Implementing security controls, encryption, access management, governance policies etc. are common topics.

3. Deployment and Automation:
    - CI/CD pipelines, infrastructure as code, automating deployments using AWS services etc. overlap.

4. Monitoring, Logging and Troubleshooting:
    - Monitoring application performance, analyzing logs, troubleshooting issues are touched upon in multiple exams.

5. Networking Concepts:
    - VPC setup, networking protocols, content delivery etc. are relevant across some of the certifications.

6. Cost Optimization:
    - Optimizing costs by selecting appropriate services/resources is a shared area.

7. High Availability and Scalability:
    - Designing resilient, fault-tolerant, and scalable architectures using AWS services is emphasized.

8. Data Storage:
    - Working with different AWS data stores like RDS, DynamoDB, S3, EFS etc. is required knowledge.

So in summary, while the certifications target different roles, there is considerable overlap in the core AWS services, security, deployments, monitoring, networking and architectural best practices.
```


## Conclusion
The PDF-to-Prompt script provides a convenient way to automate the process of extracting text content from multiple PDF files and using that content as a prompt for the Claude. By combining the power of PDF text extraction and the Claude's natural language processing capabilities, this script can be a valuable tool for analyzing and generating insights from large collections of PDF documents.


### About me

My passions lie in Network Engineering, Cloud Computing, Automation, and impacting people's lives. I'm fortunate to weave all these elements together in my role as a Developer Advocate. On GitHub, I share my ongoing learning journey and the projects I'm building. Don't hesitate to reach out for a friendly hello or to ask any questions!

My hangouts:
- [LinkedIn](https://www.linkedin.com/in/duanlightfoot/)
- [YouTube](https://www.youtube.com/@LabEveryday)
