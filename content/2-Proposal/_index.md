---
title: "Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# AWS Serverless Event Portal Proposal

**Project Name:** AWS Serverless Event Portal  
**Group:** Hieu An  
**Project Type:** Cloud-native event management application

## 1. Executive Summary

The **AWS Serverless Event Portal** is a cloud-native web application designed to simplify event organization and participation by using AWS Serverless technologies. The system provides a centralized platform where users can browse events, register online, receive digital tickets, check in with QR codes, submit feedback, and view suitable event recommendations. At the same time, administrators can manage events, participants, registrations, and attendance records through a secure web interface.

Instead of depending on traditional servers, the project uses managed AWS services to improve scalability, availability, and operational efficiency. The frontend is hosted on **Amazon S3** and delivered through **Amazon CloudFront**. Backend APIs are exposed through **Amazon API Gateway** and implemented with **AWS Lambda**. **Amazon Cognito** handles authentication and authorization, while **Amazon DynamoDB** stores event data, registrations, tickets, check-in records, and feedback. Logs, metrics, alarms, and notifications are managed through **Amazon CloudWatch** and **Amazon SNS**.

This project is both a practical university project and a demonstration of modern AWS serverless application development. By using managed cloud services, the system reduces infrastructure management work and creates a scalable foundation for future improvements.

## 2. Problem Statement

### What's the Problem?

Many universities, student clubs, and small event organizers still manage events with manual or semi-manual tools such as spreadsheets, messaging apps, and online forms. These methods may work for small activities, but they become inefficient when the number of events or participants increases.

Common problems include duplicated registration records, slow attendance checking, difficulty tracking event capacity, limited visibility into participant information, and time-consuming report preparation. Participants also lack a single platform to discover upcoming events, manage their registrations, or access digital tickets.

Without an integrated event management system, organizers must spend a large amount of effort maintaining event data, checking attendance, managing waitlists, and collecting post-event feedback.

### The Solution

The **AWS Serverless Event Portal** addresses these problems by providing an integrated cloud-based event management platform.

Users access the web application through a browser. The frontend communicates with backend APIs through Amazon API Gateway. API Gateway invokes AWS Lambda functions that process the main business logic, including event creation, registration, QR code check-in, recommendation, feedback, and administrative actions.

Amazon Cognito secures login and access control. Amazon DynamoDB stores application data with high availability and low latency. Amazon CloudWatch collects logs and metrics, while Amazon SNS can send notifications when operational alarms are triggered.

The platform is planned to support the following major capabilities:

- User authentication and authorization
- Event browsing and searching
- Online event registration
- Digital ticket management
- QR Code Check-in
- Waitlist management
- Event recommendation
- Feedback and review management
- Administrator dashboard for event management

### Benefits and Return on Investment

The proposed system reduces manual work by centralizing event registration, participant management, ticketing, and attendance tracking. Organizers can manage event information in one platform instead of using multiple disconnected tools.

From a technical perspective, AWS Serverless services reduce the need to manage servers, operating systems, and scaling policies manually. Services such as AWS Lambda, Amazon DynamoDB, and Amazon API Gateway scale based on actual demand, making the architecture suitable for student organizations, workshops, and small-to-medium event management use cases.

The solution also provides long-term value because its modular architecture can be extended with additional features, such as advanced recommendations, analytics dashboards, email reminders, or AI-assisted event support.

## 3. Solution Architecture

The AWS Serverless Event Portal uses a fully serverless architecture that separates frontend delivery, authentication, API processing, business logic, data storage, and monitoring into independent managed services. This design improves maintainability and allows each component to scale based on its own workload.

The frontend is hosted on Amazon S3 and delivered to users through Amazon CloudFront. Authentication is handled by Amazon Cognito. After login, the frontend sends authenticated requests to Amazon API Gateway, which validates and routes requests to AWS Lambda functions. Lambda functions process application logic and read or write data in Amazon DynamoDB. Operational logs and metrics are collected in Amazon CloudWatch, and important alarms can notify administrators through Amazon SNS.

![AWS Serverless Event Portal Architecture](/images/2-Proposal/serverless-event-portal-architecture.png)

### AWS Services Used

| AWS Service | Purpose |
| --- | --- |
| Amazon S3 | Hosts the React frontend application and static assets. |
| Amazon CloudFront | Delivers frontend content with lower latency. |
| Amazon Cognito | Provides user authentication and authorization. |
| Amazon API Gateway | Exposes REST APIs for frontend communication. |
| AWS Lambda | Executes backend business logic. |
| Amazon DynamoDB | Stores events, users, registrations, tickets, feedback, and check-in data. |
| Amazon CloudWatch | Collects logs, metrics, and alarms. |
| Amazon SNS | Sends operational notifications when alarms are triggered. |
| AWS SAM / CloudFormation | Deploys and manages serverless infrastructure. |

### Component Design

**Frontend Layer**  
Users access the Event Portal through Amazon CloudFront. CloudFront delivers the static React frontend hosted on Amazon S3, helping improve loading speed and availability.

**Authentication Layer**  
Amazon Cognito manages user sign-in and authorization. JWT tokens issued by Cognito are used to protect API requests.

**API Layer**  
Amazon API Gateway acts as the secure entry point for frontend requests and forwards them to the correct Lambda functions.

**Business Logic Layer**  
AWS Lambda contains the core application logic, including event management, registration processing, QR code check-in, recommendation handling, feedback processing, and administrative operations.

**Data Layer**  
Amazon DynamoDB stores application data such as user profiles, event information, registration records, digital tickets, check-in logs, feedback, and notifications.

**Monitoring Layer**  
Amazon CloudWatch monitors Lambda execution, API activity, logs, and metrics. CloudWatch alarms can trigger Amazon SNS notifications when abnormal conditions occur.

## 4. Technical Implementation

### Implementation Phases

The project is planned and developed through four main phases.

| Phase | Main Activities |
| --- | --- |
| Phase 1 - Requirement Analysis and Architecture Design | Analyze system requirements, identify suitable AWS services, design the serverless architecture, prepare the database schema, and define the application workflow. |
| Phase 2 - Backend Development | Develop AWS Lambda functions, configure Amazon API Gateway, integrate Amazon Cognito, implement Amazon DynamoDB tables, and build backend APIs. |
| Phase 3 - Frontend Development | Build the React and Vite frontend, create interfaces for event browsing, registration, tickets, QR check-in, feedback, and administration. |
| Phase 4 - Integration, Testing, and Deployment | Integrate frontend and backend, test core features, deploy serverless resources using AWS SAM and CloudFormation, and host the frontend using Amazon S3 and CloudFront. |

### Technical Requirements

**Development Environment**

- Node.js
- React + Vite
- TypeScript
- GitHub
- Visual Studio Code

**AWS Services**

- Amazon S3
- Amazon CloudFront
- Amazon Cognito
- Amazon API Gateway
- AWS Lambda
- Amazon DynamoDB
- Amazon CloudWatch
- Amazon SNS
- AWS SAM
- AWS CloudFormation

### Application Features

The completed system is expected to support:

- User authentication
- Event browsing
- Event registration
- Digital ticket management
- QR Code Check-in
- Waitlist management
- Event recommendation
- Feedback and reviews
- Administrator dashboard
- Cloud-based monitoring and logging

## 5. Timeline & Milestones

### Project Timeline

The AWS Serverless Event Portal project is planned to be completed within approximately two months. The development process is divided into four major phases to ensure systematic implementation, testing, and deployment.

| Phase | Duration | Activities |
| --- | --- | --- |
| Phase 1 - Planning & Architecture Design | Week 1-2 | Analyze requirements, identify AWS services, design the serverless architecture, database schema, and application workflow. |
| Phase 2 - Backend Development | Week 3-4 | Develop Lambda functions, configure API Gateway, integrate Cognito, implement DynamoDB, and develop backend APIs. |
| Phase 3 - Frontend Development & Integration | Week 5-6 | Develop the React frontend, integrate backend APIs, and implement registration, QR check-in, recommendation, and authentication features. |
| Phase 4 - Testing & Deployment | Week 7-8 | Perform system testing, fix defects, deploy serverless resources using AWS SAM and CloudFormation, deploy the frontend to S3 and CloudFront, and prepare the final demonstration. |

### Milestones

- Completion of AWS architecture design
- Backend API implementation
- Frontend integration
- Authentication using Amazon Cognito
- QR Code Check-in implementation
- AWS deployment completed
- Final system testing
- Workshop presentation and project demonstration

## 6. Budget Estimation

The AWS Serverless Event Portal is developed primarily as a university project and workshop demonstration. Since the system is not designed for production-scale traffic at this stage, the expected operational cost remains low.

Detailed operational costs can be evaluated during deployment using the **AWS Pricing Calculator**. The estimation should consider the expected monthly usage of the following services:

- Amazon S3 storage and requests
- Amazon CloudFront data transfer
- Amazon API Gateway requests
- AWS Lambda invocations
- Amazon DynamoDB storage and read/write requests
- Amazon Cognito Monthly Active Users (MAU)
- Amazon CloudWatch logs and monitoring
- Amazon SNS notification delivery

Because the architecture follows a pay-as-you-go serverless model, resources are billed based on actual usage instead of continuously running servers. This makes the solution suitable for student projects, university events, and small-to-medium event management systems.

## 7. Risk Assessment

### Risk Matrix

| Risk | Probability | Impact |
| --- | --- | --- |
| AWS service configuration errors | Medium | High |
| Authentication failure | Low | High |
| API or Lambda execution failure | Medium | High |
| DynamoDB data inconsistency | Low | Medium |
| QR Code scanning issues | Medium | Medium |
| Unexpected AWS operational costs | Low | Medium |

### Mitigation Strategies

**AWS Configuration**  
AWS resources should be deployed using AWS SAM and CloudFormation to keep infrastructure configuration consistent and easier to reproduce.

**Authentication**  
Amazon Cognito provides secure authentication and authorization using JWT tokens, reducing unauthorized access to protected APIs.

**Monitoring**  
Amazon CloudWatch monitors Lambda execution, application logs, and operational metrics. CloudWatch alarms can notify administrators through Amazon SNS when abnormal behavior is detected.

**Database Reliability**  
Amazon DynamoDB provides highly available and durable NoSQL storage with automatic scaling capabilities, reducing database management overhead.

**QR Code Check-in**  
The application supports QR Code scanning through browser camera access. Manual ticket code entry can be used as an alternative when camera access is unavailable.

### Contingency Plans

If deployment issues occur during the demonstration, the project can still be presented using a local development environment and mock services. This ensures that core features such as event browsing, registration, QR check-in, and administration remain available for demonstration purposes.

## 8. Expected Outcomes

### Technical Outcomes

Upon completion, the AWS Serverless Event Portal is expected to provide:

- A functional serverless event management platform
- Secure user authentication using Amazon Cognito
- Online event registration and participant management
- Digital ticket generation and QR Code Check-in
- Event recommendation functionality
- Administrator dashboard for event management
- Cloud-based monitoring and operational notifications
- Scalable backend services using AWS Lambda and Amazon DynamoDB

### Learning Outcomes

This project provides practical experience in designing and deploying cloud-native applications using AWS Serverless technologies. Team members gain hands-on experience with:

- AWS Serverless Architecture
- Infrastructure as Code using AWS SAM and CloudFormation
- REST API development with Amazon API Gateway
- Serverless backend development using AWS Lambda
- NoSQL database design with Amazon DynamoDB
- User authentication using Amazon Cognito
- Cloud monitoring using Amazon CloudWatch
- Frontend deployment using Amazon S3 and Amazon CloudFront

### Long-Term Value

The AWS Serverless Event Portal can serve as a reusable foundation for future event management applications and cloud computing projects. Its modular serverless architecture allows additional features and AWS services to be integrated with minimal architectural changes. The project also demonstrates modern cloud application development practices and can be extended to support larger-scale deployments or future AI-assisted event features.