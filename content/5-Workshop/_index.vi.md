---
title: "Workshop"
date: 2026-07-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Triá»ƒn khai AWS Serverless Event Portal báº±ng CloudFormation

#### Tá»•ng quan

Workshop nÃ y hÆ°á»›ng dáº«n triá»ƒn khai nhanh dá»± Ã¡n **AWS Serverless Event Portal** báº±ng **Infrastructure as Code (IaC)** thÃ´ng qua **AWS CloudFormation**. Thay vÃ¬ táº¡o thá»§ cÃ´ng tá»«ng database, Lambda function, API Gateway, Cognito resource vÃ  S3 bucket, ta sá»­ dá»¥ng file `template.yaml` nhÆ° má»™t báº£n váº½ kiáº¿n trÃºc.

CloudFormation sáº½ Ä‘á»c báº£n váº½ nÃ y vÃ  tá»± Ä‘á»™ng táº¡o cÃ¡c tÃ i nguyÃªn backend. Sau khi backend hoÃ n táº¥t, ta láº¥y cÃ¡c thÃ´ng sá»‘ API vÃ  Cognito trong pháº§n Outputs, cáº¥u hÃ¬nh frontend, rá»“i host website tÄ©nh báº±ng Amazon S3.

#### CÃ¡c dá»‹ch vá»¥ AWS chÃ­nh

- **Amazon S3**: LÆ°u trá»¯ file backend Ä‘Ã£ Ä‘Ã³ng gÃ³i vÃ  host frontend website.
- **AWS CloudFormation**: Triá»ƒn khai backend system tá»« file `template.yaml`.
- **AWS Lambda**: Cháº¡y serverless backend business logic.
- **Amazon API Gateway**: Cung cáº¥p REST APIs cho frontend.
- **Amazon DynamoDB**: LÆ°u trá»¯ dá»¯ liá»‡u cá»§a á»©ng dá»¥ng.
- **Amazon Cognito**: Cung cáº¥p tÃ i nguyÃªn xÃ¡c thá»±c ngÆ°á»i dÃ¹ng.

#### Ná»™i dung

1. [Tá»•ng quan workshop](5.1-Workshop-overview/)
2. [Chuáº©n bá»‹ backend code vÃ  upload lÃªn S3](5.2-Prerequiste/)
3. [Triá»ƒn khai backend báº±ng CloudFormation](5.3-S3-vpc/)
4. [Triá»ƒn khai frontend báº±ng Amazon S3](5.4-S3-onprem/)
5. [Kiá»ƒm tra káº¿t quáº£ triá»ƒn khai](5.5-Policy/)
6. [Dá»n dáº¹p tÃ i nguyÃªn](5.6-Cleanup/)

